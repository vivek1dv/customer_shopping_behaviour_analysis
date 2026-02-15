# customer_shopping_behaviour_analysis
This repository presents an end-to-end customer shopping behavior analysis using real-world transactional data (3,900+ purchases). The project demonstrates how raw data can be transformed into actionable business insights through a structured analytics workflow involving Python, SQL, and Business Intelligence.




# Customer Shopping Behavior 

## Project Background
 This project provides a 360-degree view of 3,900+ transactions to identify high-value customer segments and optimize our marketing spend.. 

By analyzing demographics, seasonal trends, and subscription ROI, this project provides a data-driven roadmap to optimize marketing spend and enhance customer lifetime value (CLV).

Insights and recommendations are provided on the following key areas:
- **Customer Demographic Performance:** Analyzing revenue and engagement across age groups and gender.
- **Product & Seasonal Trends:** Identifying high-velocity items and seasonal purchase triggers.
- **Subscription & Loyalty Dynamics:** Evaluating the ROI of our subscription model and repeat-purchase behavior.
- **Promotional & Logistics Impact:** Assessing how discounts and shipping preferences influence final checkout amounts.

The Python scripts used to inspect and clean the data for this analysis can be found here: [data_cleaning_python](https://github.com/vivek1dv/vivek1dv-customer_shopping_behaviour_analysis/blob/main/customer_shopping_behaviour.ipynb)

Targeted SQL queries regarding various business questions can be found here: [sql_analysis_queries](https://github.com/vivek1dv/vivek1dv-customer_shopping_behaviour_analysis/blob/main/customer_shopping_behaviour_sql.sql)

An interactive Power BI dashboard used to report and explore sales trends can be found here: [Power_bi_dashboard](https://github.com/vivek1dv/vivek1dv-customer_shopping_behaviour_analysis/blob/main/customer_shopping_behaviour_dashboard_bi.pbix)

# Data Structure & Initial Checks
The company's primary analytical dataset consists of a unified transactional table with a total row count of 3,900+ records.

- **customer (Raw):** The source of truth containing 19 features including demographics (Age, Gender), transaction details (Item, Category, Amount), and behavioral markers (Discounts, Frequency).
- **customer_staging1 (Processed):** The optimized SQL table used for final analysis, featuring engineered columns like `age_group` and cleaned rating values for easier segmentation.



![alt text](https://github.com/vivek1dv/vivek1dv-customer_shopping_behaviour_analysis/blob/main/columns_name.png)


# Executive Summary

### Overview of Findings
Our analysis reveals a robust retail ecosystem driven heavily by the Male demographic (67% of revenue) and the Clothing category, which remains our primary revenue engine. While we maintain a healthy average rating of 3.75, there is a significant opportunity to convert our "Returning" customer base into "Subscribers," as the current subscription penetration sits at only 27%. To drive growth, we must bridge the revenue gap between genders and capitalize on the high-spending "Young Adult" segment.

# Insights Deep Dive

### Customer Demographic Performance
* **Male Dominance in Revenue.** Male customers generated approximately **$157,890** in revenue, significantly outperforming female contributors (**$75,191**).
* **Young Adult Spending Power.** The "Young Adult" age group (18-30) is our most valuable demographic, contributing **$62,143** to total revenue, indicating strong brand resonance with Gen Z and Millennials.
* **The "Senior" Segment Opportunity.** Despite common retail assumptions, the "Senior" group (60+) remains highly active, contributing over **$55,763**, nearly matching the "Adult" (46-60) segment.
* **Geographic Outliers.** Sales are distributed across 50 states, but specific locations show higher average spends regardless of volume, indicating localized premium preferences that should be targeted for specialized marketing.

![alt text](https://github.com/vivek1dv/vivek1dv-customer_shopping_behaviour_analysis/blob/main/overview_finding.png)


### Product & Seasonal Trends
* **Clothing is King.** The Clothing category is the top performer, generating over **$104,264** in sales—more than Accessories and Footwear combined.
* **High-Velocity Items.** Blouses, Shirts, and Dresses are consistently the most purchased items, regardless of seasonal shifts, representing our "Core" inventory.
* **Seasonality of Purchase.** Spring and Fall show the highest transaction volumes, suggesting that our "New Collection" launches are well-timed with consumer appetite.
* **Review Ratings Stability.** Product satisfaction is consistent across categories (avg 3.7-3.8), indicating that our product quality meets market expectations.

![alt text](https://github.com/vivek1dv/vivek1dv-customer_shopping_behaviour_analysis/blob/main/clothing_revenue_share_dashboard.png)

### Subscription & Loyalty Dynamics
* **Subscription Gap.** Only **27%** of our customers are currently subscribed. However, subscribers show a more consistent purchase frequency than non-subscribers.
* **The "Loyal" Segment.** Customers with 10+ previous purchases (defined as "Loyal" in SQL) account for the most stable revenue stream but are not always the highest per-transaction spenders.
* **Frequency vs. Value.** "Weekly" and "Bi-Weekly" shoppers tend to buy lower-value items more often, whereas "Annually" shoppers make high-value bulk purchases.
* **Review Influence.** Subscribed customers are slightly more likely to leave ratings, providing a critical feedback loop for inventory selection.



### Promotional & Logistics Impact
* **Discount Sensitivity.** A significant portion of high-value transactions (>Avg spend) utilized a discount code, indicating that promotions are a successful "nudge" for premium items.
* **Shipping Preferences.** Standard and Express shipping are the most common choices; however, Express shipping does not show a strong correlation with higher-value baskets, suggesting customers value speed regardless of price.
* **Payment Trends.** PayPal and Credit Cards are the leading payment methods, though Venmo is seeing significant traction among the Young Adult segment.
* **Promo Code ROI.** Orders using promo codes successfully moved inventory in slower-moving categories like "Outerwear" during off-peak seasons.

# Recommendations

Based on the insights and findings above, I recommend the **Marketing and Operations teams** consider the following:

* **Gender-Targeted Campaigns:** Female revenue is roughly 50% of male revenue. **Launch targeted marketing campaigns specifically for women to balance the revenue portfolio and capture untapped market share.**
* **Subscription Conversion Program:** With only 27% of customers subscribed, we are leaving recurring revenue on the table. **Implement a "First-Order Subscriber Discount" to convert "New" customers immediately.**
* **Loyalty Tiering:** Our "Returning" customers (2-10 purchases) are the largest group. **Create a "Silver-to-Gold" loyalty tier to incentivize these customers to reach the 11+ purchase "Loyal" status through exclusive perks.**
* **Inventory Alignment:** Clothing drives the majority of revenue. **Increase inventory depth in high-velocity items (Blouses, Shirts) while using seasonal "Outerwear" flash sales to maintain margins during slow months.**
* **Young Adult Retention:** Since 18-30s are our highest spenders, **incorporate more Venmo/social-pay options and mobile-first promotional alerts to cater to their specific shopping habits.**

# Assumptions and Caveats

Throughout the analysis, multiple assumptions were made to manage challenges with the data:

* **Missing Data Handling:** 37 missing records in the `Review Rating` column were imputed using the **median rating** of that specific product category to prevent skewing satisfaction metrics.
* **Age Grouping:** Customers were segmented into four distinct buckets (Young Adult, Middle-aged, Adult, Senior) based on 15-year intervals to provide actionable marketing personas.
* **Loyalty Definition:** "Loyal" customers were defined as those with **>10 previous purchases**, while "New" customers were defined as those with **1 purchase**, based on standard retail industry benchmarks.
* **Revenue Calculation:** The `Purchase Amount` was assumed to be the net value after any applied discounts, as no separate "Gross Amount" column was provided.
