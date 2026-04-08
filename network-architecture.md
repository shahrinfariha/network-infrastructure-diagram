# Network Architecture Documentation

## Overview
This document provides a detailed overview of the network architecture utilized with the following components:

- **Proxmox**: A virtualization management solution.
- **Dell PowerEdge R630**: Servers used for hosting virtual machines.
- **MikroTik RouterOS v7.21.3**: Router operating system.
- **OPNsense 26.1.5**: Firewall solution.
- **Cisco Catalyst 2960-S Switch**: Layer 2 switch for VLAN management.
- **Ceph Storage Cluster**: Distributed storage system.

## Network Infrastructure Diagram
Below is a visual ASCII representation of the network infrastructure:
```
+-----------------+
|  MikroTik       |
|   Router        |
+----+------------+
     |  
     |  (ISP)  
     |  
+------------+     +-----------------+
|  LAN       |<----|   OPNsense      |
| (VLAN 10)  |      |   Firewall      |
+------------+      +--+---------+----+
                       |         |    
                       |         |(VLAN 20)
                +------+----+    +--+---------+--+
                |  Dell       |   |  Cisco     |
                | PowerEdge   |   | Catalyst   |
                | R630        |---| 2960-S    |
                +-------------+   +------------+
                      |                     |   
                  (VLAN 30)            (VLAN 20)
                      |                     |   
               +------+----+         +-----+----+
               |  Ceph       |         |  Servers |
               |  Storage    |         +----------+
               |  Cluster    |
               +-------------+
```

## VLAN Configurations
- **System VLAN (10)**: Used for system management traffic.
- **DEV VLAN (20)**: Used for development traffic.
- **NOC VLAN (30)**: Used for network operations communication.

## Storage Specifications
The Ceph storage cluster is configured to support high availability and scalable storage solutions, providing block storage to the servers. 

### Storage Cluster Components:
- **OSD (Object Storage Daemon)**: At least 3 replicas for redundancy.
- **Monitor Nodes**: For cluster health monitoring and management.

Ensure all configurations adhere to the documentation guidelines and best practices for network security and efficiency.