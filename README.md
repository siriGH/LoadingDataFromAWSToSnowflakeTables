# LoadingDataFromAWSToSnowflakeTables
Creating stotrage intigration between AWS S3 and Snowflake, uploading files into S3 and loading those file data into snowflake tables.

This project showcases a hands-on implementation of loading semi-structured and structured data from AWS S3 into Snowflake using a secure and reusable integration setup. 
Technologies Used
AWS S3 – Cloud object storage for storing CSV and JSON files.
AWS IAM – Role-based access for secure integration.
Snowflake – Cloud data warehouse for loading and querying the data.
SQL – Used for creating stages, file formats, and executing data copy commands.
Project Workflow
AWS Setup

Created a new AWS account and an S3 bucket to store data files.
Uploaded sample CSV and JSON files to specific S3 bucket paths (/csv/ and /json/).
Created an IAM Role and attached permissions to allow Snowflake access to S3.

Snowflake Integration

Created a Storage Integration in Snowflake using the IAM Role ARN.
Retrieved the EXTERNAL_ID from Snowflake and updated the trust policy in the AWS IAM Role.
Defined allowed locations for secure access to only relevant folders in S3.

File Format & Stage Setup

Created a file format in Snowflake to define the structure of the CSV file (pipe-delimited, skip header).
Created an external stage linked with the storage integration and file format to access the S3 bucket.

Data Loading

Created a target table in Snowflake to match the schema of the CSV file.
Used the COPY INTO command with a PATTERN to load multiple files at once based on file naming (e.g., files with "customer" in their name).
Validated the data using SELECT queries to ensure the load was successful.

Data Validation & Flexibility

Successfully verified the loaded records.
Also able to list and access individual files in S3 directly through the external stage.
Learnings
Understood the importance of using storage integrations for secure, scalable, and reusable access between Snowflake and AWS.
Learned how to use PATTERN matching in the COPY INTO command to load multiple files in a single operation.
Gained practical experience in combining cloud storage with data warehousing to build real-world data pipelines.

