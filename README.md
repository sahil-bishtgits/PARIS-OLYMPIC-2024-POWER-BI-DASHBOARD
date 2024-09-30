   #                                   2024 PARIS OLYMPIC Dashboard

 ![olympic LOGO](https://github.com/sahil-bishtgits/PARIS-OLYMPIC-2024-POWER-BI-DASHBOARD/blob/main/pngimg.com%20-%20olympic_rings_PNG6.png)

#### Dashboard Link : https://app.powerbi.com/groups/me/reports/42463b67-9a74-41bd-8eaa-fd26ce90f9c6/8d36de2c07723ecfbe31?experience=power-bi

## Problem Statement

Problem Statement
The Olympic Games are a massive global event, featuring thousands of athletes from numerous countries competing across a variety of sports. Tracking and analyzing data from such an event is a complex challenge. For event organizers, media, and analysts, understanding the following is critical:

- Which countries are performing the best?
- How is the medal tally distributed across countries and sports?
- Which athletes are excelling in their respective events?
- What are the trends in performance based on factors like age, gender, and country?
This project aims to address these challenges by developing a user-friendly Power BI dashboard that visualizes key metrics and trends from the 2024 Paris Olympic Games.

## Key Features
- Country-wise Medal Analysis: Breakdown of the medal tally by country, sport, and event.
- Athlete Performance: Detailed insights into top-performing athletes and their achievements.
- Event Statistics: Overview of various sports, including participant statistics and results.
- Interactive Visuals: Filters and slicers allowing users to explore data based on country, event, athlete, and more.
- Trend Analysis: Visualizations to showcase trends in medal distribution and athlete performance across previous Olympics and 2024.


### Steps followed 

This project involves several steps, from downloading the data to preparing it for visualization. Here’s a breakdown of the entire process:

Step 1: Setting Up Kaggle API and Python Environment
First, we need to set up the Kaggle API to access and download datasets.
- Sign up on Kaggle
- Create an API Token: In your Kaggle account settings, go to the “API” section and click “Create New API Token.” This will download a kaggle.json file containing your credentials.
- Save the API Token: Place the kaggle.json file in a secure directory on your machine, where it will be used to authenticate the Kaggle API.

## Python Environment Setup
Make sure you have Python installed along with the necessary libraries:
```bash
  pip install kaggle pandas
```
#### Step 2: Python Script for Downloading the Dataset
Below is the Python script that automates the process of downloading the Paris 2024 Olympic dataset from Kaggle and loading it into Pandas DataFrames for analysis.  

## Installation

Install my-project with npm

```import kaggle
import os
import pandas as pd

# Set Kaggle API credentials directory
os.environ['KAGGLE_CONFIG_DIR'] = 'C:/Users/sahil/.kaggle'  # Update this path to your Kaggle configuration directory

# Specify the dataset identifier
dataset = 'piterfm/paris-2024-olympic-summer-games'

# Set the download path
download_path = 'C:/Users/sahil/Downloads/Power BI_Imp Summary/Olympic/Source' # Change this to your preferred download directory

# Remove existing files in the folder to prevent duplicates or outdated files
for file in os.listdir(download_path):
    file_path = os.path.join(download_path, file)
    try:
        if os.path.isfile(file_path):
            os.unlink(file_path)  # Delete the file
            print(f"Deleted {file_path}")
    except Exception as e:
        print(f"Error deleting {file_path}: {e}")

# Download the dataset using the Kaggle API and unzip the files
kaggle.api.dataset_download_files(dataset, path=download_path, unzip=True)

# List of CSV files to be imported
csv_files = [
    'athletes.csv',
    'events.csv',
    'medallists.csv',
    'medals.csv',
    'medals_total.csv',
    'schedules.csv',
    'schedules_preliminary.csv',
    'teams.csv',
    'torch_route.csv',
    'venues.csv'
]

# Initialize a dictionary to hold DataFrames
dataframes = {}

# Iterate through each CSV file and load it into a DataFrame
for file in csv_files:
    # Construct the full path to the CSV file
    file_path = os.path.join(download_path, file)
    
    # Load the CSV file into a Pandas DataFrame
    df = pd.read_csv(file_path)
    
    # Add the DataFrame to the dictionary using the file name as the key
    table_name = file.split('.')[0]  # Remove the .csv extension
    dataframes[table_name] = df
```
#### Step 3: Importing Data into Power BI
With the dataset downloaded and organized into DataFrames, we can now import this data into Power BI for visualization.

Connecting Power BI to Python
- Open Power BI: Start by opening Power BI Desktop.
- Get Data: Click on “Get Data” in the Home tab and choose “Python script” as the data source.


```# Import necessary libraries
import pandas as pd
import os

# Define the path to the downloaded CSV files
download_path = 'C:/Users/faisa/Downloads/Power BI_Imp Summary/Olympic/Source'

# Load the data into DataFrames
athletes = pd.read_csv(os.path.join(download_path, 'athletes.csv'))
events = pd.read_csv(os.path.join(download_path, 'events.csv'))
medallists = pd.read_csv(os.path.join(download_path, 'medallists.csv'))
medals = pd.read_csv(os.path.join(download_path, 'medals.csv'))
medals_total = pd.read_csv(os.path.join(download_path, 'medals_total.csv'))
schedules = pd.read_csv(os.path.join(download_path, 'schedules.csv'))
schedules_preliminary = pd.read_csv(os.path.join(download_path, 'schedules_preliminary.csv'))
teams = pd.read_csv(os.path.join(download_path, 'teams.csv'))
torch_route = pd.read_csv(os.path.join(download_path, 'torch_route.csv'))
venues = pd.read_csv(os.path.join(download_path, 'venues.csv'))
```

#### Step 4: Creating Visualizations in Power BI
With the data loaded into Power BI, we can now create compelling visualizations to analyze the Olympic dataset. Here are a few examples:

### Visual 1: Athlete Participation by Country
- Type: Bar Chart
- Fields: Use the athletes table to plot the number of athletes participating from each country. This provides a quick overview of which countries have the most representation in the Olympics.
### Visual 2: Medal Count by Country
- Type: Pie Chart
- Fields: Utilize the medals_total table to display the total medal count for each country. This visualization helps identify the top-performing nations in terms of medals won.
### Visual 3: Event Schedule
- Type: Table
- Fields: Use the schedules table to create a detailed schedule of events, including event names, dates, and venues. This allows viewers to plan their viewing schedule and follow specific events.
### Visual 4: Torch Route Map
- Type: Map
- Fields: Employ the torch_route table to visualize the Olympic torch route on a map. This visualization adds geographical context to the relay and highlights the journey of the Olympic flame.
### Visual 5: Medal Trends Over Time
- Type: Line Chart
- Fields: Use the medals table to display trends in medal wins over time, broken down by country or sport. This visualization offers insights into how countries’ performances have changed across different Olympics.

### 1. Snapshot of Dashboard 

![dashboard_snapo](https://github.com/sahil-bishtgits/PARIS-OLYMPIC-2024-POWER-BI-DASHBOARD/blob/main/Screenshot%20(48).png)

- Home page of report , contain overlay of the repoert.

### 2. Snapshot of Dashboard 

![dashboard_snapo](https://github.com/sahil-bishtgits/PARIS-OLYMPIC-2024-POWER-BI-DASHBOARD/blob/main/Screenshot%20(49).png)

The data that are shown on this pages are
- key feature
- Total number of medals won by each country
- total no of medal won by both gender and to which country do they belong
- AND number of country that partcipated , number of athletes that partcipated etc

### 3. Snapshot of Dashboard 

![dashboard_snapo](https://github.com/sahil-bishtgits/PARIS-OLYMPIC-2024-POWER-BI-DASHBOARD/blob/main/Screenshot%20(50).png)

The data that are shown on this pages are
- Gender wise medals won in each category
- Age category Which won the most number of medals

### 4. Snapshot of Dashboard 

![dashboard_snapo](https://github.com/sahil-bishtgits/PARIS-OLYMPIC-2024-POWER-BI-DASHBOARD/blob/main/Screenshot%20(51).png)

This page of report consist of a json map 
- The heat map shows the medal won by the country
- It gives a better overview of how sucessful was each country in this year olympic

### 5. Snapshot of Dashboard 

![dashboard_snapo](https://github.com/sahil-bishtgits/PARIS-OLYMPIC-2024-POWER-BI-DASHBOARD/blob/main/Screenshot%20(52).png)

This page of report shows the historical record of olympic
- The medal distribution across across all the past olympic
- The data also have a country filter which can be used to sort it 



## Conclusion
By leveraging Python and Power BI, we’ve efficiently downloaded, organized, and visualized the Paris 2024 Olympic dataset. This project demonstrates the power of data analysis and visualization in understanding the dynamics of a global event like the Olympics.

Through this exploration, we gain valuable insights into athlete participation, medal trends, event schedules, and more. As the 2024 Summer Olympics draw nearer, this analysis provides a fascinating glimpse into the event’s potential outcomes and highlights the immense scale and diversity of the games.

## Further Exploration
- Advanced Analytics: Dive deeper into advanced analytics by applying machine learning models to predict medal outcomes or identify key performance indicators for athletes.
- Dynamic Dashboards: Enhance Power BI reports with dynamic dashboards, providing interactive and real-time updates on Olympic events and statistics.
Feel free to download the code and datasets, and experiment with your own visualizations and analyses. Happy analyzing!
- Load the Script: Copy and paste the following Python script into the Power BI editor to load the DataFrames:
