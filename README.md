# BigBasket Grocery Data Analysis using SQL
## Project Overview
The **BigBasket Grocery Data Analysis** project focuses on analyzing grocery sales data using **SQL, Excel, and Power BI**.
The project explores sales performance, product characteristics, customer ratings, and outlet-level distribution to identify meaningful business patterns. SQL queries are used to transform the raw dataset into analytical summaries, while Power BI can be used to present the findings through interactive dashboards.  

The analysis is designed around key business questions such as:  
* How much revenue is generated from the complete product portfolio?  
* What is the average sales value per item?  
* How many product records are available?  
* What is the average customer rating?  
* How do sales vary based on product fat content?  
* Which product types contribute most to sales?  
* How does product performance differ across outlet locations?  
* Does outlet establishment year have an impact on sales?  
* What percentage of revenue comes from different outlet sizes?   
* Which outlet locations contribute the most to overall sales?
* How do different outlet types compare across major KPIs?  

## 🛠️ Tools & Technologies
The project uses the following tools:  
* **SQL** – Data analysis, aggregation, grouping, and KPI calculation
* **Microsoft Excel** – Dataset inspection and preparation
* **Power BI** – Interactive visualization and dashboard development

## 📂 Dataset
The analysis uses grocery transaction-level data containing information about products, sales, outlet characteristics, and customer ratings.  

### Main Dataset Fields

Field        | Description
------------- | -------------
**Item Fat Content** | Fat-content classification of the product
**Item Type** | Product category/type
**Sales**  | Revenue generated from the item
**Rating** | Customer rating associated with the product
**Outlet Location Type**  | Classification of the outlet's location
**Outlet Establishment Year** | Year in which the outlet was established
**Outlet Size**  | Size classification of the outlet
**Outlet Type** | Type or format of the outlet

## 📊 SQL Analysis
The following SQL queries were created to answer important business questions from the grocery dataset.  
### 1. Overall Revenue Generated
#### Business Question
What is the total revenue generated from all products available in the dataset?  
```text
SELECT CONCAT(CAST(SUM(Sales) / 1000000 AS DECIMAL(10,2)), 'M') AS Total_Sales_Millions FROM bigbasket_grocery_data;
```
#### Insight
This calculation provides a high-level view of the total revenue generated across the entire product portfolio. It can be used as a starting point for evaluating the overall scale of sales activity.  

### 2. Average Revenue per Sale
#### Business Question
What is the average sales value generated per product entry?  
```text
SELECT CONCAT( CAST(AVG(Sales)AS DECIMAL(10,0)), 'M') AS Avg_Sales FROM bigbasket_grocery_data;
```
#### Insight
The average sales metric provides an indication of the typical revenue associated with an individual product record. Comparing this value with product-level and category-level results can help understand whether sales are concentrated among higher-value products or distributed across a larger volume of items.  

### 3. Total Number of Items
#### Business Question
How many product records are present in the dataset?  
```text
SELECT COUNT(*) AS Total_No_Items FROM bigbasket_grocery_data;
```
#### Insight
This query measures the total number of item records available for analysis and provides an indication of the breadth of the grocery product dataset.  

### 4. Average Customer Rating
#### Business Question
What is the average customer rating across all products?  
```text
SELECT CAST(AVG(Rating) AS DECIMAL(10,2)) AS Avg_Rating FROM bigbasket_grocery_data;
```
#### Insight
Average rating provides a general indicator of customer feedback associated with the products. It can be analyzed alongside sales performance to understand the relationship between product popularity and customer ratings.  

### 5. Sales Analysis by Fat Content
#### Business Objective
Analyze how sales performance varies between different product fat-content classifications.  
```text
SELECT `Item Fat Content`, CONCAT( CAST(SUM(Sales) / 1000 AS DECIMAL(10,2)), 'k' ) AS Total_Sales_Thousands, CONCAT( CAST(AVG(Sales) AS DECIMAL(10,0)), 'M' ) AS Avg_Sales, COUNT(*) AS Total_No_Items, CAST(AVG(Rating) AS DECIMAL(10,2)) AS Avg_Rating FROM bigbasket_grocery_data GROUP BY `Item Fat Content` ORDER BY Total_Sales_Thousands DESC;
```
#### Insight
Grouping sales by fat content makes it possible to compare different product classifications based on revenue, number of items, average sales, and customer ratings. These comparisons can provide useful information for assortment planning and product-level analysis.  

### 6. Sales Performance by Item Type
#### Business Objective
Determine how different product types contribute to overall sales.  
```text
SELECT `Item Type`, CONCAT( CAST(SUM(Sales) / 1000 AS DECIMAL(10,2)), 'k') AS Total_Sales, CONCAT(CAST(AVG(Sales) AS DECIMAL(10,0)), 'M') AS Avg_Sales, COUNT(*) AS Total_No_Items, CAST(AVG(Rating) AS DECIMAL(10,2)) AS Avg_Rating FROM bigbasket_grocery_data GROUP BY `Item Type` ORDER BY Total_Sales;
```
#### Insight
This analysis provides a product-type-level comparison using multiple KPIs. It can help identify which product groups contribute more revenue and how their sales levels compare with customer ratings and item volumes.  




























