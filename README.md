<h1>Predicting a Startup’s Acquisition Status</h1>

The dataset is all about the Startup’s Financial Information and we need to predict the current 
financial status of the company. The dataset is of Crunchbase - 2013, database, company, investors and all the other details 
belongs to the company. In this project, we analyzed the company’s status i.e., Operating, Acquired, IPO or Closed.

<h2>Understand the dataset</h2>

- Dataset Link: https://drive.google.com/file/d/17bfNyMgP-PofCkdlvnLHxxFqV8mdDo-9/view
- The dataset is completely based on the company’s information from company’s 
website database of 2013.
- Features: All the columns with the company’s information like name, permalink, 
category, funding dates, funding rounds, funding amount, city, state, founding dates, 
last milestone dates and many more.
- Target Variable: Status

<br>

 <h2>Data Cleaning</h2>
 
- We deleted columns with redundancy, granularity and irrelevant information we also deleted instances with missing values for specific columns basically we removed null values for the following columns status, country _code, category_code, founded_at. For the columns with less percentage of null values with used the Imputing method using mean , median and mode.

<br>

<h2>Data Transformation</h2>

- Here we are fixing irrelevant data types to some columns  so we converted columns that include date year datatype.

- Then we started filling the null values in closed_at for calculation of the age of company then we created column active_days from subtracting closed_at from founded_at then we removed rows with negative values in active_days and dropped the other two columns

- Then we removed outliers using IQR method then we generalized category_code and country_code using One hot encoder to prepare for feature engineering through working on our targeted variable Status and we finalized the data analysis part with deleting duplicates from dataset.

<br>

<h2> Model Building</h2> 

- We started the ML part through applying Logistic Regression Model ,XGBoost Claasifier Model , Quadratic Discriminant Analysis Model and Random Forest Classifier Model .
But first we had to prepare the data through the following steps:

  1. Splitting the data. We split the data through sklearn ysing test_tain_split function.

  2.	Separating numerical and Categorical columns
  3.	Applying one-hot encoding to the whole dataset
  4.	Scaling the dataset.

- After preparing the data we started created a pipeline for each model and applying it then tuned the parameter using several methods to increase train and test accuracy and we took the best accuracy to be in the pipeline and we saved our data model. Followings are results of implemented models:

  | Models | Default Parameters | Hyperparameter Tuning (GridSearchCV) | Hyperparameter Tuning (RandomizeSearchCV) |
  | :---        |    :----:   |          :---: | ---: |
  | Logisitc Regression Model      | Train accuracy: 87.24% Test accuracy: 86.141%| Train accuracy: 87.254% Test accuracy: 86.102%   | |
  | XGBoost Classifier Model   | Train accuracy: 92.59% Test accuracy: 90.84%        | Train accuracy: 91.63% Test accuracy: 91.22%      | |
  | Quadratic Discriminant Analysis Model   | Train accuracy: 65.24% Test accuracy: 63.43%        | Train accuracy: 84.35% Test accuracy: 83.23%      | |
  | Random Forest Classifier Model   | Train accuracy: 95.76% Test accuracy: 86.96%        | Train accuracy: 91.4% Test accuracy: 91.34%      | Train accuracy: 91.51% Test accuracy: 91.38% |

<br>

<h2> Model Deployment using Django and Heroku:</h2>
<br>

 **App link:** https://team-a-model-deployment-django.herokuapp.com/
