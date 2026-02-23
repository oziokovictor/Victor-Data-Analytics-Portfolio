Portfolio
│
├── Dashboards
├── Datasets
├── SQL
└── README.md

hospital_analysis.sql

-- Create Hospital Table
CREATE TABLE hospital_patients (
    patient_id INT,
    admission_date DATE,
    department VARCHAR(50),
    gender VARCHAR(10),
    diagnosis VARCHAR(100),
    length_of_stay INT
);

-- Total Patients
SELECT COUNT(*) AS total_patients
FROM hospital_patients;

-- Patients by Department
SELECT department, COUNT(*) AS total_patients
FROM hospital_patients
GROUP BY department
ORDER BY total_patients DESC;

-- Average Length of Stay
SELECT AVG(length_of_stay) AS avg_stay
FROM hospital_patients;

-- Gender Distribution
SELECT gender, COUNT(*) AS total
FROM hospital_patients
GROUP BY gender;

sales_analysis.sql

-- Create Sales Table
CREATE TABLE sales_data (
    order_id INT,
    order_date DATE,
    region VARCHAR(50),
    product VARCHAR(100),
    category VARCHAR(50),
    quantity INT,
    unit_price DECIMAL(10,2)
);

-- Total Revenue
SELECT SUM(quantity * unit_price) AS total_revenue
FROM sales_data;

-- Sales by Region
SELECT region,
       SUM(quantity * unit_price) AS revenue
FROM sales_data
GROUP BY region
ORDER BY revenue DESC;

-- Sales by Category
SELECT category,
       SUM(quantity * unit_price) AS revenue
FROM sales_data
GROUP BY category;

-- Top Products
SELECT product,
       SUM(quantity) AS total_sold
FROM sales_data
GROUP BY product
ORDER BY total_sold DESC;

Hospital Dataset Columns

patient_id
admission_date
department
gender
diagnosis
length_of_stay

Sales Dataset Columns

order_id
order_date
region
product
category
quantity
unit_price

