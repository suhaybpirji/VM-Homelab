# VM-Homelab

# 🏠 Homelab Project

This repository documents my enterprise-style homelab environment built using pfSense, Windows Server Active Directory, DNS, DHCP, and VirtualBox.  
The goal of this lab is to simulate a real corporate network and gain hands‑on experience with networking, identity, security, and systems administration.

---

## 🔧 Technologies Used

- **pfSense Firewall**
- **Windows Server 2022** (AD DS, DNS, DHCP)
- **Windows 10/11 Client**
- **VirtualBox**
- **VLANs & Network Segmentation**
- **PowerShell**
- **Basic Linux (optional)**

---

## 📁 Repository Structure

```text
homelab/
├── documentation/
│   ├── network-diagram.png
│   ├── architecture-overview.md
│   ├── topology.md
│
├── configs/
│   ├── pfsense/
│   │   ├── dhcp-config.xml
│   │   ├── firewall-rules.xml
│   │   ├── vlans-config.xml
│   ├── windows-server/
│   │   ├── ad-ds-setup.md
│   │   ├── dns-config.md
│   │   ├── dhcp-config.md
│   │   ├── gpo-baseline.md
│
├── screenshots/
│   ├── pfsense-dashboard.png
│   ├── ad-users-and-computers.png
│   ├── dns-manager.png
│   ├── dhcp-manager.png
│
├── scripts/
│   ├── powershell/
│   ├── bash/
│
└── README.md
```

---

## 🌐 Simple Network Diagram

```text
                   Internet
                       │
                       │
                ┌──────▼──────┐
                │   pfSense    │
                │ Firewall/Router
                └──────┬──────┘
                       │
                VirtualBox Internal Network
                       │
        ┌──────────────┼──────────────┐
        │              │              │
┌───────▼───────┐ ┌────▼───────┐ ┌────▼───────┐
│ Windows Server │ │ Windows 11 │ │ (Optional) │
│  AD / DNS /    │ │ Domain PC  │ │  Linux VM  │
│     DHCP       │ │ Joined to  │ │  (Future)  │
└───────────────┘ │   Domain    │ └────────────┘
                   └────────────┘
```

---

## 🧱 Homelab Overview

This homelab simulates a small enterprise network with:

- A **pfSense firewall** acting as the router, firewall, and DHCP/DNS forwarder  
- A **Windows Server 2022 domain controller** providing:
  - Active Directory Domain Services  
  - DNS  
  - DHCP  
- A **Windows 10/11 client** joined to the domain  
- A **segmented network** using VLANs  
- All running inside **VirtualBox**  

This setup mirrors real-world corporate infrastructure and provides hands-on experience with identity, networking, and security.

---

## 🔐 VLAN Plan

| VLAN | Name        | Purpose                     | Subnet            |
|------|-------------|-----------------------------|-------------------|
| 10   | Servers     | Domain Controller, DNS      | 192.168.10.0/24   |
| 20   | Clients     | Windows 10/11 PCs           | 192.168.20.0/24   |
| 30   | Management  | pfSense, Admin PC           | 192.168.30.0/24   |

---

## 🔐 pfSense Configuration

Documented in `/configs/pfsense/`:

- WAN (NAT from VirtualBox)
- LAN (Internal Network)
- DHCP for VLANs
- DNS Resolver forwarding to Windows Server
- Firewall rules:
  - Allow LAN → DC
  - Allow Clients → DC
  - Block inter-VLAN traffic (optional)

---

## 🗂️ Active Directory Configuration

Documented in `/configs/windows-server/`:

- Domain setup  
- DNS zones  
- DHCP scopes  
- OU structure  
- GPO baseline  
- Domain join steps  

---

## 🖥️ VirtualBox Setup

- pfSense VM (2 NICs: NAT + Internal Network)  
- Windows Server VM (Internal Network)  
- Windows 11 VM (Internal Network)  

---

## 📸 Screenshots

Add screenshots to `/screenshots/`:

- pfSense dashboard  
- AD Users & Computers  
- DNS Manager  
- DHCP Manager  
- Network diagram  

---

## 🚀 Future Improvements

- Add Linux server (web, monitoring, syslog)  
- Add Zabbix or Grafana monitoring  
- Add Wazuh SIEM  
- Add Ansible automation  
- Add Terraform for VM provisioning  
- Add Azure AD Sync  
- Add Intune MDM  

