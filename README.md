# Uncovering Hidden Patterns: Market Basket Analysis Demystified

In the era of data-driven decision-making, businesses are constantly seeking innovative ways to understand their customers better. Market Basket Analysis (MBA) is a powerful technique that has emerged as a cornerstone of this endeavor. It enables businesses to unravel hidden patterns within transactional data and make informed decisions. In this article, we will explore the concept of Market Basket Analysis and illustrate its practical application using the Instacart Market Basket Analysis dataset.

## Understanding Market Basket Analysis
Market Basket Analysis is a data mining technique focusing on uncovering associations and relationships between products or items customers purchase. The core idea is simple yet profound: By identifying item associations, businesses can optimize their strategies, enhance the customer experience, and boost sales.

## Case study
  - Groceries Dataset ➡️ I have discussed the Groceries Dataset on my [Medium](https://medium.com/@salsabilabasalamah/market-basket-analysis-with-r-7104c09cedab)
  - [Instacart Market Basket Analysis](https://www.kaggle.com/c/instacart-market-basket-analysis/data) Dataset

<br />

## [Instacart Market Basket Analysis](https://www.kaggle.com/c/instacart-market-basket-analysis/data) Dataset

- **Aisles:** This file contains different aisles and there are total 134 unique aisles.
- **Departments:** This file contains different departments and there are total 21 unique departments.
- **Orders:** This file contains all the orders made by different users. From below analysis, we can conclude following:
    - There are total 3421083 orders made by total 206209 users.
    - There are three sets of orders: Prior, Train and Test. The distributions of orders in Train and Test sets are similar whereas the distribution of orders in Prior set is different.
    - The total orders per customer ranges from 0 to 100.
    - Based on the plot of 'Orders VS Day of Week' we can map 0 and 1 as Saturday and Sunday respectively based on the assumption that most of the people buy groceries on weekends.
    - Majority of the orders are made during the day time.  
    - Customers order once in a week which is supported by peaks at 7, 14, 21 and 30 in 'Orders VS Days since prior order' graph.
    - Based on the heatmap between 'Day of Week' and 'Hour of Day,' we can say that Saturday afternoons and Sunday mornings are prime time for orders.
    

### Markest Basket Analysis

**Support** : Its the default popularity of an item. In mathematical terms, the support of item A is the ratio of transactions involving A to the total number of transactions.

**Confidence** : Likelihood that customer who bought both A and B. It is the ratio of the number of transactions involving both A and B and the number of transactions involving B.
- Confidence(A => B) = Support(A, B)/Support(B)

**Lift** : Increase in the sale of A when you sell B.
- Lift(A => B) = Confidence(A, B)/Support(B)
      
- Lift (A => B) = 1 means that there is no correlation within the itemset.
- Lift (A => B) > 1 means that there is a positive correlation within the itemset, i.e., products in the itemset, A, and B, are more likely to be bought together.
- Lift (A => B) < 1 means that there is a negative correlation within the itemset, i.e., products in itemset, A, and B, are unlikely to be bought together.
    
**Apriori Algorithm:** Apriori algorithm assumes that any subset of a frequent itemset must be frequent. Its the algorithm behind Market Basket Analysis. Say, a transaction containing {Grapes, Apple, Mango} also contains {Grapes, Mango}. So, according to the principle of Apriori, if {Grapes, Apple, Mango} is frequent, then {Grapes, Mango} must also be frequent.

I utilized apriori algorithm from Mlxtend python library and found out associations from top 100 most frequent products which resulted in 28 product pairs (total 56 rules) that have lift highr than 1. The top 10 product pairs having highest lift are shown below:

| Product A  | Product B | Lift |
| ------------- | ------------- | ---- |
| Limes  | Large Lemons  | 3 |
| Organic Strawberries | Organic Raspberries | 2.21 |
| Organic Avocado | Large Lemon | 2.12 |
| Organic Strawberries | Organic Blueberries | 2.11 |
| Organic Hass Avocado | Organic Raspberries | 2.08 |
| Banana | Organic Fuji Apple | 1.88 |
| Bag of Organic Bananas | Organic Raspberries | 1.83 |
| Organic Hass Avocado | Bag of Organic Bananas | 1.81 |
| Honeycrisp Apple | Banana | 1.77 |
| Organic Avocado | Organic Baby Spinach | 1.70 |

