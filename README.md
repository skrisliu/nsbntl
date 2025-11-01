## Compare sky quality meter (SQM) night sky brightness (NSB) and nighttime light (NTL) from spaceborne satellites with Luojia-1 and the International Space Station

Paper: Analyzing nighttime lights using multi-temporal imagery from Luojia-1 and the International Space Station with in-situ and land use data. 

This is a critical step guide on reproducing the results. 


## Step 1: Download image data. 

1. Luojia-1 data can be downloaded at [http://59.175.109.173:8888/app/login_en.html](http://59.175.109.173:8888/app/login_en.html) via Wuhan University. 

2. ISS Image data can be downloaded at [https://eol.jsc.nasa.gov/searchphotos/](https://eol.jsc.nasa.gov/searchphotos/) via NASA/JSC Gateway to Astronaut Photography of Earth, a service provided by the International Space Station program and the JSC Earth Science \& Remote Sensing Unit, ARES Division. 

3. Select a bounding box area including Hong Kong (22.4 N, 114.1 E). 

4. Luojia-1 image data is unique by time. 
```
20180903, 6 snapshots
20181124, 5 snapshots
20190129, 6 snapshots
20190311, 2 snapshots
```

5. ISS image data is unique by time. We also list the image ID here. Choose request the raw image and wait for download. 
```
20150119, 7 snapshots. ISS042-E-152944 to ISS042-E-152950
20150123, 13 snapshots. ISS042-E-165423 to ISS042-E-165435
20180228, 6 snapshots. ISS055-E-095111 to ISS055-E-095116
20200226, 2 snapshots. ISS062-E-609958 to ISS062-E-609959
```


## Step 2: Process and georeference image data. 
1. For ISS, read raw NEF image to 16-bit TIF, using this Python script: [readNEF.py](readNEF.py). 

2. Download the OpenStreetMap data, or other georeferenced vector data or image data. 

3. In ArcGIS, load the georeferenced image data first. Then, load the nonreferenced TIF image. Start georeferencing. You may find a tutorial on using this tool from the software provider. 

4. Select 3-5 points roughly first to ensure the image is shown in the map. After 10 points, change to 3rd-order transformation. DO NOT USE SPLINE. The 3rd-order transformation allows for some uncertainty for each control point, and by placing control points randomly within the image, they can cancel out each other, making sure no systematic bias coming from certain control points. Continue to work towards 30-40 points. It should be enough for a city the scale of Hong Kong. Double check RMSE from the table. Delete and reselect some control points with large RMSE. 

5. Output the georeferenced image, set the resolution to 0.001 degree (~111 m). You may change the resolution to a small value if the image captured with a large focal length. 

6. Luojia-1 image data has a rough georeferencing, but not accurate enough. Need to georeference Luojia-1 image with similar steps. 


## Step 3: Analysis
7. Download the NSB data from the monitoring network. Note the time difference and make sure adjust for local time. 

8. Match the site location within each image. Extract the NTL and NSB values through different window size. 

9. Do analysis. 






