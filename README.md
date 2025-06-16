---

# 🏨 Hotel Management Lab Simulation

## 📦 Project Overview

This is a network simulation project created using **Cisco Packet Tracer (version 8.2.2)**. It models a 3-floor hotel network infrastructure, where each floor represents different departments. Each department is assigned a unique VLAN and subnet for proper segmentation, security, and management.

---

## ✅ Requirements

* Cisco Packet Tracer **version 8.2.2** or later
* Basic understanding of:

  * VLAN configuration
  * Inter-router connectivity (DCE/Serial)
  * Subnetting and IP addressing
  * Switch and router configuration

---

## 🏢 Network Design Summary

### 🧱 Floors and Departments

| Floor     | Departments                 |
| --------- | --------------------------- |
| 1st Floor | Reception, Store, Logistics |
| 2nd Floor | Finance, HR, Sales          |
| 3rd Floor | IT, Admin                   |

* Each department is assigned a **dedicated VLAN** and **separate subnet**.
* Each floor has its **own switch** and is connected to a **dedicated router**.
* All three routers are **interconnected using DCE serial cables**.
* All routers are housed in the **IT department (3rd floor)**.

---

## 🗂️ VLAN & IP Addressing Scheme

| Floor   | Department | VLAN | Network Address |
| ------- | ---------- | ---- | --------------- |
| **1st** | Reception  | 80   | 192.168.8.0/24  |
|         | Store      | 70   | 192.168.7.0/24  |
|         | Logistics  | 60   | 192.168.6.0/24  |
| **2nd** | Finance    | 50   | 192.168.5.0/24  |
|         | HR         | 40   | 192.168.4.0/24  |
|         | Sales      | 30   | 192.168.3.0/24  |
| **3rd** | Admin      | 20   | 192.168.2.0/24  |
|         | IT         | 10   | 192.168.1.0/24  |

---

## 🔌 Inter-Router Network Configuration

The three routers are connected via serial interfaces with the following point-to-point subnets:

| Connection        | Network       | CIDR |
| ----------------- | ------------- | ---- |
| Router1 ↔ Router2 | 10.10.10.0/30 | /30  |
| Router2 ↔ Router3 | 10.10.10.4/30 | /30  |
| Router1 ↔ Router3 | 10.10.10.8/30 | /30  |

---

## 📡 Additional Features

* Each **floor has a Wi-Fi network** connected to the switch (used for laptops).
* **Each department has a dedicated printer**.
* All routing and VLAN configurations support full inter-department communication via the core network.

---

## 🔧 Configuration Summary (Examples)

### VLAN Setup (Switch):

```bash
Switch(config)# vlan 10
Switch(config-vlan)# name IT
Switch(config)# interface fa0/1
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 10
```

### Router-on-a-Stick (Router Subinterfaces):

```bash
Router(config)# interface g0/0.10
Router(config-subif)# encapsulation dot1Q 10
Router(config-subif)# ip address 192.168.1.1 255.255.255.0
```

### Serial Interface Configuration:

```bash
Router(config)# interface s0/0/0
Router(config-if)# ip address 10.10.10.1 255.255.255.252
Router(config-if)# clock rate 64000
Router(config-if)# no shutdown
```

---

## ✅ How to Verify

* Use `ping` between PCs from different VLANs to verify inter-VLAN routing.
* Run `show vlan brief` on switches to ensure VLANs are configured.
* Use `show ip interface brief` and `show ip route` on routers.
* Ensure all departments can reach their respective printers and Wi-Fi APs.

---

## 🧑‍💻 Author

**\[nyamsec]**
Hotel Management Lab Simulation – Packet Tracer (2025)

---

