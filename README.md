# E-learner Segmentation

### Business Case: Scaler - Clustering

#### Problem Statement:

Scaler is an online tech-versity offering intensive computer science & Data Science courses through live classes delivered by tech leaders and subject matter experts. The meticulously structured program enhances the skills of software professionals by offering a modern curriculum with exposure to the latest technologies. It is a product by InterviewBit.

You are working as a data scientist with the analytics vertical of Scaler, focused on profiling the best companies and job positions to work for from the Scaler database. You are provided with the information for a segment of learners and tasked to cluster them on the basis of their job profile, company, and other features. Ideally, these clusters should have similar characteristics.

#### Solution: EDA | ML model building

Scaler is an online tech-versity offering intensive computer science & Data Science courses through live classes delivered by tech leaders and subject matter experts. The meticulously structured program enhances the skills of software professionals by offering a modern curriculum with exposure to the latest technologies. It is a product by InterviewBit.

As per the business problem, Scaler wants the data science team to cluster the information for a segment of learners on the basis of their job profile, company, and other features.

It was a simple data frame which had sufficient features corresponding to each student who has past work experience. There were multiple entries for few students due to history of working in more than one company or multiple CTC updation entries in one company. Duplicate values were dropped, missing values were imputed and outliers were removed.

With the help of given data, I performed EDA, manual, hierarchical and K means clustering. 

1. The data set had features like company, ctc, joining_year, job_position etc. CTC was the only continuous feature. It had an extremely right tailed distribution with a mean of around 22 lakhs and median of around 9.5 lakhs. This shows that there were outliers which were affecting the mean. After treating those outliers with IQR method, I found the mean to be around 10 lakhs. Hence, each and every learner who is aiming for placements will expect a salary of at least more than 12 Lpa. 
2. Most of the learners have experiences under 10 years with 1 and 2 years topping the list. There are also significant number of students with under 1 year of experience. Hence our training and teaching need to be good enough so that these learners can crack higher packages. Also, most of the learners are recent joiners (2016-2019). 
3. All most all the top 10 job positions are either related to software field or Data Science field. Hence, we can expect most of them to get decent packages as they already have experience in the relevant field. 
4. After EDA, I I started with preparing my data set for manual clustering. I grouped Company, Job Position, Years of Experience features and aggregated the CTC to new features which had the 5 point summary (mean, median, max, min, count). Flags were created based on these aggregations.
5. All the questions related to manual clustering have been answered in the jupyter notebook.
6. Kmeans is a distance based unsupervised clustering algorithm. There were so many categories in company and job position features. Target encoding is not possible and OHE also cannot be done due to curse of dimensionality. I had to drop those features. Rest of the features were standard scaled. 
7. Not much pattern was observed. It was very difficult to get the number of clusters just by visualisation without hue. Hence, elbow method was used. I found 5 clusters to be best using DB_score. But, after rigorously plotting again with different clusters, I dropped 1 value and found 4 clusters to be the best. 
8. Hierarchical clustering algorithm was also used to cluster. To get the dendrogram plot accurately, I initially trained a model using SciPy with just 100 points and found that 2 and 4 number of clusters can be taken. Due to limitations in my hardware, I had to run the agglomerative clustering algorithm from scikit-learn only on a random sample of 30000 data points. Here after rigorously plotting with different clusters, I found that this algorithm was clearing able to distinguish the data points with 2 clusters.
9. The interpretation of the clusters for both these algorithms has been clearly written on the jupyter notebook.

To whoever reads this, I hope my insights and recommendations from this case study were meaningful.

Thank you,

Krishna
