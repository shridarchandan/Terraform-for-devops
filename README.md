# Terraform-for-devops
This project provides a comprehensive Terraform configuration to manage infrastructure on AWS, leveraging reusable modules and best practices. It provisions resources such as EC2 instances, S3 buckets, and DynamoDB tables, enabling a full-stack AWS environment setup.

## Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Folder Structure and File Details](#folder-structure-and-file-details)
- [Prerequisites](#prerequisites)
- [Setup and Usage](#setup-and-usage)
  - [Step 1: Clone the Repository](#step-1-clone-the-repository)
  - [Step 2: Configure AWS Credentials](#step-2-configure-aws-credentials)
  - [Step 3: Initialize Terraform](#step-3-initialize-terraform)
  - [Step 4: Customize Variables](#step-4-customize-variables)
  - [Step 5: Execute Terraform Commands](#step-5-execute-terraform-commands)
  - [Step 6: Destroy Resources](#step-6-destroy-resources)
- [Outputs](#outputs)

## Overview

This project is designed to automate the creation and management of AWS resources using Terraform. It organizes configurations into multiple files, each dedicated to specific resources or aspects of infrastructure, making the code modular and easy to understand.

## Features

- **Automated AWS Resource Provisioning**: EC2 instances, S3 buckets, and DynamoDB tables.
- **Modular Code Structure**: Organizes resources into separate files for clarity and maintainability.
- **Reusability**: Define variables to make the configurations reusable across environments.

## Folder Structure and File Details

```plaintext
terraform-for-devops-main/
├── dynamodb.tf          # Defines DynamoDB resources
├── ec2.tf               # Configures EC2 instances and their settings
├── s3.tf                # Manages S3 bucket configurations
├── terraform.tf         # Main configuration file, sets up the provider
├── variables.tf         # Declares variables used across the project
├── outputs.tf           # Specifies output values to access resource information
└── aws_module_project/  # Submodule for additional infrastructure
    ├── backend_infra.tf # Configures backend infrastructure like VPC, subnets, etc.
    ├── main.tf          # Main entry point for the module's resources
    └── providers.tf     # Sets up providers for the module
```

### Prerequisites

To run this project, ensure you have the following tools installed and configured:

- **Terraform** (version >= 0.12): [Download Terraform](https://www.terraform.io/downloads.html).
- **AWS CLI**: Install and configure with AWS IAM credentials.
- **AWS Account**: Ensure your IAM user has the necessary permissions to create resources in AWS.

### Setup and Usage

Follow these steps to set up and execute the Terraform configurations for this project.

#### Step 1: Clone the Repository

Clone this repository to your local machine:

```bash
git clone https://github.com/your-username/terraform-for-devops.git
cd terraform-for-devops-main
```

#### Step 2: Configure AWS Credentials
Set up AWS credentials using the AWS CLI, or export the credentials directly:

```bash
aws configure
# or
export AWS_ACCESS_KEY_ID="your_access_key"
export AWS_SECRET_ACCESS_KEY="your_secret_key"
```

#### Step 3: Initialize Terraform
Initialize the Terraform project to download the required provider plugins and prepare the environment:

```bash
terraform init
```

#### Step 4: Customize Variables
Edit variables.tf to adjust resource-specific values like instance type, region, or bucket names:

```bash
hcl
# Example: Change instance type
variable "instance_type" {
  description = "The type of instance to use"
  default     = "t2.micro"
}
```

#### Step 5: Execute Terraform Commands
1. Plan: Run the terraform plan command to preview the resources that Terraform will create.

```bash
terraform plan
```
2. Apply: To create the resources, execute the terraform apply command. Confirm the prompt to apply the changes.

```bash
terraform apply
```
After applying, Terraform will output resource details based on outputs.tf.


#### Step 6: Destroy Resources
When you're finished, you can destroy all resources created by Terraform by running:

```bash
terraform destroy
```
This command will delete all resources defined in the project, ensuring that no costs are incurred for unused resources.

### Outputs

After a successful apply, you’ll see the outputs defined in outputs.tf, including useful information such as:

- **Instance ID**: The ID of the EC2 instance created.
- **S3 Bucket Names**: The names of created S3 buckets.
- **DynamoDB Table Name**: The name of the DynamoDB table.
