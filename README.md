Supervised Learning- Financial Fraud
Determing fraudulent transactions is a vital component of any business and having appropriate methologies is key to predict fraud. This project aims to create a machine learning algorithm that can provide information for fraudulent cases based on the transaction's specifications. My hypothesis, was the following:


1. DATA

The dataset had approximately 10,000 data points. Given my 8GB computer, i had reduced our data set to 500,000. This would be a good beginning data set for proof of concept.

2. METHOD

Hypotheses:

Null Hypothesis (H0): There is no main effect of type of transaction  on the target variable 'is_Fraud".
Alternative Hypothesis (H1): There is a main effect of type of transaction  on the target variable 'is_Fraud".

The goal was to first clean the data and choose our ideal features. There are a number of general types of models that could be used for predicting fraud.

I utilized:

Train test splits and implement a RandomForestClassifier

After training this initial classifier and viewing its accuracy measures, I moved forward with hyperparameter tuning via RandomizedSearchCV

Upon finding optimal hyperparameters, I re-train our model using these hyperparameters, generate predictions for this new model, and output the subsequent F1 score for this classifier.

3. EDA

EDA Report

We explored the dataset by utilizing describe, head, and columns functions. I then started creating histogram to determine distribution of transaction amounts. I noticed that the fraudulent transactions were a small data set of the overall dataset. 
![image](https://github.com/zenasawaged/TLAB2/assets/75915150/54b6317b-1abf-40a7-bf62-416163abed6d)

Then I conducted a Bivariate analysis with hue - using a mix of scatter plots, bar plots, and box plots. A scatter plot with hue (for numerical variables), which shows there is a correlation of fraudulent cases between new balance of $0 and old balance between $0- $1.5million.
![image](https://github.com/zenasawaged/TLAB2/assets/75915150/0e5095c8-5f85-420f-bc37-dbeba90b8d67)

Then I conducted a Bar plot with hue (for categorical variables) to detemine which amount and type is marked fraud- we can see transfer and cash out are the type marked fraud.
![image](https://github.com/zenasawaged/TLAB2/assets/75915150/deaf123a-5316-42bb-b6ec-cbb8807ecd00)

4. CLEANING

Cleaning Report

We want to make sure the data is clean and usable. That means removing things like missing data-sets and columns that are not necessary. I started by checking for null values and dropping columns that  were not so useful such as "isFlaggedFraud","nameOrig","nameDest" as they did not have a correlation to the target variable 'is_fraud'. This information does not provide a lot of depth to our dataset. We first pre-processed the data by doing the necessary dummy encoding of 'type' by creating a boolean and as random classifier computes integers not non-integers.

<img width="1718" alt="Untitled 2" src="https://github.com/zenasawaged/TLAB2/assets/75915150/f882688b-9438-462c-90d1-6137eccdd745">

We moved on to deeper exploration after this and created a new csv file.

5. MODELING

Pre-Processing Report Modeling Report

I chose to utilize a few different packages in order to perform the Machine Learning modeling. 

# Train and Test I used to measure the accuracy of your model. It is called Train/Test because you split the data set into two sets: a training set and a testing set. 

<img width="1718" alt="Untitled 2" src="https://github.com/zenasawaged/TLAB2/assets/75915150/75f65900-8780-45d5-968b-72fade97158a">


# implement a RandomForestClassifier

Random Forests are particularly well-suited for handling large and complex datasets, dealing with high-dimensional feature spaces, and providing insights into feature importance. This algorithm’s ability to maintain high predictive accuracy while minimizing overfitting makes it a popular choice for financial data.

# hyperparameter tuning via RandomizedSearchCV
We see that the accuracy score of this model with the default values for hyperparameters is about F1 Score: 0.8539325842696629.
<img width="1718" alt="Untitled 4" src="https://github.com/zenasawaged/TLAB2/assets/75915150/77581804-1d15-4c17-aba1-9973a52e1719">

# I re-train our model using these hyperparameters
 As i re-trained by model the f-SCORE reduced to F1 Score: 0.8507462686567163. Here we used a random_state of 42. For a different random state you will get a different training test split, and subsequently different accuracy score.
<img width="1718" alt="Untitled 5" src="https://github.com/zenasawaged/TLAB2/assets/75915150/30212b2c-a993-4838-8add-1e457b0b5dec">

6. CONCLUSION

Our model has an F1 Score of 0.85, which is close to 1 (which means all predictions are correct). Using the harmonic mean in F1 Score, we find a balance of similar values for precision and recall. This informs us that our machine learning model is accurate in deciphering which cases are fraudulent. Gathering more data on fraudulent transactions and more effective grouping algorithms is always a great start. I think that the data set was a great proof of conccept and beginning point but I would love to see the predictors of fradulent cases with real life data. 
