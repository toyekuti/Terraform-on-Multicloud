<h1>Terraform-on-Multicloud</h1>

<h2>Description</h2>
Enabling of a MultiCloud architecture deployment through Terraform, with resources running in AWS and Google ﻿Cloud Platform
<br />

<h2>Languages and Cloud Providers Used</h2>

- <b>PowerShell</b> 
- <b>AWS</b>
- <b>Google ﻿Cloud Platform (GCP)</b>

<h2>Environments Used </h2>

- <b>Google Cloud Shell</b>

<h2>Program walk-through on AWS:</h2>
<!-- https://drive.google.com/file/d/1a-xgVDc37bNWsMCYpeZNggLiUL2nQbBN/view?usp=sharing -->
<p align="center">https://drive.google.com/uc?export=view&id=1a-xgVDc37bNWsMCYpeZNggLiUL2nQbBN
Create a programmatic user: <br/>
<img src="https://drive.google.com/file/d/1a-xgVDc37bNWsMCYpeZNggLiUL2nQbBN/view?usp=sharing"/>
<br />
<br />
Search & Select AmazonS3FullAccess: <br/>
<img src="https://i.imgur.com/tcTyMUE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Review & click Create user: <br/>
<img src="https://i.imgur.com/nCIbXbg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
- Click the user created, click <b>Security credentials</b> tab, Scroll down to Access keys section, and Click on <b>Create access key</b>: <br/>
<img src="https://i.imgur.com/cdFHBiU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
- Select <b>Command Line Interface (CLI)</b> and <b>I understand the above recommendation and want to proceed to create an access key</b> checkbox, Click <b>Next</b>, Click on <b>Create access key</b>, Click on <b>Download .csv file</b> and After downloading click on <b>Done</b>:  <br/>
<img src="https://i.imgur.com/JL945Ga.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<h2>Program walk-through on Google Cloud Platform (GCP):</h2>

- **[CLICK HERE to download the hands-on files](https://tcb-public-events.s3.amazonaws.com/icp/mission1.zip)**[.](https://objectstorage.us-ashburn-1.oraclecloud.com/p/mE7kdT1O8UppsI0aV6qxwi8Rfm4YAn3A9rIX6Yv1FxE2Rv6mI1W_RrUs2CBYWxAx/n/idqfa2z2mift/b/eventos-thecloudbootcamp/o/ICP2/mission1.zip)
- Access GCP Console and open Cloud Shell
- Upload **accessKeys.csv** and **mission1.zip** hands-on file to GCP Cloud Shell
- Check if upload has been successfully completed using the command **ls -la**

<p align="center">
Hands-on files preparation: <br/>
<img src="https://i.imgur.com/K71yaM2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br/>
Run the following commands to prepare AWS and GCP environment. Authorize when asked:  <br/>
<img src="https://i.imgur.com/AeZkvFQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br/>
Execute the command below:  <br/>
<img src="https://i.imgur.com/AeZkvFQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Enable the Container Registry API, Kubernetes Engine API and the Cloud SQL API:  <br/>
<img src="https://i.imgur.com/AeZkvFQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

**IMPORTANT (DO NOT SKIP):**
- **Before executing the Terraform commands, open the Google Editor and update the file tcb_aws_storage.tf replacing the bucket name with an unique name (AWS requires unique bucket names).**
    - Open the **tcb_aws_storage.tf** using Google Editor
    - On **line 4** of the file **tcb_aws_storage.tf**:
        - Replace **xxxx** with your name initials, using **5 letters** plus **5 random numbers**:
        Example: **luxxy-covid-testing-system-pdf-en-jerod29292**
</p>

<p align="center">
Run the following commands to finish provision infrastructure steps:  <br/>
<img src="https://i.imgur.com/AeZkvFQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

**Attention**: The Cloud SQL database may take **15 to 25 minutes** to create, always check the **CloudShell** and click **Reconnect** when the session expires (the session expires after **5 minutes** of inactivity by default)

<p align="center">
The warning message at the end of terraform apply command execution is not a problem, please go ahead:  <br/>
<img src="https://i.imgur.com/AeZkvFQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<h2>SQL Network Configuration:</h2>

- Once the Cloud SQL instance is provisioned, access the Cloud SQL service
- Click on your Cloud SQL instance.
- On the left side, under Primary Instance, click on **Connections**.
- Go to **Networking** tab.
- Under **Instance IP assignment**, select Private IP to enable.
    - Under **Associated networking**, select "Default"
    - Click **Set up Connection**
    - Click on **Enable API**, to enable Service Networking API (if asked).
    - Select **Use an automatically allocated IP range in your network**.
    - Click **Continue**
    - Click **Create Connection** and **wait a minutes until conclude.** You will see the message: “*Private services access connection for network default
     has been successfully created.”*
- Under **Authorized Networks**, click "Add Network".
- Under **New Network**, enter the following information:
    - **Name:** Public Access (For testing purposes only)
    - **Network**: 0.0.0.0/0
    - Click **Done**.
    - Click **Save** and wait to finish the update.
    This update may take from **10 to 20 minutes** to finish

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
