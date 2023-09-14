# PostgreSQL-PgAdmin-Project
Populating a Data Warehouse using PostgreSQL.


## Database:
The database  used in this lab. contains the following tables:

* DimCustomer
* DimMonth
* FactBilling

A cloud service provider has provided us with their billing data. This file contains billing data from the past 10 years. We need to design a data warehouse to support insightful queries on this data.

# File Description

This document describes the fields of the database table, including their names and details.

| Field Name       | Details                                                               |
|------------------|-----------------------------------------------------------------------|
| customerid       | The unique identifier for each customer.                              |
| category         | The category of the customer, which can be 'Individual' or 'Company'.|
| country          | The country where the customer is located.                            |
| industry         | The domain or industry to which the customer belongs (e.g., Legal, Engineering). |
| month            | The month for which billing information is recorded, stored in YYYY-MM format . |
| billedamount     | The amount charged by the cloud services provider for that month, measured in USD. |


The fact in this data is the monthly bill, therefore the customer ID and billed amount are the key fields in the fact table. with this We can create 2 dimensions table with the following descripton:

# Customer Table
This contains information about customers.

| Field Name  | Details                                 |
|-------------|-----------------------------------------|
| customerid  | Primary Key - Id of the customer        |
| category    | Category of the customer. Example: Individual or Company |
| country     | Country of the customer                 |
| industry    |  domain/industry the customer belongs to. Example: Legal, Engineering |

# Bill-Date information

These fields are derived to provide information about the date of the bill.

| Field Name  | Details                                 |
|-------------|-----------------------------------------|
| monthid     | Primary Key - Id of the month           |
| year        | Year derived from the month field of the original data. Example: 2010 |
| month       | Month number derived from the month field of the original data. Example: 1, 2, 3 |
| monthname   | Month name derived from the month field of the original data. Example: March |
| quarter     | Quarter number derived from the month field of the original data. Example: 1, 2, 3, 4 |
| quartername | Quarter name derived from the month field of the original data. Example: Q1, Q2, Q3, Q4 |

# The final fact table for the bill wi be structured as:

| Field Name   | Details                                                |
|--------------|--------------------------------------------------------|
| billid       | Primary key - A unique identifier for each bill       |
| customerid   | Foreign Key - The ID of the customer associated with the bill |
| monthid      | Foreign Key - The ID of the month, used to resolve the billed month information |
| billedamount | Amount charged by the cloud services provider for that month in USD |




### Here are some of the things we need to consider when designing the data warehouse:

1. The size of the data set.
2. The types of queries that will be run against the data.
3. The performance requirements for the queries.
4. The security requirements for the data.

   

# Output

* schema:
![Pgadmin login](https://github.com/wafemi999/PostgreSQL-PgAdmin-Project/blob/main/SC/pgadminlogin.JPG)
![Schema](https://github.com/wafemi999/PostgreSQL-PgAdmin-Project/blob/main/SC/star-schema.JPG)

![create Production Db](https://github.com/wafemi999/PostgreSQL-PgAdmin-Project/blob/main/SC/createDb.JPG)
![upload sql](https://github.com/wafemi999/PostgreSQL-PgAdmin-Project/blob/main/SC/upload%20dataset.JPG)
![verify dataset](https://github.com/wafemi999/PostgreSQL-PgAdmin-Project/blob/main/SC/desribe%20dataset.JPG)
![Avg_billing_per_customer](https://github.com/wafemi999/PostgreSQL-PgAdmin-Project/assets/36579635/65bb49ed-1520-40d6-904e-c1d493ac78c9)

## Requirements.:

* A PostgreSQL instance running on your computer.
* The pgAdmin graphical user interface tool.
* The scripts in the FILES foloder already contains the data for  DimCustomer, DimMonth, and FactBilling tables.
