# youtube-data-analysis

This project involves the creation of a data pipeline for processing YouTube analytics data. The pipeline includes data ingestion from Kaggle datasets, data cleansing using AWS Glue, and storage in an S3 bucket. Additionally, it covers the process of querying the cleansed data using Amazon Athena.

## Project Components

1. **Data Ingestion:**
   - Kaggle datasets were uploaded to an S3 bucket.
   - AWS Glue was used to crawl and catalog the datasets.

2. **Data Cleansing:**
   - An AWS Glue ETL job was created to transform and cleanse the raw data.
   - The cleansing process includes filtering data based on the 'region' column with a predicate pushdown.

3. **Data Storage:**
   - The cleansed data is stored in a Parquet format in an S3 bucket.
   - The data is partitioned by the 'region' column for efficient querying.

4. **Data Querying:**
   - Amazon Athena is utilized to query the cleansed data in an interactive manner.
   - Sample queries are provided to demonstrate data exploration capabilities.

## Project Structure

- `lambda_function.py`: AWS Lambda function for processing and storing JSON data into the cleansed layer.
- `pyspark_code.py`: AWS Glue script for ETL job.
- `readme.md`: Documentation for the project.

## AWS Services Used

- S3: Storage of raw and cleansed data.
- Glue: ETL job for data cleansing.
- Athena: Querying cleansed data.
- Lambda: Serverless function for processing and storing JSON data.

## How to Run

1. **Data Ingestion:**
   - Upload Kaggle datasets to the specified S3 bucket.
   - Run the Glue Crawler to catalog the datasets.

2. **Data Cleansing:**
   - Execute the Glue ETL job (`pyspark_code.py`) to transform and cleanse the data.

3. **Data Storage:**
   - The cleansed data will be stored in the specified S3 bucket.

4. **Data Querying:**
   - Use Athena to run SQL queries on the cleansed data.

## Sample Queries

Here are a few sample queries to get started with data exploration:

```sql
-- Sample Query 1: Get total views by region
SELECT region, SUM(views) AS total_views
FROM your_cleansed_table
GROUP BY region;

-- Sample Query 2: Find top 10 videos with the highest likes
SELECT video_id, title, likes
FROM your_cleansed_table
ORDER BY likes DESC
LIMIT 10;

## Architecture Diagram
<img src="architecture.jpeg">


##kaggle dataset link

https://www.kaggle.com/datasets/datasnaek/youtube-new