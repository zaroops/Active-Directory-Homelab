# Active-Directory-Homelab

![Network Diagram](Network_Diagram.png)

## Network Overview

This lab uses a single NAT network inside VMware Workstation.
All machines share the same subnet 192.168.75.0/24.


## 🛡️ Active Directory Home Lab for Red Teaming + IT Help Desk Skills

This project documents the creation of a full Active Directory enterprise environment built using VMware Workstation Pro, Windows Server 2022, Windows 10, and Kali Linux.

The goal was to simulate a real corporate domain environment to learn:

• Windows Server administration

• Active Directory & Group Policy 

• User & computer management

• DNS and DHCP

• Networking fundamentals

• Red team attack techniques

• Blue team analysis and detection

## 🏗️ Virtual Lab Architecture

My Hypervisor: VMware Workstation Pro
Network: NAT (vmnet8)
Domain Name: homelb.local

| Machine        | OS           | IP Address  | Role  |
| ------------- |:-------------:| :-----:| -----:|
| Wiindows-Server-2022 | Windows Server 2022 | 192.168.75.133 | Domain Controller, DNS server|
| Windows-10-Server     | Windows 10 Home |   192.168.75.136 | Domain Joined Client, User|
| Kali-Linux | Kali Linux  |192.168.75.134| Attacker VM|

## Network Explanation

This network involved me utilizing VMware Workstation pro, configured on a NAT (private network on a single IP address), which was a hypervisor (virtualization software that creates and runs Virtual Machines) for my virtual machines on said private network. My goal was to learn how to use Microsoft Active Directory and to familiarize myself with it, alongside onboarding users and creating my own simulated corporate environment. I also took it a step further by introducing an attacker machine, to not only learn how active directory domain services work, but also how to exploit vulnerabilities within active directory domain services. Though not included in this lab, iI have a separate repository detailing my attacks. This involved setting up my windows 2022 server as the domain controller and dns server for my windows 10 machine, and then configure my kali linux attacker VM to be able to see said local network. 


## Active Directory Enterprise Lab 

## Overview

This lab establishes a **baseline enterprise Active Directory environment** that serves as the foundation for future offensive security testing, detection engineering, and SOC simulations.

The purpose of this phase is to build a **clean, functional, and realistic Active Directory domain** that mirrors a small-to-mid-sized enterprise. No attacks or security tooling are introduced at this stage. The focus is on **correct configuration, domain functionality, and operational realism**.

This environment will later be leveraged for:
- Active Directory attack simulations
- Red team vs blue team exercises
- SIEM log ingestion and SOC analysis

## Network Explanation

The lab operates on an **isolated internal virtual network** to simulate an enterprise LAN while preventing exposure to external networks.

### Network Characteristics
- Internal LAN-only communication between VMs
- No direct internet exposure to domain assets
- Static IP assignment for the Domain Controller

### Logical Flow
- **DC01** provides authentication, authorization, and DNS services
- **WIN10-01** functions as a standard employee workstation
- All authentication and domain traffic flows through the Domain Controller

This design ensures:
- Stable domain functionality
- Predictable authentication behavior
- A controlled baseline for future attack simulations

---

## Step-by-Step Setup

### 1. Hypervisor & Network Setup
- Hypervisor: VMware Workstation
- Created an **Internal Network** for lab communication
- Configured temporary NAT access for operating system updates

---

### 2. Domain Controller Setup (DC01)
- Installed Windows Server 2019
- Assigned a static IP address
- Installed:
  - Active Directory Domain Services (AD DS)
  - DNS Server role
- Promoted the server to a Domain Controller
- Created a new domain  
  - Example: `homelb.local`

---

### 3. Active Directory Configuration
- Created Organizational Units (OUs) to reflect enterprise structure:
  - Users
  - Workstations
  - IT
- Created domain user accounts:
  - Standard user accounts
  - Administrative accounts
- Configured basic Group Policy Objects (GPOs) for:
  - Password policies
  - User authentication behavior

---

### 4. Workstation Setup (WIN10-01)
- Installed Windows 10 Enterprise
- Joined the workstation to the Active Directory domain
- Verified:
  - Domain authentication
  - Domain user login functionality
- Simulated standard user activity to validate environment stability

---

## Learning Objectives

By completing this prerequisite lab, the following competencies are demonstrated:

- Deployment of a functional **Active Directory domain**
- Configuration of Windows Server as a Domain Controller
- Understanding of **identity and access management fundamentals**
- Domain user and workstation lifecycle management
- Enterprise-style Active Directory organizational structure
- Preparation of a clean baseline environment for security testing

---

## Why This Phase Matters

A properly configured Active Directory environment is critical for:
- Realistic attack simulation
- Accurate detection engineering
- Meaningful SOC investigations

This phase ensures all future security testing is performed against a **stable, enterprise-authentic identity infrastructure**, allowing analysis to focus on attacker behavior rather than configuration issues.

---

