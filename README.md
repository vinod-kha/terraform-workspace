# Terraform EC2 Instance Deployment

This Terraform project automates the creation of an EC2 instance on AWS. It also demonstrates the usage of Terraform workspaces for managing multiple environments.

## Table of Contents

- [Overview](#overview)
- [Prerequisites](#prerequisites)
- [Project Structure](#project-structure)
- [Terraform Configuration](#terraform-configuration)
- [Usage](#usage)
  - [Initializing Terraform](#initializing-terraform)
  - [Creating Terraform Workspace](#creating-terraform-workspace)
  - [Deploying Infrastructure](#deploying-infrastructure)
- [Cleaning Up](#cleaning-up

## Overview

This Terraform project defines the infrastructure needed to create an EC2 instance on AWS. It uses Terraform workspaces to manage separate environments such as development, staging, and production.

## Prerequisites

Before you begin, ensure you have the following prerequisites installed:

- Terraform CLI
- AWS CLI configured with appropriate access credentials
- AWS account

## Project Structure

The project structure is as follows:

```
terraform-ec2-instance/
├── main.tf
├── variables.tf
└── terraform.tfvars
```

- `main.tf`: Contains the Terraform configuration for creating the EC2 instance.
- `variables.tf`: Defines input variables used in the Terraform configuration.
- `terraform.tfvars`: Specifies the values for input variables.

  
Terraform workspaces are useful for managing multiple environments (such as development, staging, and production) within a single Terraform configuration. Workspaces allow you to maintain separate state files for each environment while using the same configuration code. This helps in organizing and managing infrastructure resources more efficiently.

## Terraform Configuration

Modify the `variables.tf` and `terraform.tfvars` files to customize your EC2 instance configuration. Key variables include:

- `region`: AWS region where the EC2 instance will be created.
- `ami`: ID of the Amazon Machine Image (AMI) to use for the EC2 instance.
- `instance_type`: Type of EC2 instance to launch (e.g., t2.micro).
- `key_name`: Name of the SSH key pair used to access the instance.

Refer to the Terraform documentation for more information on configuring EC2 instances and input variables.

## Usage

Follow these steps to deploy the EC2 instance using Terraform:

### Initializing Terraform

1. Navigate to the project directory:

   ```bash
   cd terraform-ec2-instance/
   ```

2. Initialize Terraform:

   ```bash
   terraform init
   ```

### Creating Terraform Workspace

Create separate Terraform workspaces for each environment:

- Development:

  ```bash
  terraform workspace new development
  ```

- Staging:

  ```bash
  terraform workspace new staging
  ```

- Production:

  ```bash
  terraform workspace new production
  ```

### Deploying Infrastructure

1. Select the desired workspace (e.g., development, staging, production):

   ```bash
   terraform workspace select development
   ```

2. Review the Terraform plan:

   ```bash
   terraform plan
   ```

3. Apply the Terraform configuration to create the EC2 instance:

   ```bash
   terraform apply
   ```

## Cleaning Up

To destroy the resources created by Terraform and clean up:

1. Select the appropriate workspace:

   ```bash
   terraform workspace select development
   ```

2. Destroy the infrastructure:

   ```bash
   terraform destroy
   ```

3. Repeat the above steps for other workspaces as needed.

## Note

Benefits of Terraform Workspaces:

* Isolation: Each workspace maintains its own state file, allowing changes to be scoped to that environment only.
* Efficiency: Simplifies management of multiple environments with shared configuration code.
* Safety: Reduces the risk of accidentally modifying resources in the wrong environment.
* Consistency: Ensures consistent configurations across environments while allowing for environment-specific customization.
