---
title: "Ubuntu networking"
date: 2010-07-11
forum: Networking &amp; Wireless
---

### Post by Crzyrev2 on 2010-07-11
I am attempting to network a second desktop using Ubuntu 10.04 to my home wireless network.  I ran "iwconfig" and results:
lo   no wireless extensions
wlan  IEEE 802.11bgn  ESSID: "JonesFN"
Mode: Managed   Frequency: 2.462 Ghz
Access Point: Not Associated
Tx -Power= 12dBar
Retry Long Limit: 7  RTS  thr: off
Fragment thr: off
power management: on 

Any suggestions would be appreciated,

---

### Post by cavalier911 on 2010-07-12
iwconfig indicates ubuntu is communicating with your wireless adapter.
Make sure the adapter is turned on if it's built-in to a laptop.

Network Manager is the software we use to setup and manage the wireless connections on Ubuntu. 

Network Manager tutorial: 
[https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7)

---

