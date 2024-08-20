# Readme v1.0

## Predicting Radiology Prioritisation and Protocols Using Natural Language Processing and Machine Learning

Author: Stephen Lyen\
Date: 18 August 2024

Dissertation for MSc in Computer Science\

## Contents
1. [Submitted Files](#submitted-files)
2. [Download Files](#downloadable-files)
3. [Dependencies](#dependencies)
4. [Models and Testing](#models-and-testing)
5. [Data](#data)
6. [Python Notebooks](#python-notebooks) 

## Submitted Files (Engage)

Summarised list and brief description of the files submitted on Engage. All of these files are also available on github: <link>

* Python Notebooks\
Details in subsequent Python Notebooks section. 
    1. DataProcessing.ipynb
    2. DataAugmentation.ipynb
    3. UrgencyBert.ipynb
    4. UrgencyRoberta.ipynb
    5. ProtocolBert.ipynb
    6. ProtocolRoberta.ipynb
    7. ProtocolBert-CNN.ipynb
    8. ProtocolRoberta-CNN.ipynb
    9. SVM.ipynb
    10. ModelTester.ipynb

* Sample.csv
This ia sample dataset file, as the original datasets exceed Engage Bath upload limits. This is not intended to be run with the provided notebooks. Please see [Downloadable Files](#downloadable-files) section for link to full datasets.

* Readme file

### Dependencies

* All code was run on Google Colaboratory using Python 3.10.12. 
* External pre-trained RoBERTa library provided in download link folder as above, otherwise all models and libraries are readily available.

## --PLEASE READ BEFORE RUNNING CODE--
### Download files

Full anonymised datasets, study models and pre-trained RoBERTa model are available for download from Google Drive: <[link](https://drive.google.com/drive/folders/1paH5A-5rxyYVgU4DYup3hVsgQ9mp5HDM?usp=sharing)>

1. Models
2. Data
3. RoBERTa-base-PM-M3-Voc-distill-align-hf

**IMPORTANT:** In order for code to run please save these folders in the same location as the .ipynb files. 

RoBERTa-base-PM-M3-Voc-distill-align-hf contains the pre-trained RoBERTa model, downloaded from github under a Creative Commons License NonCommercial 4.0 (Lewis et al. 2020, link: <https://github.com/facebookresearch/bio-lm>). Please see manuscript Methods 3.7.1 for description and reference. 

As the study was performed using Google Colaboratory, the data has been temporarily retained on Google Drive to keep the number of external data storage locations to a minimum, and to facilitate future research.

### Models and Testing

* File list:
1. urgency_bert.pth
2. urgency_roberta.pth
3. urgency_bert_cnn.pth
4. urgency_roberta_cnn.pth
5. protocol_bert.pth
6. protocol_roberta.pth
7. protocol_bert_cnn.pth
8. protocol_roberta_cnn.pth 

Due to Engage upload limits, this folder is available for download, link in the [Downloadable Files](#downloadable-files) section.

<u>**Before Running Code:**</u> please copy the Models folder to the same location as the .ipynb files. 

This folder contains all of the final fine-tuned pytorch models that obtained the best performance metrics.

The file name formats are task_modeltype_cnn. Tasks are urgency or protocol classification and the model types are RoBERTa or BERT. For example, urgency_roberta_cnn.pth is the RoBERTa-CNN model applied to urgency classification.

A ModelTester notebook has been provided for transformer and transformer-CNN models.
To run this, there is a cell labelled **'Set Parameters'** following the imports and function declarations where the user can specify parameters.

* set_label : 'Protocol' or 'UrgBin'
* set_cnn: True will apply transformer-CNN, False will apply transformer only
* set_model: 'roberta' or 'bert'
* dir_path: Please replace with the file path to the submission folder

### Data

File list:
* Non-augmented
1. Xtrain_70-30_no-aug.csv
2. Xtest_70-30_no-aug.csv
3. ytrain_70-30_no-aug.csv
4. ytest_70-30_no-aug.csv
* Augmented
5. Xtrain_aug_1000-400.csv
6. Xtest_aug_1000-400.csv
7. ytrain_aug_1000-400.csv
8. ytest_aug_1000-400.csv

* Misc
9. nlp_languages.csv
10. SampleRaw.xlsm

Download link for the Data folder is provided in the [Downloadable Files](#downloadable-files) section.

<u>**Before Running Code:**</u> please copy Data folder to the folder containing the .ipynb files.

This folder contains the full datasets for this project. These are divided into Xtrain, Xtest, ytrain, and ytest .csv files. These are either non-augmented (labelled no-aug), or augmented with threshold-number.

For simplicity, only the optimal augmentation level has been provided, i.e. 1000-400 which is 400 cases below 1000 threshold. Please see manuscript Methods 3.6 for details.

nlp_languages.csv contains a further list of language codes for the nlpaug backtranslation functions.


## Python Notebooks

### DataProcessing.ipynb

Cleans the pre-anonymised data and extracts data from the semi-structured 'Comment' column. Full details of the different datatypes are in the manuscript Methods section 3.5.

Note that the full raw data input for this notebook has not been provided, only an example spreadsheet containing 100 cases labelled SampleRaw.xlsm. The full dataset is available upon request.

<u>**Before Running Code:**</u> Replace file_path with the path to folder containing dataset file.
If using sample data, set_sample = True.


### DataAugmentation.ipynb

Augments the training dataset generated from DataProcessing.ipynb. 

This notebook was executed in two sections due to GPU memory constraints, although depending on the user's GPU this may not apply. If necessary, please restart kernel and run section 2.

<u>**Before Running Code:**</u> Replace file_path with the path to folder containing dataset file.
If using sample data, set_sample = True.


### Transformer and Transformer-CNN Notebooks
* File List
1. UrgencyRoberta.ipynb
2. UrgencyBert.ipynb
3. ProtocolRoberta.ipynb
4. ProtocolBert.ipynb
5. ProtocolRoberta-CNN.ipynb
6. ProtocolBert-CNN.ipynb

Notebooks used to train, validate and test models.
The file name formats are task-model, e.g. UrgencyRoberta-CNN would be the urgency classification task using the RoBERTa-CNN model.

<u>**Before Running Code:**</u> Replace dir_path with the path to folder containing dataset file.

Load Dataset and Parameters Section:\
set_aug = True to load augmented data, False non-augmented.\
Note this has already been done for ProtocolRoberta-CNN and ProtocolBert-CNN notebooks.

### SVM Notebook

<u>**Before Running Code:**</u> Replace dir_path with the path to folder containing dataset file.

Load Dataset and Parameters Section:\
set_aug = True to load augmented data, False non-augmented.\
set_label = 'Protocol' or 'UrgBin'


## Contact

Stephen Lyen\
email: smmtl20@bath.ac.uk
