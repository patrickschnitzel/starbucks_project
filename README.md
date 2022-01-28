# Starbucks Capstone Challenge
Final project of the Udacity Data Scientist Nanodegree

### Table of Contents
todo: adjust
1. [Installation](#installation)
2. [Project Motivation](#motivation)
3. [File Descriptions](#files)
4. [Results](#results)
5. [Licensing, Authors, and Acknowledgements](#licensing)

## Installation <a name="installation"></a>

A basic Anaconda installation and Python 3.X is sufficient.

## Project Motivation<a name="motivation"></a>

One option for the capstone challenge of the Udacity Datascientist Nanodegree is to work with Starbucks customer data. The data set contains simulated data that mimics customer behavior on the Starbucks rewards mobile app during an offer experiment. Once every few days, Starbucks sends out different offers to users of the mobile app. An offer can be merely an advertisement for a drink or an actual offer such as a discount or BOGO (buy one get one free). Some users might not receive any offer during certain weeks. During this time the user reactions and transactions are recorded.

### So what goal are we aiming at?

A data scientist is employed to generate business value. When sending adds there are multiple opportunities doing that.
When creating adds there are costs:
- Creating offers costs money. So an offer with zero response is lost effort
    - None of the offers have zero response. We can compare their effectiveness against eachother though
- Deploying offers can be expensive if the offer have to sent over channels that are not controlled by the company. In this case an example would be deployment via social media
- Giving out rewards costs money. How much exactly e.g. a BOGO offer really costs the company only can be guessed since giving rewards of x$ sale value does cost the company less than x$. So we would have to make assumptions there. 
    - we could try to identify how much an offer increases spending. Therefore however we would need two groups. 

And there are benefits
- Successful offers increase customer spending and therefore company profit

To improve the effects of offers already an understanding how well individual offers are doing can be an enabler to create business value. The marketing department can improve their adds with insights from data. Another option is to target customers better. One way is targeting individual customers using a recommendation engine.

The ultimate recommendaiton engine could recommend the offer that increases profit for an individual customer the most (including sending no offer).
That would mean sending an offer with 
- max(sum_increase_in_spending_ - product_cost - offer_reward - offer_deployment_cost)
Since there is a lot of business understanding and data missing that is not feasible with this dataset. 

However there are other possible beneficial recommendations:
- predict if an offer gets accepted
    - could save offer deployment costs and get feedback to markting team on which type of offer they should focuse
- predict if an offer has a negative effect and not sent 
  - we could try to identify demographic groups with similar behaviour but left out offers

So what we will do:
- get a better understanding of the experiment and the data
- understand how well are different offers are doing by treating the experiment as A/B tests
- implement recommendation engine or classifier that predicts if offers will be successful or not


## File Descriptions <a name="files"></a>
The notbook `Starbucks_capstone_notebook.ipynb.json` contains all relevant code and analysis.
The data set is a simplified version of the real Starbucks app because the underlying simulator only has one product whereas Starbucks actually sells dozens of products.

The data is contained in three files:
- `portfolio.json` - containing offer ids and meta data about each offer (duration, type, etc.)
- `profile.json` - demographic data for each customer
- `transcript.json` - records for transactions, offers received, offers viewed, and offers completed

Here is the schema and explanation of each variable in the files:

`portfolio.json`
- id (string) - offer id
- offer_type (string) - the type of offer ie BOGO, discount, informational
- difficulty (int) - the minimum required to spend to complete an offer
- reward (int) - the reward is given for completing an offer
- duration (int) - time for the offer to be open, in days
- channels (list of strings)

`profile.json`
- age (int) - age of the customer
- became_member_on (int) - the date when customer created an app account
- gender (str) - gender of the customer (note some entries contain 'O' for other rather than M or F)
- id (str) - customer id
- income (float) - customer's income

`transcript.json`
- event (str) - record description (ie transaction, offer received, offer viewed, etc.)
- person (str) - customer id
- time (int) - time in hours since the start of the test. The data begins at time t=0
- value - (dict of strings) - either an offer id or transaction amount depending on the record

## Results<a name="results"></a>
A summary of the results is contained in this medium post: https://medium.com/@patrick.schnizel/starbucks-rewards-randomforest-vs-funksvd-or-just-stack-em-7f05afdfac1e.
A more detailed analysis is contained in the file `Starbucks_capstone_notebook.ipynb.json`

## Licensing, Authors, Acknowledgements<a name="licensing"></a>

Credits to Starbucks and Udacity for the data :)