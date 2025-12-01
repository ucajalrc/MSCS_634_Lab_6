# **NOTE:  Since instacard order product file was too large even after zipping it, I had to upload it to one drive so, please download it first in your repo: https://cumber-my.sharepoint.com/:u:/r/personal/arc39456_ucumberlands_edu/Documents/order_products__prior.csv.zip?csf=1&web=1&e=mt8svz**

# **MSCS 634 – Lab 6: Association Rule Mining with Apriori and FP-Growth**

### *Instacart Market Basket Analysis*

## **Overview**

This lab explores **association rule mining** using the Instacart Market Basket dataset.
The goal was to transform real-world purchase data into meaningful insights by:

* Preparing order–product transactions
* Mining **frequent itemsets** using **Apriori** and **FP-Growth**
* Generating **association rules** (support, confidence, lift)
* Visualizing item frequency patterns and item co-occurrence
* Comparing the performance and output of the two algorithms

This lab demonstrates how association rule mining helps uncover hidden relationships in large transactional datasets — the same techniques used in retail for recommendation systems and product placement.

---

## **Dataset Used**

The dataset comes from the Instacart Market Basket Analysis project.
Files used:

* **order_products__prior.csv**
* **products.csv**

We merged these files to connect each `order_id` with corresponding `product_name` and then constructed transaction baskets for each order.

Due to the dataset’s large size, a subset of orders was sampled for computational efficiency while still maintaining realistic item distribution patterns.

---

## **Lab Purpose**

The primary goals of the lab were:

1. **Understand how transactional data is transformed into baskets** suitable for association mining
2. **Apply Apriori and FP-Growth** to extract frequent item combinations
3. **Generate and interpret association rules** to identify strong consumer purchase patterns
4. **Visualize item frequencies and co-occurrences** using Seaborn
5. **Compare algorithm behavior and efficiency** on real transactional data

This lab gives practical experience with the exact techniques used in:

* Recommender systems
* Market basket analysis
* Retail promotions
* Inventory optimization

---

## **Key Insights**

### **1. Frequent Itemsets**

Both Apriori and FP-Growth identified item pairs and triplets that commonly appear together in orders.
Frequent items typically included:

* Bananas
* Yogurt
* Milk
* Fresh produce

This aligns with real Instacart purchasing behavior — certain staple items appear in many baskets.

### **2. Association Rules**

Rules were generated using **confidence and lift** to identify meaningful shopping patterns.

Examples of interpretable patterns include:

* Items from similar categories often co-occur (e.g., dairy items)
* Essential groceries (like bananas and milk) form the backbone of many strong rules
* High-lift rules indicated products that are disproportionately purchased together

These rules are exactly the type used in recommendation engines such as:
*“Customers who bought X also bought Y.”*

### **3. Apriori vs FP-Growth Performance**

A clear difference appeared:

| Algorithm     | Speed       | Frequent Itemsets | Notes                                        |
| ------------- | ----------- | ----------------- | -------------------------------------------- |
| **Apriori**   | Slower      | Fewer             | Expensive joins and candidate generation     |
| **FP-Growth** | Much faster | More              | Compresses data using FP-tree; more scalable |

FP-Growth was more efficient and returned a richer set of patterns using the same support threshold.

---

## **Challenges and How They Were Addressed**

### **1. Dataset Size (Millions of Rows)**

Instacart is very large, and Apriori does not scale well.
**Solution:**
We sampled a subset of orders while preserving realistic item distributions.

### **2. Memory & Run-Time Constraints**

Apriori especially can become slow or fail for large datasets.
**Solution:**

* Started with a **higher support threshold** (e.g., 1%)
* Used FP-Growth for comparison
* Limited analysis to most frequent items during heatmap generation

### **3. Data Cleaning**

Some product names were missing in the raw files.
**Solution:**
Rows with missing `product_name` values were dropped to avoid errors in encoding.

### **4. Choosing Good Hyperparameters**

* Too low support → millions of itemsets
* Too high support → almost no itemsets
  **Solution:**
  Experimented until a balanced support threshold was found that produced meaningful itemsets without overwhelming computation.

---

## **Visualizations Included**

* **Bar plot of most frequent items**
* **Heatmap of top co-occurring products**
* **Frequent itemsets (Apriori & FP-Growth)**
* **Confidence vs Lift scatterplots for association rules**

These visualizations helped interpret patterns that weren’t obvious from raw data.

---

## **Conclusion**

This lab provided hands-on experience with association rule mining from start to finish.
Using real retail data made it clear how Apriori and FP-Growth differ not only in performance but also in the quality and quantity of insights they help uncover.

The results demonstrate how retailers can:

* Understand purchasing behavior
* Improve product recommendations
* Optimize promotions and store planning
* Enhance customer experience
* 
Overall, this lab strengthened practical skills in data mining, pattern discovery, and working with large transactional datasets.
