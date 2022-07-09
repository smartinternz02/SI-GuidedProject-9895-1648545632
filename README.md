# Detection-of-phishing-websites-from-urls-using-ibm-watson-studio
There are a number of users who purchase products online and make payments through e-banking. There are e-banking websites that ask users to provide sensitive data such as username, password & credit card details, etc., often for malicious reasons. This type of e-banking website is known as a phishing website. Web service is one of the key communications software services for the Internet. Web phishing is one of many security threats to web services on the Internet. 

##### Common threats of web phishing:

Web phishing aims to steal private information, such as usernames, passwords, and credit card details, by way of impersonating a legitimate entity.

It will lead to information disclosure and property damage.

Large organizations may get trapped in different kinds of scams.

This Guided Project mainly focuses on applying a machine-learning algorithm to detect Phishing websites.

In order to detect and predict e-banking phishing websites, we proposed an intelligent, flexible and effective system that is based on using classification algorithms.  We implemented classification algorithms and techniques to extract the phishing datasets criteria to classify their legitimacy. The e-banking phishing website can be detected based on some important characteristics like URL and domain identity, and security and encryption criteria in the final phishing detection rate. Once a user makes a transaction online when he makes payment through an e-banking website our system will use a data mining algorithm to detect whether the e-banking website is a phishing website or not.
<a ><img src="https://lh4.googleusercontent.com/oohEvy6ZvTTr7oKH1fL_lPeOkdiDQJbtEWcxIe4_CnFcjj5jnFB3tib6sN627fFztSzTSAVjvepuUVNYQo4913L0IVN_VCz7ItxnlJWtURhtg8xan8wTBT8GxMJ3iN1yquYJTi1R" /></a>

 ###### Detecting phishing website using machine learning

Phishing is a type of attack where an attacker tricks the victim to give up sensitive information such as login credentials by disguising as a trustworthy entity. In this application we will try to detect a phishing website using the features that differentiates these domains from the legitimate ones. We will create our own dataset, train and test various machine learning models using Jupyter Notebooks on IBM Watson studio and deploy the best model to be used by the application for detection.

Various features that are used to create the dataset are as follows : 
1. Using IP Address - check if URL has an ip address in it
1. HTTPS - checking the existance of 'https', trusted certificate authority and age of certificate
1. URL Short - check if url has been shortened
1. Having @ symbol - it leads the browser to ignore everything preceding the '@' symbol
1. Having double-slash - means that the user will be redirected (http://www.legitimate.com//http://www.phishing.com)
1. Domain registration Length - Trustworthy domains are regularly paid for several years
1. favicon - favicon loaded from the domain or not
1. Existance of https token in the domain part of the URL
1. Request URL - examines  whether  the  external  objects  contained  within  a  webpage are loaded from another domain
1. URL of Anchor - If the <a> tags and the website have different domain names
1. Links in tags - It is expected that tags (Meta, Script and Link) are linked to the same domain of the webpage.
1. Server Form Handler - If it is blank or contains any other domain name
1. Submitting information to email
1. Abnormal URL - if domain name (from whois) not in url
1. redirect count
1. invisible iframe
1. Age of domain 
1. web traffic - google rank for page
1. statistical report - match it with top 10 domains and top 10 IPs from PhishTank

  
## Getting started 

1. Sign up for an [IBM Cloud account](https://console.bluemix.net/registration/)
1. Login to the [IBM Watson Studio](https://www.ibm.com/cloud/watson-studio)
1. Install Python3.7
1. Install dependencies
```
pip install -r packages.txt
```

## Creating Dataset

The dataset created for this application uses around 250 legitimate and 250 phishing urls with 20 features each as mentioned above. You can add more data and features (feature_extraction.py) to the project to create your own dataset as shown below. 

The URLs for phishing websites was retrieved from [here](https://www.phishtank.com/developer_info.php) (verified_online.csv) and
The URLs for legitimate websites was retrieved from [here](http://s3.amazonaws.com/alexa-static/top-1m.csv.zip) (top1m.csv)

1. Create the dataset for the phishing websites

python create_dataset.py <file_with_phishing_url> <number_of_urls_to_use> <output_file> <target_value>

```
python create_dataset.py verified_online.csv 500 dataset2.csv 1
```
1. Create the dataset for the legitimate websites

python create_dataset.py <file_with_legitimate_url> <number_of_urls_to_use> <output_file> <target_value>

```
python create_dataset.py top1m.csv 500 dataset2.csv 0
```

## Preprocess the data, build machine learning models and test them

### 1. Sign up for Watson Studio

Sign up for IBM's [Watson Studio](https://dataplatform.ibm.com/).

### 2. Create a new Project

> Note: By creating a project in Watson Studio a free tier `Object Storage` service will be created in your IBM Cloud account. Take note of your service names as you will need to select them in the following steps.

* On Watson Studio's Welcome Page select `New Project`.

* Choose the `Data Science` option and click `Create Project`.

* Name your project, select the Cloud Object Storage service instance and click `Create`


### 3. Upload the dataset

* Drag and drop the dataset (`csv`) file you just created to Watson Studio's dashboard to upload it to Cloud Object Storage.

### 4. Import notebook to Watson Studio

* Create a **New Notebook**.

* Import the notebook found in this repository

* Give a name to the notebook and select a `Python 3.5` runtime environment, then click `Create`.


### 5. Import dataset into the notebook

To make the dataset available in the notebook, we need to refer to where it lives. Watson Studio automatically generates a connection to your Cloud Object Storage instance and gives access to your data.

* Go to the Files section to the right of the notebook and click `Insert to code` for the data you have uploaded. Choose `Insert pandas DataFrame`.

### 6. Follow the steps in the notebook

The steps should allow you to understand the dataset, analyze and visualize it. You will then go through the preprocessing and feature engineering processes to make the data suitable for modeling. Finally, you will build some machine learning models and test them to compare their performances.

### 7. Deploy the best model on IBM Cloud

1. Navigate to your project and add a new machine learning model.
1. Give it a name, choose a machine learning service, select model builder as model type as logistic regression is one of the best model for our dataset and is available in the builder, select the default runtime and select Manual.
1. Add the reduced dataset to the model.
1. Add a deployment
1. Get the deployment url and the machine learning model instance tokens.
1. Replace the deployment url and tokens in the check_url.py file

## Test a URL

```
python check_url.py <url>
```

## REFERNCES

https://www.researchgate.net/publication/277476345_Phishing_Websites_Features









