# 📦 AWS Lambda OpenSearch Integration Project

This project is part of a school assignment to demonstrate a complete AWS serverless pipeline using multiple AWS services. The solution includes:

- **Three AWS Lambda functions**:
  - One function uploads a PDF file to S3.
  - Another function indexes the uploaded file into OpenSearch.
  - A third function reads from OpenSearch and returns the results to the user.
- **S3** for storing uploaded files.
- **Amazon OpenSearch Service** for indexing and querying documents.
- **API Gateway** to trigger the Lambda function that reads from OpenSearch.
- **AWS CodeBuild** to automatically build and deploy the project using code pushed to GitHub.
- **AWS SAM (Serverless Application Model)** to manage deployment.
- **IAM roles and permissions** for secure access between services.

---

## 🔧 Technologies Used

- **AWS Lambda**
- **Amazon S3**
- **Amazon OpenSearch Service**
- **Amazon API Gateway**
- **AWS CodeBuild**
- **AWS SAM CLI**
- **GitHub**
- **IAM (for security and roles)**

---

## 📁 Project Structure
```
.
├── aws_auth.zip
├── PDFtoTXT.zip
├── pypdf.zip
├── README.md
├── Search_Engine_Deployment-v1.pdf
├── Search_Function.zip
├── Search_Gateway.zip
├── testfiles.zip
└── Upload_to_search.zip
```
---

## 🚀 Deployment Workflow

1. **Push code to GitHub**
   - Triggers CodeBuild via webhook

2. **CodeBuild** runs the `buildspec.yml` script:
   - Installs dependencies
   - Builds the SAM application
   - Deploys the CloudFormation stack
   - Creates/updates all Lambda functions and resources

3. **Testing the Flow**
   - Upload a PDF → S3
   - Index to OpenSearch via Lambda
   - Query OpenSearch via API Gateway endpoint

---

## 📦 How to Use (Locally)

1. Clone the repo:
   ```bash
   git clone https://github.com/your-org/your-repo.git
   cd your-repo

deploy Manual (optional, not required)
```
sam build
sam deploy --guided
```

🔐 IAM and Security Notes
An IAM user with programmatic access is used to authenticate GitHub with AWS.

The IAM user has limited permissions to:

```
Deploy Lambda functions

Access S3

Interact with OpenSearch

Deploy CloudFormation stacks

```
