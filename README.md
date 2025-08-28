# WhatsApp Automation & Messaging Behaviour Analysis  

## 1. Overview  
- This project combines end-to-end WhatsApp automation, built using the `pywhatkit` library, with large-scale data analysis of more than **420,000 logged messages**.  

- On the automation side, the system was designed in a clean, modular way using Python functions and a menu-driven `match-case` control flow. It is capable of instantly sending messages and images, scheduling messages with a wait-time, sending messages to groups, looping through multiple messages, and even deleting log files.  

- On the analysis side, over **420k records** were processed across four attributes. The raw log data was cleaned, transformed, and validated into an analytics-ready format. Exploratory Data Analysis (EDA) was then carried out using **Seaborn** and **Matplotlib** to identify the most frequently used messages, daily activity patterns, and the most contacted receivers.  

- This project demonstrates both automation engineering and data storytelling — two of the most in-demand skills for internships and entry-level data roles.  



## 2. Objectives  
The primary goals of this project were:  
- To automate WhatsApp communication with minimal manual effort.  
- To log all automated actions into a structured CSV file for future analysis.  
- To clean and transform raw logs, of which around **20% were malformed rows**, into a clean dataset.  
- To analyse communication patterns with respect to frequency of messages, time of day, and most frequent receivers.  
- To demonstrate a scalable, end-to-end pipeline combining automation and analytics.  



## 3. Methodology  

### 3.1 Automation Development  
The automation component was implemented using the **pywhatkit** library. Separate functions were written for each major task including sending instant messages, scheduling messages with a delay, sending group messages, sending images with captions, looping through multiple messages, and deleting logs.  
These functions were integrated into a **menu-driven CLI application**, allowing the user to choose from different options interactively.  

### 3.2 Data Processing  
The final dataset contained **420,000 rows and 4 columns**. Initially, the schema was unstructured, with timestamps stored as plain text and receiver identifiers stored as integers. After cleaning, the schema was normalised to consistent datatypes and prepared for analysis.  

**Schema before cleaning**  

| Column    | Dtype   |  
|-----------|---------|  
| timestamp | object  |  
| receiver  | int64   |  
| status    | object  |  
| message   | object  |  

**Schema after cleaning and transformation**  

| Column    | Dtype             |  
|-----------|------------------|  
| timestamp | datetime64[ns]   |  
| receiver  | string[python]   |  
| status    | string[python]   |  
| message   | string[python]   |  

A null values check confirmed that no missing data remained in the cleaned dataset:  

| Column    | Null Count |  
|-----------|------------|  
| timestamp | 0          |  
| receiver  | 0          |  
| status    | 0          |  
| message   | 0          |  

In summary, timestamps were normalised to the format `DD-MM-YYYY HH:MM` and converted into Pandas datetime objects, receiver IDs were converted into strings, categorical columns such as `status` and `message` were cast to string datatypes, and roughly 20% of malformed or invalid rows were removed.  



## 4. Execution  
(Make sure to run this program as an Administrator and pre-login whatapp web in browser)
When the automation script is executed, the user is presented with the following interactive menu:  

Choose an option:

Instantly message

Waittime Message

Instantly Send Image

Group Waittime Message

Multiple Messages



## 5. Visualisation  

Exploratory Data Analysis (EDA) was performed on the **420k+ cleaned records**.  

### 5.1 Message Frequency Distribution  
- Most frequently used messages: **hi, hello, okay, thanks, bye, sure**  
- These top 6 account for the majority of all interactions.  
- Rare outliers: **gooo_luck, congrats, need_help, enjow**  
![Message Frequency Distribution](link_to_message_frequency_plot)  

### 5.2 Time-Based Activity Patterns  
- Aggregated message counts by hour of day.  
- Found low activity at **10 AM** and **11 PM**.  
- **Afternoons** showed peak activity, suggesting higher engagement.  
![Time-Based Activity Patterns](link_to_time_activity_plot)  

### 5.3 Receiver Analysis: Most Contacted Numbers  
- Identified top receivers across the dataset.  
- Top contacts appeared **5–4 times** each; majority were contacted fewer times.  
**Sample Top Receivers**: `917794046348 (5), 919190383400 (5), 917657717128 (5), 916866469732 (4), 919541675598 (4)`  
![Top Receivers](link_to_top_receivers_plot)  


## 6. Key Insights  
- Automation successfully streamlined WhatsApp communication into a structured data pipeline.  
- 420k+ records processed into a fully clean, schema-consistent dataset.  
- No nulls after cleaning → 100% reliable logs.  
- Message trends show reliance on short, repetitive conversational tokens.  
- Time patterns highlight afternoon as peak messaging hours, with dips at late morning and late night.  
- Receiver frequency analysis shows limited but repeated contacts dominating the logs.  



## 7. Impact  
- Demonstrated ability to integrate automation and analytics in a single project.  
- Scaled pipeline to handle **>400k records** with 0 missing values.  
- Optimised log structure for real-time monitoring and post-hoc EDA.  
- Built reproducible workflow useful for **internship-level automation, data wrangling, and analytics tasks**.  



## 8. Tech Stack  
- Python (3.10+)  
- pywhatkit (automation)  
- Pandas, NumPy (data wrangling)  
- Matplotlib, Seaborn (visualisation)  




















