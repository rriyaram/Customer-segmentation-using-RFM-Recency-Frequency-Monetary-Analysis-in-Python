# Customer-segmentation-using-RFM-Recency-Frequency-Monetary-Analysis-in-Python
Segment Customers Based on Purchasing Behaviour
 Project Overview

This project performs Retail Sales Data Analysis and implements RFM (Recency, Frequency, Monetary) Analysis to segment customers based on their purchasing behavior.

The objective is to help businesses:

Identify high-value customers

Detect inactive or at-risk customers

Improve retention strategies

Increase revenue through targeted marketing

 Business Problem

Retail businesses often struggle to:

Identify loyal customers

Understand purchase behavior patterns

Improve customer retention

Maximize revenue from existing customers

This project solves these problems using data-driven customer segmentation.

 Dataset Information

Rows: 1000

Columns: 9

Type: Retail transaction data

Key Columns Used:

CustomerID

InvoiceDate

Quantity

UnitPrice

 Tools & Technologies

Python

Pandas

NumPy

Matplotlib

Seaborn

Jupyter Notebook

 Project Workflow
1️⃣ Data Cleaning

Removed missing values

Removed negative quantities

Converted InvoiceDate to datetime

Created TotalAmount = Quantity × UnitPrice

2️⃣ RFM Calculation
Recency

Days since last purchase.

Frequency

Total number of purchases per customer.

Monetary

Total revenue generated per customer.

rfm = df.groupby("CustomerID").agg({
    "InvoiceDate": lambda x: (snapshot_date - x.max()).days,
    "InvoiceNo": "nunique",
    "TotalAmount": "sum"
})

3️⃣ RFM Scoring

Customers were divided into quartiles (1–4) using pd.qcut().

rfm["R_Score"] = pd.qcut(rfm["Recency"], 4, labels=[4,3,2,1])
rfm["F_Score"] = pd.qcut(rfm["Frequency"].rank(method="first"), 4, labels=[1,2,3,4])
rfm["M_Score"] = pd.qcut(rfm["Monetary"], 4, labels=[1,2,3,4])

4️⃣ Customer Segmentation

Customers were grouped into segments such as:

🏆 Champions

💎 Loyal Customers

🔥 Potential Loyalists

⚠️ At Risk

❌ Lost Customers

 Visualizations Included

Recency, Frequency, Monetary Distributions

RFM Heatmap

Revenue Contribution by Segment

RFM Score Distribution

Cumulative Revenue Curve (Pareto Analysis)

Segment-wise Boxplots

 Key Insights

Most customers made only one purchase (low retention rate).

A small percentage of customers generate a large portion of revenue.

Several customers are at risk due to high recency values.

Targeted marketing strategies can significantly improve retention.

 Business Recommendations

Implement loyalty programs for repeat purchases.

Offer personalized discounts to at-risk customers.

Focus marketing campaigns on high-value segments.

Use email re-engagement campaigns for inactive customers.

 Outcome

This project successfully demonstrates how RFM analysis can:

Improve customer segmentation

Enhance marketing efficiency

Increase customer lifetime value

Support data-driven decision making

 Future Improvements

Implement K-Means clustering on RFM scores

Build Customer Lifetime Value (CLV) prediction model

Deploy interactive dashboard using Power BI 

 Conclusion

RFM analysis provides a simple yet powerful framework to understand customer behavior and improve business strategies. This project demonstrates practical implementation using Python for real-world retail data.
