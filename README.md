# AWS Sales Data Engineering

## Project Overview

This is a beginner-friendly end-to-end Sales Data Engineering project built using **PySpark, Amazon S3, and Amazon Athena**.

The project demonstrates how raw CSV sales data can be processed and transformed using PySpark, stored in Amazon S3, and analyzed using SQL through Amazon Athena.

The project focuses on learning the fundamentals of a cloud-based data engineering workflow.

---

## Business Problem

A retail business has sales data stored in multiple CSV files containing information about customers, orders, and products.

The objective is to combine and transform these datasets into a clean sales dataset, store it in Amazon S3, and make it available for SQL-based analysis using Amazon Athena.

The project answers questions such as:

- How many orders were placed?
- What are the total sales?
- Which states generate the most sales?
- Which products and categories perform best?
- How many orders are completed or cancelled?
- Which customers place multiple orders?
- How do sales change month by month?

---

## Dataset

The project uses three CSV datasets:

### Customers

Contains customer information:

- Customer ID
- Customer Name
- City
- State
- Signup Date

### Orders

Contains sales transaction information:

- Order ID
- Order Date
- Customer ID
- Product ID
- Quantity
- Order Status

### Products

Contains product information:

- Product ID
- Product Name
- Category
- Subcategory
- Unit Price

The datasets are used for learning purposes and are not included in this repository.

---

## Technologies Used

- **Python** – Programming language used for data processing
- **PySpark** – Data cleaning, transformation, and joining
- **Apache Spark** – Distributed data processing framework
- **Amazon S3** – Cloud storage for raw and processed data
- **Amazon Athena** – Serverless SQL analysis
- **SQL** – Data analysis and aggregation
- **Jupyter Notebook** – PySpark development environment
- **Git & GitHub** – Version control and project management

---

## Project Workflow

### 1. Load Raw Data

The three CSV files are loaded into PySpark DataFrames using Spark's CSV reader.

Customers CSV → PySpark DataFrame  
Orders CSV → PySpark DataFrame  
Products CSV → PySpark DataFrame

### 2. Data Exploration

The datasets are inspected to understand:

- Number of records
- Column names
- Data types
- Missing values
- Data structure

### 3. Data Cleaning

The data is cleaned using PySpark by:

- Handling missing values
- Checking data types
- Validating records
- Removing unnecessary data where required

### 4. Data Transformation

New columns are created and existing data is transformed for analysis.

Sales Amount = Quantity × Unit Price

Additional fields such as order month and order month name are also created.

### 5. Data Joining

The Customers, Orders, and Products datasets are joined using their respective IDs.

Orders
├── Customer ID → Customers
└── Product ID → Products

This produces a final combined sales dataset.

### 6. Store Processed Data in Amazon S3

The processed dataset generated using PySpark is stored in Amazon S3.

The S3 structure is organized as:

S3 Bucket
├── raw/
│   ├── customers.csv
│   ├── orders.csv
│   └── products.csv
│
├── Processed/
│   └── processed sales data
│
└── athena-results/
    └── Athena query results

### 7. Create Athena Database and Table

Amazon Athena is used to create a database and external table pointing to the processed data stored in S3.

Database: sales_db  
Table: result_athena

### 8. SQL Analysis

SQL queries are executed in Amazon Athena to analyze the processed sales data.

The analysis includes:

- Total orders
- Total sales
- Average order value
- Sales by state
- Sales by category
- Monthly sales
- Top 5 products by sales
- Top 5 customers by sales
- Orders by status
- Sales by city
- Sales by subcategory
- Repeat customers
- Quantity sold by category
- Completed orders and sales
- Cancelled orders and sales
- Highest-value orders
- Category and order status analysis
- Monthly sales summary

All SQL queries are available in:

athena_queries.sql

---

### Future Improvements

The project can be extended into a more advanced data engineering pipeline by:

- Using AWS Glue for automated ETL
- Using AWS Lambda for event-driven processing
- Automating the pipeline
- Scheduling regular data processing
- Converting CSV data to Apache Parquet
- Partitioning data in Amazon S3
- Adding data quality checks
- Adding monitoring and logging
- Connecting Athena to a BI tool such as Power BI
 
