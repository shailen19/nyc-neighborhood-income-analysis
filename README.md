# nyc-neighborhood-income-analysis

**Overview**



This project analyzes the income distribution across the five boroughs of New York City using data from the American Community Survey (ACS) and additional neighborhood spatial data. The goal is to visualize income disparities across different neighborhoods and explore correlations between industries and income growth. Various data visualizations, including bar graphs, maps, and regression plots, are generated to illustrate these trends.

**Interactive Map for Visualizing Income by Neighborhood**

A central feature of this project is an interactive map that allows users to explore income distribution across New York City's five boroughs by neighborhood. The map integrates ACS income data and additional neighborhood spatial data, providing a dynamic way to visualize income disparities and trends.

**Key Features:**

  1.	**Color-Coded Income Ranges:**
  The map displays income data for each neighborhood, with colored from white to blue representing different income ranges. This allows users to quickly assess the income distribution across neighborhoods at a glance. Neighborhoods without income data are shown in grey.
  2.	**Click to View Specific Income:**
  When a user clicks on a neighborhood, they can view detailed income information for that specific area, including the exact average income for that neighborhood.
  3.	**Zoom and Pan Functionality:** 
  Users can zoom in on specific neighborhoods or pan across the five boroughs to explore the income distribution in greater detail.
  4.	**Interactive and Informative:**
  The map is designed to be easy to interact with, allowing users to engage directly with the data and gain insights into income disparities across New York City.
  This interactive map provides a dynamic and user-friendly way to visualize income distribution and explore how income levels vary across different
neighborhoods and boroughs.

_The code for generating this map can be found in lines 259-269:_

```{r}
#st_as_sf os used to convert the data frame in to a sf object
merged_data_tm <- st_as_sf(merged_data_final)
tmap_mode("view")
tm_shape(merged_data_tm) +
  tm_polygons(c("Income"), Name = "neighborhood", palette = "Blues") +
  tm_text("Borough", size = 0.5)
```

**How to Run:**

To run this project, you will need to install the necessary libraries and set up your environment. The following instructions will guide you through the setup in RStudio.

**1. Set Up Your Environment**
Make sure you have RStudio installed on your computer. 

**2. Install Required Libraries**
In RStudio, open a new R console and install the necessary libraries using the following code:

  ```{r}
install.packages("maptools", repos = "https://packagemanager.posit.co/cran/2023-10-13")
```
```{r}
install.packages(c("tidyverse", "readxl", "ggplot2", "reticulate", "fuzzyjoin", "stringdist", "tmap", "ggfortify", "installr", "leaflet", "ggmap", "dplyr", "tigris", "sp", "sf", "httr", "broom"))
```

These libraries are required for data manipulation, visualization, and creating interactive maps.

**3. Prepare the Data Files**
Make sure to place the necessary data files in the working directory (the folder where your R script is located):

  **Census Data (Excel File):** 
  The project requires an Excel file named nyc.xlsx, which contains income data for each neighborhood. Make sure this file is in the same directory as your project script.
  
  _In the code, lines 110-113 should look like this:_
  
    ```{r}
  	neighborhoods <- read_excel(".../Your_Path_Here/nyc.xlsx")
  	neighborhood.
    ```
  
  
  **GeoJSON File for Neighborhood Income Visualization:**
   You’ll also need a GeoJSON file named nycneighborhoods.geojson that includes the spatial data for each neighborhood on the map. Ensure this file is located in the same directory as your R script.
   
  _In the code, lines 157-160 should look like this:_
  
  		```{r}
  		file_path <- "~/Your_Path_Here/nycneighborhoods.geojson"
  	nyc_neighborhoods <- st_read(file_path, quiet = TRUE)
  	```
