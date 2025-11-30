# SigmaAldrich Data Extraction Project (2024)

This repository documents a large-scale data extraction project performed in 2024 on the SigmaAldrich product catalog.  
The goal of this project was to analyze the structure of the catalog, study product metadata relationships, and build a normalized database suitable for research and data engineering experimentation.

A total of approximately **700,000 product-related records** were extracted, cleaned, and organized across multiple relational tables.

---

## 📁 Project Overview

This project focuses on the technical aspects of large-scale web data extraction and structuring, including:

- Automated crawling of product pages
- Parsing multiple layers of product metadata
- Normalizing information into relational database tables
- Handling missing or inconsistent values
- Designing a schema optimized for analytical workloads

The dataset includes product identifiers, descriptions, physical/chemical properties, safety information, SDS/COA flags, and size/price variations.

---

## 🗄️ Database Schema

The extracted data is organized into several tables, each representing a specific category of product information.

### 1. `product`

| Column                        | Type           | Description                           |
|-------------------------------|----------------|---------------------------------------|
| Number                        | varchar(128)   | Product identifier                     |
| Name                          | varchar(128)   | Product name                           |
| Short_Description             | varchar(1024)  | Summary description                    |
| Categories                    | varchar(256)   | Category hierarchy                     |
| Brand                         | varchar(128)   | Brand name                             |
| Description                   | mediumtext     | Full product description               |
| product_info                  | tinyint(1)     | Flag indicating if info exists         |
| product_property              | tinyint(1)     | Flag indicating if property exists     |
| product_safety_information    | tinyint(1)     | Flag indicating if safety info exists  |

---

### 2. `product_info`

| Column      | Type           |
|------------|----------------|
| Number     | varchar(128)   |
| Info_Name  | varchar(256)   |
| Info_Value | varchar(512)   |

---

### 3. `product_property`

| Column        | Type           |
|---------------|----------------|
| Number        | varchar(128)   |
| Property_Name | varchar(256)   |
| Property_Value| varchar(512)   |

---

### 4. `product_safety_information`

| Column                    | Type           |
|----------------------------|----------------|
| Number                     | varchar(128)   |
| Safety_Information_Name    | varchar(256)   |
| Safety_Information_Value   | varchar(512)   |

---

### 5. `product_sds_coa`

| Column | Type       |
|--------|------------|
| Number | varchar(128) |
| SDS    | tinyint(1) |
| COA    | tinyint(1) |

---

### 6. `product_size_price`

| Column                       | Type           |
|-------------------------------|----------------|
| Number                        | varchar(128)   |
| Size                          | varchar(128)   |
| SKU                           | varchar(64)    |
| Price                         | varchar(64)    |
| Foreign_Trade_Commodity_Code  | varchar(128)   |
| CAS_Number                    | varchar(128)   |
| Packaging_Information         | varchar(128)   |

---
---

## 🧩 Technical Notes

- The scraper handled over **700,000 records** across all tables.
- Extensive error handling was implemented for missing fields and dynamic page content.
- Data was normalized to allow efficient querying and downstream analysis.
- The project demonstrates practical challenges in large-scale web extraction, including request throttling, anti-bot protection, and schema variability.

---

⚠️ Legal Note
This dataset was collected for research and educational purposes. 
The full dataset is distributed privately on request due to potential terms of service restrictions of the source website. 
Commercial use or redistribution without permission is prohibited.


## 📬 Contact

For technical discussions, consulting, or data engineering inquiries, you can reach me at:

- **Email:** parhamkhani.ir@gmail.com
- **Telegram:** t.me/parhamkhani
