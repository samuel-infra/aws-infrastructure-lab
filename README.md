# AWS Infrastructure Lab

![AWS](https://img.shields.io/badge/AWS-EC2%20%7C%20VPC%20%7C%20EBS-FF9900?logo=amazonwebservices&logoColor=white)
![Windows Server](https://img.shields.io/badge/Windows-Server-0078D4)
![SQL Server](https://img.shields.io/badge/SQL%20Server-2025%20Express-CC2927)

> **Hands-on AWS infrastructure project:** deploying and securing two Windows Server EC2 instances, validating private communication, sharing EBS-backed storage over SMB, and testing a SQL Server database.

## Project Overview

Built for the fictional company **Sweditech AB**, this lab demonstrates how networking, compute, storage, security and database administration work together in Amazon Web Services.

## Architecture

```text
AWS VPC / subnets
  |
  +-- Sweditech-AWS-VM01 (10.0.24.98)
  |      |
  |      +-- Private network connectivity to VM02
  |      +-- SMB client: \\10.0.0.150\Gemensam
  |
  +-- Sweditech-AWS-VM02 (10.0.0.150)
         |
         +-- 10 GB Amazon EBS volume
         +-- Windows SMB shared folder
         +-- SQL Server 2025 Express
         +-- SQL Server Management Studio 22
         +-- SweditechDB / Anstallda table
```

## Technologies

Amazon VPC · Amazon EC2 · Amazon EBS · AWS Security Groups · Windows Server · Windows Firewall · SMB · Microsoft SQL Server 2025 Express · SSMS 22

## Implementation

### 1. Networking and compute
- Created an AWS VPC with subnets, routing and an Internet Gateway.
- Deployed **Sweditech-AWS-VM01** and **Sweditech-AWS-VM02**.
- Tested connectivity between the instances over private IP addresses using ping.

### 2. Network security
- Configured the **Sweditech-AWS-SG** security group and Windows Firewall rules.
- Restricted inbound RDP (TCP 3389) to the administrator's own public IP.
- Configured ICMP for connectivity tests and SMB for the required file-sharing traffic.

### 3. Shared storage
- Attached a **10 GB EBS volume** to VM02.
- Configured a shared Windows folder at `G:\Gemensam Lagring\Gemensam`.
- Accessed the SMB share from VM01 at `\\10.0.0.150\Gemensam` and verified shared file access.

### 4. SQL Server and database verification
- Installed **SQL Server 2025 Express** on VM02.
- Installed **SQL Server Management Studio 22** on VM02 and connected to `localhost\SQLEXPRESS` using Windows Authentication.
- Created **SweditechDB** and the **Anstallda** table.
- Inserted and retrieved test records to confirm the database worked.

## Validation Results

| Test | Result |
|---|---|
| Private connectivity between EC2 instances | Verified with ping |
| SMB share accessible from VM01 | Verified |
| SQL Server instance accessible in SSMS | Verified |
| Database creation and test data retrieval | Verified |

## What This Project Demonstrates

- Designing and deploying a multi-server AWS environment
- Configuring network-level and host-level access controls
- Troubleshooting private connectivity and Windows file sharing
- Integrating block storage, SMB services and SQL Server
- Verifying infrastructure through hands-on tests

## Evidence

Screenshots from the original lab report can be added to a `screenshots/` directory. Do not upload passwords, access keys, public IPs or sensitive account identifiers.

---

*Educational infrastructure lab; not a production deployment.*