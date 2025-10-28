# Cohort-Analysis


---

##  **Project Report: Cohort Analysis of Customer Retention and Behavior**

### **1. Objective**

The goal of this project is to analyze customer behavior over time by grouping users into **cohorts**—customers who made their first purchase in the same period.
Through this, we aim to:

* Understand **customer retention trends** (how many users remain active after signup).
* Measure the **average quantity purchased** across different cohorts over time.
* Identify patterns in customer engagement and purchasing behavior.

---

### **2. Data Preparation**

Before the analysis, the dataset underwent data cleaning and preprocessing (e.g., handling missing values, ensuring correct data types, etc.).

Key features used:

* **CustomerID:** Unique identifier for each customer.
* **InvoiceDate:** Date of each transaction.
* **Quantity:** Number of items purchased.

---

### **3. Creating Cohort Labels**

#### a. **Billing Period (`InvoiceMonth`)**

Each transaction date was converted to the **first day of its month** to standardize billing periods.
This allows transactions to be grouped at the month level rather than by individual dates.

#### b. **Cohort Group (`CohortMonth`)**

For each customer, the **first month they made a purchase** was identified.
This month represents their **cohort group** — the time when they first engaged with the business.

#### c. **Cohort Index (`CohortIndex`)**

The **number of months since a customer’s first purchase** was calculated.

* `1` → the month of the first purchase
* `2` → one month after their first purchase
* and so on…

This helps track how long customers remain active after joining.

---

### **4. Cohort Analysis: Retention Rate**

####  **Steps**

* Customers were grouped by `CohortMonth` and `CohortIndex`.
* For each cohort and month index, the number of **unique active customers** was counted.
* The **retention rate** was then calculated by dividing the number of active customers in each period by the total number in the first month of that cohort.

####  **Visualization**

A **heatmap** was plotted showing the retention rates over time for each cohort.

```python
sns.heatmap(data=retention, annot=True, fmt='.0%', vmin=0.0, vmax=0.5, cmap="BuPu_r")
```

####  **Findings**

* The diagonal of the heatmap represents **month 1** (when every customer is new).
* As the months progress, the retention percentages typically decline — indicating **customer churn** over time.
* Some cohorts may show **higher retention** (brighter cells), suggesting better engagement or customer experience during those months.

This retention matrix helps identify:

* When customers tend to drop off (which month).
* Which cohort performed best (e.g., after a marketing campaign).

---

### **5. Cohort Analysis: Average Quantity Purchased**

####  **Steps**

* The average **quantity purchased** by customers in each cohort and month index was calculated.
* This shows how purchasing behavior changes as customers mature.

####  **Visualization**

A second heatmap was generated showing the **average quantity purchased** per customer across cohorts.

```python
sns.heatmap(data=average_quantity, annot=True, vmin=0.0, vmax=20, cmap="BuGn_r")
```

####  **Findings**

* Some cohorts show **higher average quantities** in the early months, possibly due to new-user promotions or first-time enthusiasm.
* Over time, the quantity per customer may stabilize or decline, suggesting a **reduction in engagement**.
* Certain cohorts may show spikes, indicating **seasonal trends** or **marketing effectiveness**.

---

### **6. Key Insights**

| Aspect                   | Insight                                                                                                     |
| ------------------------ | ----------------------------------------------------------------------------------------------------------- |
| **Customer Retention**   | Retention tends to drop after the first few months — showing when customer churn happens.                   |
| **Engagement Trends**    | Some cohorts maintain steady activity, implying loyal customers or effective onboarding.                    |
| **Purchase Behavior**    | The average purchase quantity may vary by cohort, hinting at changes in buying patterns over time.          |
| **Business Application** | Findings can guide marketing, loyalty programs, and retention strategies to target cohorts with high churn. |

---

### **7. Conclusion**

This cohort analysis provides actionable insights into **customer retention and purchasing behavior**.
By tracking how different customer groups behave over time, the business can:

* Identify the **most loyal cohorts**.
* Understand **churn patterns**.
* Optimize **customer engagement and marketing strategies** to improve long-term retention.

---

### **8. Possible Next Steps**

* Extend analysis to **revenue-based cohorts** (using total spend instead of quantity).
* Perform **segmentation** by region, product type, or subscription plan.
* Use **predictive models** to forecast future retention or churn.

---
