# Amazon S3
Amazon S3 is an object storage service. In a system, we used Amazon S3 for uploading very large files(>25GB). As our system grew, we have to update our 
S3 upload program to fit the user requirements. We were providing a webpage, from where user could upload files.

## Upload ability upto 2GB
Initially, we have used a plain HTML file using NGINX server. The HTML file has an input field of type file and an upload button. Upon clicking on the upload button, 
we called a lambda endpoint. The Presigned URL was retrieved by the Lambda function and we used the Presigned URL to put the file in S3. The maximum file size to put
a file using the S3 PUT request is 2GB.              
### Cons
- File size is limited to upto 2GB
- Browser stucks some couple of seconds if file size is larger



## Multer
### Pros
- Multipart upload
- Unlimited file size

### Cons
- **Consumes the instances' network resource**. Upload gets superslow when some number of people uploads simultaneously because of the bottleneck of instances maximum upload bandwidth.

We used an Express server to for the frontend and backend. In the backend, we have used `multer-s3` module to put the file(object) to the S3.


## POST request to Presigned URL
### Pros
- Upto 5GB
- 
### Cons
- Upto 5GB
- Browser gets stuck for long time
