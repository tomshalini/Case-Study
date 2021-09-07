# Case Study

## Task1
Imagine that you were asked to use this dataset to build a classification model, with  `gender`  as the target. Look at the information we have given you and identify 3-5 potential problems you can see with the provided dataset that might make building a classification model difficult.
### Solution:
1.  **Imbalanced dataset**
     From the summary metrics, it can be seen that number of males are more than doubled the number of females.
2. **Missing Values**
    There are around 60% missing values in device_name feature.
3. **Non numeric datatype**
    There are categorical data present in dataset. Based on model selection, we might need to handle categorical data using one-hot encoding.
4. **Non featured Columns**
Assuming there are multiple app_id corresponding to each app_category otherwise these two features are redundant information in dataset. Combined value of User_id, app_id and device_name can be used as unique id but not required for the model. (device_name can be maximum of number of rows in dataset which can not be handled using one hot encoding to feed it to the network).

## Task2
Describe briefly how you would find the features that are likely to be the most important for your model.
### Solution:
* Using **correlation matrix**
* From domain knowledge, device_name needs not be considered as a feature because of missing values and random names. If required to use it as a feature, one-hot encoding is not feasible option rather needs to use some fixed length embeddings.

## Task3
Identify which model you would try first, and at least one advantage and disadvantage of this choice.
### Solution:
**Weighted XGBoost classifier**
#### Advantage
1. Can be used for feature selection (feature importance can be found out).
2. Model performance is good (for imbalanced dataset as well).
3. Less feature engineering is required.


#### Disadvantage
1. Large number of hyperparameters to be tuned. Most importantly finding the right value of **scale_pos_weight** hyperparameter which is used to handle imbalanced classification problem.
2. Overfitting possible if parameters are not pruned properly.


## Additional Points
1. Accuracy alone is not a good measure for imbalanced dataset. Rather use precision, recall, and f1 score.
2. Can try resampling using **SMOTE** (Synthetic Minority Oversampling Technique).
3. Use Stratified cross validation. 
