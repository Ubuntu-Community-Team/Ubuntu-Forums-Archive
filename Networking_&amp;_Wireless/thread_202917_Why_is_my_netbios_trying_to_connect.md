---
title: "Why is my netbios trying to connect?"
date: 2006-06-24
forum: Networking &amp; Wireless
---

### Post by mibadt on 2006-06-24
Hi,
Scanning my syslog, I noticed that my firewall has rejected multiple repeated trials of connections via ports 137 and 138. I've checked and found that these ports are related to NETBIOS Name & Datagram Services. 
What's going on? Is this OK? How can I stop it?

TIA
;) 



---------------copy of relevant syslog segment-----------
Jun 24 12:47:54 localhost kernel: [4316294.190000] DROPPED IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0c:6e:94:36:18:08:00 SRC=10.0.0.3 DST=10.255.255.255 LEN=214 TOS=0x00 PREC=0x00 TTL=128 ID=550 PROTO=UDP SPT=138 DPT=138 LEN=194
Jun 24 12:47:54 localhost kernel: [4316295.008000] DROPPED IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0c:6e:94:36:18:08:00 SRC=10.0.0.3 DST=10.255.255.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=552 PROTO=UDP SPT=137 DPT=137 LEN=58

---------------end--------------------------------

---

