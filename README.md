# Power BI Data Modeling Project

**Prepared By:** Shrey Dharmeshbhai Patel

---

## Project Overview

This project demonstrates the implementation of a complete data modeling solution in Microsoft Power BI. The objective was to import, clean, transform, model, and validate business data using industry-standard dimensional modeling techniques. The project focuses on schema design, relationship management, hierarchy creation, and data validation using Power BI and Power Query.

---

## Data Sources

The following tables were used in the project:

* Sales_fact
* Customer_Dim
* Product_Dim
* Region_Dim
* Date_dim
* Return_facts

---

## Data Preparation

All datasets were imported using Power Query. The following data preparation activities were performed:

* Imported all source files into Power BI.
* Removed blank rows and unnecessary records.
* Validated and corrected data types.
* Ensured consistency between primary key and foreign key columns.
* Loaded the cleaned datasets into the Power BI data model.

---

## Schema Design

A **Star Schema** was implemented with **Sales_fact** as the central fact table.

### Dimension Tables

* Customer_Dim
* Product_Dim
* Region_Dim
* Date_dim

### Fact Tables

* Sales_fact
* Return_facts

The Return_facts table was modeled as a secondary fact table connected to Sales_fact and Date_dim to support return analysis.

---

## Relationships

The following relationships were created:

| From Table   | To Table     | Relationship             |
| ------------ | ------------ | ------------------------ |
| Customer_Dim | Sales_fact   | CustomerID               |
| Product_Dim  | Sales_fact   | ProductID                |
| Region_Dim   | Sales_fact   | RegionID                 |
| Date_dim     | Sales_fact   | DateKey                  |
| Sales_fact   | Return_facts | SalesID                  |
| Date_dim     | Return_facts | ReturnDateKey (Inactive) |

### Relationship Settings

* Cardinality: One-to-Many (1:*)
* Cross Filter Direction: Single
* Inactive Relationship: Date_dim → Return_facts

These settings ensure efficient filter propagation while avoiding ambiguity within the model.

---

## Data Model Enhancements

### Data Formatting

Appropriate formats were assigned to all fields:

* Revenue → Currency
* Quantity → Whole Number
* Discount → Decimal Number
* Date → Date Format
* Key Columns → Whole Number

### Data Categories

The following data categories were configured:

* Country → Country/Region
* State → State or Province
* City → City

---

## Hierarchies Created

### Date Hierarchy

Year → Quarter → Month → Date

### Region Hierarchy

Country → State → City

### Product Hierarchy

Category → Subcategory → ProductName

These hierarchies allow users to drill down and explore data at multiple levels.

---

## Advanced Model Settings

The model was configured with:

* One-to-Many relationship cardinality.
* Single-direction filter propagation.
* Inactive relationship between Date_dim and Return_facts.
* Validation of filter flow and relationship behavior.

Potential ambiguity issues were avoided by maintaining single-direction filtering throughout the model.

---

## Verification

Matrix visuals were used to verify the correctness of the model.

### Verification 1

**Sales by Product Category and Region**

Validated that sales data aggregated correctly across product categories and regions.

### Verification 2

**Return Reasons by Fiscal Year**

Verified return analysis through fiscal year categorization.

### Verification 3

**Revenue by Customer Segment**

Confirmed revenue aggregation based on customer segments.

These verification steps confirmed that all relationships and hierarchies functioned as expected.

---

## Challenges and Solutions

### Challenge 1: Data Type Inconsistencies

Some columns were imported with incorrect data types.

**Solution:** Updated data types in Power Query and Power BI before loading the model.

### Challenge 2: Relationship Creation

Relationships could not be established when duplicate values existed in dimension tables.

**Solution:** Verified uniqueness of primary key columns and removed duplicate records.

### Challenge 3: Inactive Relationship Configuration

The assignment required an inactive relationship between Date_dim and Return_facts.

**Solution:** Created the relationship using ReturnDateKey and marked it as inactive.

### Challenge 4: Hierarchy Creation

Hierarchies required manual configuration.

**Solution:** Created Date, Region, and Product hierarchies to support drill-down analysis.

---

## Tools Used

* Microsoft Power BI Desktop
* Power Query
* Data Modeling
* Matrix Visualizations

---

## Conclusion

This project successfully demonstrates the implementation of a professional Power BI data model using dimensional modeling techniques. A Star Schema was designed, relationships were configured correctly, hierarchies were created, and matrix-based validation confirmed the accuracy of the model. The final solution follows Power BI best practices and supports efficient business analysis and reporting.

---

**Author:** Shrey Dharmeshbhai Patel
