
# 🔐 Secure DMZ Network Design using Cisco Packet Tracer

## 📌 Project Overview
This project demonstrates the design and implementation of a **secure enterprise network** using **Cisco Packet Tracer**, focusing on **network security, DMZ architecture, firewall concepts, and NAT configuration**.

The network is designed to allow **external users to securely access a public web server hosted in a DMZ**, while **protecting the internal LAN** from unauthorized access using **Access Control Lists (ACLs)** and **Network Address Translation (NAT)**.

This project reflects **real-world enterprise network security principles** commonly used in corporate environments.

---

## 🎯 Project Objectives
- Design a **secure enterprise network topology**
- Implement a **DMZ (Demilitarized Zone)** for public services
- Configure **Static NAT** for public web access
- Configure **PAT (NAT Overload)** for internal LAN users
- Apply **Firewall ACL rules** to restrict traffic
- Ensure **internal network isolation**
- Validate traffic flow using **Packet Tracer simulation**

---

## 🏗️ Network Topology Description

### Network Zones
| Zone | Description |
|----|----|
| External Network | Simulated internet users |
| Firewall Zone | Central security control point |
| DMZ | Hosts public-facing servers |
| Internal LAN | Private enterprise users |

### Devices Used
- Routers: 3 × Cisco 2911  
- Switches: 2 × Cisco 2960  
- Servers: Web Server, DNS Server  
- End Devices: External PC, Internal LAN PC

---

## 🌐 IP Addressing Scheme

### External Network
```
198.51.100.0/24
EXT-PC           : 198.51.100.10
ISP Router       : 198.51.100.1
```

### WAN (ISP ↔ Firewall)
```
203.0.113.0/30
ISP Router       : 203.0.113.1
Firewall Router  : 203.0.113.2
```

### DMZ Network
```
172.16.10.0/24
Firewall (DMZ)   : 172.16.10.1
Web Server       : 172.16.10.10
DNS Server       : 172.16.10.20
```

### Internal LAN
```
192.168.10.0/24
LAN Router       : 192.168.10.1
LAN-PC           : 192.168.10.10
```

---

## 🔁 NAT Configuration

### Static NAT
```
ip nat inside source static 172.16.10.10 203.0.113.10
```

### PAT Configuration
```
access-list 1 permit 192.168.10.0 0.0.0.255
ip nat inside source list 1 interface Serial0/3/0 overload
```

---

## 🔥 Firewall & Security Configuration

### Access Control List (ACL)
```
ip access-list extended OUTSIDE_IN
 permit tcp any host 203.0.113.10 eq 80
 permit tcp any host 203.0.113.10 eq 443
 deny ip any 192.168.10.0 0.0.0.255
 permit ip any any
```

---

## 🧪 Testing & Verification
- External users can access DMZ web server
- Internal LAN is protected from external access
- NAT translations verified using:
```
show ip nat translations
```

---

## ⚠️ Packet Tracer Limitation
Cisco Packet Tracer may not always render HTTP pages correctly for DMZ + Static NAT setups. Verification was done using **Simulation Mode** and NAT tables.

---

## 📂 Repository Structure
```
secure-dmz-network-cisco-packet-tracer/
├── Secure-DMZ-Network.pkt
├── screenshots/
├── configs/
└── README.md
```

---

## 🚀 Skills Demonstrated
- DMZ Architecture
- Static NAT & PAT
- Firewall ACLs
- Routing & Security
- Cisco Packet Tracer

---

## 👤 Author
**Vihanga Nethsara**  
Computer Science Undergraduate – University of Jaffna  

---

## 📜 License
Educational use only.
