---
title: "WPA2 connection drops"
date: 2013-01-25
forum: Networking &amp; Wireless
---

### Post by spartan223193 on 2013-01-25
I am running Ubuntu 12.10 with a broadcom 4331 network card. I do have the proper drivers installed. My university uses WPA2-Enterprise on their wireless network. I can connect just fine and I do have full connectivity for the most part. However I often seem to have spouts were I continuously lose internet connectivity. Network manager states that I am still connected, the fix is disabling and re-enabling the connection. I think it has something to do with our authentication server since I couldn't specify that option in the GUI. I noticed wpa_supplicant.conf has been swapped out in favor of a different system. I was hoping someone could walk me through the steps to fix this issue. I greatly appreciate it. Here is a copy of the configuration for our wifi.


Security:	  WPA2-Enterprise (not WPA2-PSK)
Encryption:	  AES
Authentication Type:	  EAP-TTLS
Authentication Protocol:	  PAP
Certificate Authority:	  AddTrust External CA Root
Authentication Server:	  radius1.aset.psu.edu

---

### Post by cher80 on 2013-02-07
the same problem, macbook 8.1, b4331 wifi chip. Work perfectly while "WPA/WPA2 Personal" and drops connection constantly while in "WPA/WPA2 Enterprise" network.

---

### Post by cher80 on 2013-02-08
It seems I solved this removing standart Network manager and installing Wicd wireless manager. 

In wcid manager select PEAP with GTC (not WPA - strange) and provide your pass and log (with domain in my case). It works much more stable

---

### Post by cher80 on 2013-02-11
no, it wasn't solved, still disconnecting

---

