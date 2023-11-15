# Home_Sales
Module 22 Challenege
# SparkSQL Home Sales Data Analysis

## Project Overview

This project involves leveraging SparkSQL to analyze and query home sales data. The analysis includes importing data, creating temporary views, running SQL queries, caching data for performance improvement, comparing query runtimes, and working with Parquet data.

## Project Structure

The project follows these key steps:

### 1. Importing Packages

The necessary Python packages, including `findspark` and `pyspark.sql`, are imported to initialize Spark and work with SparkSQL.

### 2. Creating a SparkSession

A SparkSession is created using `SparkSession.builder.appName("SparkSQL").getOrCreate()` to establish a connection to Spark.

### 3. Reading Data

Home sales data is read from an AWS S3 bucket into a DataFrame using the provided URL.

### 4. Creating a Temporary View

A temporary view named "my_sale_table" is created for the DataFrame using `createOrReplaceTempView()` to enable SQL queries on the DataFrame.

### 5. Querying the Data

Several SQL queries are executed to analyze the home sales data. This includes calculating the average price for a four-bedroom house sold in each year and the average price of homes based on different criteria such as bedrooms, bathrooms, and square footage.

### 6. Caching the Data

The temporary table "my_sale_table" is cached using `spark.catalog.cacheTable()` to improve query performance by storing the data in memory.

### 7. Query Runtime Comparison

The runtime of a specific query is compared between the cached version and the version using Parquet data. The start time is recorded using `time.time()` before executing each query, and the difference in time is calculated to measure the runtime.

### 8. Writing Parquet Data

The formatted home sales data is written to Parquet format with partitioning based on the "date_built" field using the `partitionBy().parquet()` method.

### 9. Reading Parquet Data

The Parquet data is read into a DataFrame to perform further analysis.

### 10. Creating a Temporary Table for Parquet Data

A temporary table named "parquet_table" is created for the Parquet DataFrame using `createOrReplaceTempView()`.

### 11. Querying Parquet Data

SQL queries are executed on the Parquet DataFrame to filter out view ratings with an average price greater than or equal to $350,000. The runtime is measured and compared to the cached version.

### 12. Uncaching the Temporary Table

The temporary table "my_sale_table" is uncached using `spark.catalog.uncacheTable()` to release memory resources.

### 13. Checking Caching Status

The caching status of the table "my_sale_table" is checked using `spark.catalog.isCached()` to confirm whether it is still cached or not.

## Conclusion

This project demonstrates the utilization of SparkSQL for reading, querying, caching, and analyzing home sales data, providing valuable insights into average prices based on various criteria.
