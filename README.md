# Oopsie--HackTheBox--Cybersecurity-Learning-Journey
A complete walkthrough for the **Oopsie** machine on HackTheBox (Starting Point - Tier 2).

# HackTheBox - Oopsie Writeup
#📁 Repository Structure
Oopsie-HackTheBox/
├── README.md
├── screenshots/          # Room screenshots & proof
├── notes.md              # Detailed notes
└── exploits/
    └── shell.php

---

## 📖 Machine Overview

**Oopsie** is a Linux machine that focuses on **Broken Access Control**, **Insecure File Upload**, and **SUID/Path Hijacking** for privilege escalation.

- **Difficulty**: Easy
- **OS**: Linux
- **IP**: 10.129.6.22 (changes per spawn)

---

## ✅ Key Findings

### User Flag
`f2c74ee8db7983851ab2a96a44eb7981`

### Root Flag
`af13b0bee69f8a877c3faf667f7beacf`

---

## 📋 Detailed Writeup

### 1. Enumeration & Initial Access
- Discovered open ports: **22 (SSH)** and **80 (HTTP)**
- Found login page at `/cdn-cgi/login`
- Logged in as **Guest**

### 2. Broken Access Control (Cookie Manipulation)
- Used Developer Tools to inspect cookies
- Changed:
  - `role=guest` → `role=admin`
  - `user=2233` → `user=34322`
- Gained **Super Admin** access → Unlocked **Uploads** page

### 3. Foothold (Web Shell)
- Uploaded a PHP webshell (`shell.php`)
- Gained initial reverse shell as **`www-data`**

### 4. Lateral Movement (to robert)
- Found hardcoded credentials in `db.php`
- Password: `M3g4C0rpUs3r!`
- Switched user: `su robert`

### 5. Privilege Escalation (Root)
- Discovered `robert` belongs to `bugtracker` group
- Found SUID binary: `/usr/bin/bugtracker`
- Exploited **Path Hijacking**:
  ```bash
  cd /tmp
  echo '/bin/sh' > cat
  chmod +x cat
  export PATH=/tmp:$PATH
  bugtracker
  ---
![HackTheBox](https://img.shields.io/badge/HackTheBox-Oopsie-red)
![Linux](https://img.shields.io/badge/OS-Linux-blue)
![Difficulty](https://img.shields.io/badge/Difficulty-Easy-brightgreen)
![Status](https://img.shields.io/badge/Status-Completed-success)
---
🛠️ Techniques Learned

Cookie Manipulation (Broken Access Control)
Insecure File Upload → RCE
Hardcoded Credentials
SUID Binary Exploitation
PATH Hijacking


⭐ Credits & Resources

Platform: HackTheBox
Machine: Oopsie (Starting Point)
Completed on: May 23, 2026


For learning Linux Privilege Escalation 🔥

My LinkedIn: [https://www.linkedin.com/feed/update/urn:li:activity:7464041195472715776/]

My [X]: [https://x.com/charisma1385/status/2058274964608893133]


#HackTheBox #Linux #PrivilegeEscalation #PathHijacking #SUID #WebExploitation #BugBounty #CTF #Cybersecurity #InfoSec #EthicalHacking


  
