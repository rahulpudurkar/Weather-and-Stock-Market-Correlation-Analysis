# Weather and Stock Market Analysis

This project analyzes the relationship between weather conditions in London and stock market indices over time, particularly focusing on the FTSE index. It explores various data processing techniques, visualizations, and correlation analysis between different variables such as temperature, precipitation, stock prices, and more.

## Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Installation](#installation)
- [Data Sources](#data-sources)
- [Usage](#usage)
- [Methodology](#methodology)
- [Results](#results)
- [Contributing](#contributing)

## Introduction

This project aims to understand potential correlations between weather conditions in London and stock market indices like FTSE, SPX, DAX, and Nikkei. The analysis involves weather variables such as cloud cover, global radiation, temperature, and snow depth, along with stock indices data from 1994 to 2021. Using statistical and visual methods, this project demonstrates how external factors like weather might influence financial markets.

## Features

- **Descriptive Statistics**: Calculating standard deviation and median for weather data.
- **Visualizations**: Plotting histograms for weather variables, time-series plots of stock indices, and heatmaps for correlation analysis.
- **Correlation Analysis**: Analyzing the correlation between weather factors and stock indices, and exploring trends during specific time periods (e.g., 2005-2010, 2014-2018).
- **Data Merging**: Merging weather data with stock market data to investigate any potential relationships.
- **Handling Missing Data**: Imputation of missing values using interpolation techniques for both weather and stock market datasets.

## Installation

To use the project, follow these steps:

1. Clone the repository:
   ```bash
   git clone (https://github.com/rahulpudurkar/Weather-and-Stock-Market-Correlation-Analysis.git
   cd weather-stock-analysis
   ```

2. Install the required dependencies.

3. Download or place the required datasets (London weather data and stock market data) in the appropriate directory.

## Data Sources

- **London Weather Data**: Historical weather data for London from 2014 to 2018. This includes variables like cloud cover, global radiation, temperature, snow depth, and more.
- **Stock Market Data**: Index closing prices from 1994 to 2021 for stock markets such as FTSE, SPX, DAX, and Nikkei.

## Usage

Here is an example of how to use this notebook for visualizations and analysis:

1. **Calculate Descriptive Statistics**: 
   ```python
   df_weather[['cloud_cover', 'sunshine', 'global_radiation', 'max_temp', 'mean_temp', 'min_temp', 'precipitation', 'pressure', 'snow_depth']].std()
   ```

2. **Visualize Weather Data**:
   ```python
   for col in df_weather.columns:
       df_weather[col].hist()
       plt.show()
   ```

3. **Correlation Heatmap**:
   ```python
   correl = df_weather.corr()
   trace = go.Heatmap(z=correl.values, x=correl.index.values, y=correl.columns.values)
   plotly.offline.iplot([trace], filename='basic-heatmap')
   ```

4. **Analyze Stock Market Indices**:
   ```python
   fig = px.line(df_stock, x='Date', y='ftse', labels={'ftse': 'FTSE Value'}, title='FTSE Index Over Time')
   fig.show()
   ```

5. **Merging Weather and Stock Data**:
   ```python
   merged_data = pd.merge(weather_data_filtered, stock_subset, left_on='date', right_on='Date', how='left')
   merged_data['ftse'].interpolate(inplace=True)
   ```

## Methodology

1. **Data Preprocessing**: 
   - Handling missing values using interpolation.
   - Filtering data for specific time periods.
   
2. **Exploratory Data Analysis**:
   - Generating descriptive statistics for weather and stock data.
   - Plotting histograms and time-series visualizations.
   
3. **Correlation Analysis**:
   - Calculating correlation matrices for weather variables and stock indices.
   - Generating heatmaps to visualize correlations.

## Results

- **Stock Market Trends**: Visualization of stock market indices like FTSE, SPX, DAX, and Nikkei over time.
- **Weather Impact**: Exploration of the relationship between weather conditions (such as snow depth) and stock market performance.
- **Correlation Insights**: Heatmaps showing the strength of correlations between weather and stock indices.

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository.
2. Create a new branch for your feature (`git checkout -b feature/your-feature`).
3. Commit your changes (`git commit -m 'Add new feature'`).
4. Push to the branch (`git push origin feature/your-feature`).
5. Create a new Pull Request.

---
