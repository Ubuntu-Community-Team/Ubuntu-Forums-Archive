---
title: "No TKIP security"
date: 2012-04-12
forum: Networking &amp; Wireless
---

### Post by robalrr on 2012-04-12
I have a problem because I need to configure a network with this configuration

Network Name: MyNet
Security: WPA Enterprise
EAP Method: TTLS
Key Type: TKIP
Inner Authentication: PAP
Identity: MyIdentity
Password: **************
Anonymous identity: @Anony.mo.us
CA Certificate File: None

My problem is that in the new network manager there is not Key Type option, so I cannot define the TKIP option, I tried omitting this parameter but the system do not connect.

---

### Post by haqking on 2012-04-12
WPA enterprise or 802.1x uses CCMP/AES over TKIP

and you need a radius server

---

