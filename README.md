<h1 align="center"><strong>AWS Auto Scaling Group + Application Load Balancer (Terraform Project)</strong></h1>

This project deploys a complete, production-style AWS environment using Terraform. It demonstrates your ability to design and provision real-world cloud infrastructure including networking, compute scaling, load balancing, and secure architecture patterns.

This setup is similar to what many organizations use in their web applications: highly available, scalable, and fault-tolerant.

## 📌 Project Overview

This Terraform configuration builds:

Networking

A VPC (10.112.0.0/16)

3 public subnets (for Load Balancer and NAT Gateway)

3 private subnets (for EC2 instances)

An Internet Gateway

A NAT Gateway

Public and private route tables with correct routing

Security

Security Group for the Load Balancer

Security Group for EC2 instances

Only HTTP (port 80) is allowed to the instances

Compute

A Launch Template that:

Uses Amazon Linux 2023

Installs Apache (httpd)

Generates a custom HTML page displaying instance metadata

Load Balancing

An Application Load Balancer (ALB)

A Target Group attached to the ALB

HTTP listener on port 80

Auto Scaling

An Auto Scaling Group (ASG) deployed across 3 AZs

Automatically registers EC2 instances to the target group

Auto scaling policy based on CPU utilization

ASG configuration:

min_size = 1

desired_capacity = 2

max_size = 3

This ensures high availability and elasticity while controlling cost.

🧠 What This Architecture Demonstrates
1. High Availability Across Multiple AZs

The application runs in three Availability Zones, ensuring continuity even during an AZ failure.

2. Scalable Compute Layer

The ASG automatically adds or removes EC2 instances based on traffic and CPU load.

3. Secure and Modern AWS Architecture

Instances are placed in private subnets and access the internet through a NAT Gateway, which is a best practice for production workloads.

4. Infrastructure as Code (IaC)

The project demonstrates a strong command of Terraform fundamentals:

Providers

Resources

Dependencies

Launch templates

Auto scaling settings

Load balancer configuration

Modular file structure

This mirrors real DevOps workflows.

📂 Repository Structure
.
├── 0-auth.tf
├── 1-vpc.tf
├── 2-subnets.tf
├── 3-igw.tf
├── 4-nat.tf
├── 5-route.tf
├── 6-sg01-all.tf
├── 7-launchtemplate.tf
├── 8-targetgroup.tf
├── 9-loadbalancer.tf
├── 10-autoscalinggroup.tf
└── .gitignore


Each file represents a distinct layer of the infrastructure — a clean, modular layout used in professional environments.

🛠️ How to Deploy the Infrastructure
1. Initialize Terraform
terraform init


This downloads required provider plugins and prepares the environment.

2. Preview the Infrastructure
terraform plan


This shows exactly what Terraform will create.

3. Deploy the Environment
terraform apply


Approve when prompted.

After deployment completes, Terraform outputs:

lb_dns_name = your-loadbalancer.amazonaws.com


Paste the DNS name into a browser to load your dynamically generated web page.

4. Clean Up (Destroy All Resources)
terraform destroy


This safely removes all provisioned resources to avoid charges.

🔒 Security & Best Practices
Your .gitignore protects sensitive files:
.terraform/
*.tfstate
*.tfstate.backup
.terraform.lock.hcl


State files are never committed, ensuring:

Credentials are not exposed

Resource IDs remain local

You follow industry IaC hygiene standards

🧩 Key AWS & Terraform Skills Demonstrated

This project showcases proficiency in:

✔ Amazon VPC design (public/private subnets)
✔ Internet/NAT Gateway configuration
✔ Route tables and routing patterns
✔ EC2 Launch Templates
✔ Application Load Balancer setup
✔ Target Groups & health checks
✔ Auto Scaling Groups with scaling policies
✔ User data scripting and metadata usage
✔ Terraform provider configuration
✔ Modular Terraform architecture
✔ Git/GitHub workflow

This is a strong portfolio-ready project demonstrating real cloud engineering capability.
