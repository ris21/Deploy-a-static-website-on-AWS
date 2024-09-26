Static Website Hosting on AWS S3

This project demonstrates how to host a static website on Amazon S3. By following the steps outlined below, I was able to create an S3 bucket, configure static website hosting, secured my bucket using IAM policies, uploaded my website files, and accessed my website via the S3 endpoint.

Project Overview
Objective: Host a static website on AWS S3.
Technologies Used: Amazon S3, IAM policies.
Steps Involved:
Creating an S3 bucket
Enabling static website hosting
Securing the S3 bucket with IAM policies
Uploading web files to the bucket
Testing the website endpoint
Step 1: Creating the S3 Bucket
Sign in to the AWS Management Console and navigate to the Amazon S3 Console.
Click on Create bucket.
Enter a unique name for your bucket and choose your preferred AWS region.
Under Block Public Access settings for this bucket, uncheck Block all public access and accept the acknowledgment.
Under Bucket Versioning, select Disable.
(Optional) Add tags for easy identification.
Under Default encryption, disable server-side encryption.
Click Create bucket.
Step 2: Enabling Static Website Hosting
In the S3 console, go to your newly created bucket and click the Properties tab.
Scroll down to the Static website hosting section.
Enable static website hosting and select Host a static website.
For the Index document, enter index.html (or the name of your main webpage).
Click Save Changes.
Note the Endpoint URL under the static website hosting section. This will be the public URL of your website.
Step 3: Securing the S3 Bucket with IAM Policies
To secure your bucket and allow public read-only access, follow these steps:

In the S3 console, select your website bucket and navigate to the Permissions tab.
Under Bucket Policy, click Edit.
Add the following bucket policy to grant public read access:
json
Copy code
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": [
                "s3:GetObject"
            ],
            "Resource": [
                "arn:aws:s3:::your-bucket-name/*"
            ]
        }
    ]
}
Replace your-bucket-name with the name of your bucket.
Click Save changes.
Step 4: Uploading Web Files to the S3 Bucket
In the S3 console, go to your bucket and click the Objects tab.
Click the Upload button.
Click Add files to upload your website files, or Add folder to upload your website folder.
Once uploaded, your static site files will be stored in the bucket.
Step 5: Testing Your Website
Go to the Properties tab of your bucket.
Scroll down to the Static website hosting section.
Click the Endpoint URL link to open your hosted website.
