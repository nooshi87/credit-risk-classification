# credit-risk-classification

##Purpose of analysis:
- Create a regression model that could most accurately predict whether a loan that was granted was in the "high-risk" loan category or the "healthy" loan category.
- The inputs to create the regrssio model included features like the borrower's income, total debt, debt to income ratio, number of financial accounts, loan size (assuming it is the amount the borrower requested), and derogatory marks. Based on these inputs, the lending instances was placed in two categorys - healthy or high risk loans.
- We were trying to create a model that could categorize loans granted based on data available for instances labeled as 0 (healthy loan) and 1 (high-risk loans). The dataset we were provided had 18765 healthy loans and 619 high risk loans. 
- The first part of the analysis used the raw, original dataset. When the classification report for this model was generated, it was seen that healthy-loan predictions were supported by almost 30xs more instances/data. The original regression model was 100% accurate in predicting '0' instances, but was only 88% accurate in predicting '1' cases. 
- We then used the RandomOverSampler module from the imbalanced-learn library to randomly over sample from the existing high-risk data to strengthen the model predictions for labels in the '1' category.


## Results

Using bulleted lists, describe the balanced accuracy scores and the precision and recall scores of all machine learning models.

* Machine Learning Model 1:
  * Using original data split 80:20 to create a regression model (train data, 80%) and test data based on model (remaining 20% of the data) 
    - Balanced Accuracy:99.2%
    - Precision '0':1.00
    - Precision '1':0.85
    - Recall '0':0.99
    - Recall '1':0.91


* Machine Learning Model 2:
  * Same 80:20 data split from previous regresson model was used. However, model 2 over-sampled data to balance presence of '1' cases in the training dataset and generated a regression model accordingly. 
    - Balanced Accuracy:99.4%
    - Precision '0':1.00
    - Precision '1':0.84
    - Recall '0':0.99
    - Recall '1':0.99
    - 

## Summary

* Model 2 performs the best in overall accuracy. Model 1 is better in predicting false positives (precision for '1' is slightly higher). Model 2 is better for predicting false negatives (recall for '1' is higher). 

In order to suggest a model with full confidence,  I would need to be clear on what the categorization of loans would be used for. Is the lender concerned they will not get re-payment back from the high-risk borrowers and need to send more frequent reminders or increase interest rates as a penalty? If so, then model 2 would be better as there is less of a chance of high-risk loans being categorized as healthy.  However, if lenders want to use this information to reward healthy loan borrowers upon re-payment (or are more concerned about identifying healthy-loan borrowers for any purpose) - then model 1 should be used. The number of false positives (from the confusion matrices) indicate that more health-loan borrowers would be mis-flagged as high-risk with model 2. 

Based on the information I have, I would suggest using model 2 since the accuracy is for '1' is 91% as opposed to 88% from model 1. Accuracy for '0' is 100% for both models. Also, identifying high credit risk borrowers (avoiding false negatives) is likely to be more cruicial in real-world scenarios. 
