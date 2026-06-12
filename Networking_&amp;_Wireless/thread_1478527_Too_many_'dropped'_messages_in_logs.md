---
title: "Too many 'dropped' messages in logs?"
date: 2010-05-09
forum: Networking &amp; Wireless
---

### Post by DragonDon on 2010-05-09
Greetings all,

I am somewhat new to Ubuntu and am currently trying to learn about logs and in particular firewalls.

I wanted to know if there is something mis-configured in my setup in that I am seeing a ton of the following:

13256.485415] DROPPED IN=eth0 OUT= MAC=00:16:76:5f:25:a7:00:0f:66:a5:76:8a:08:00 SRC=94.96.95.135 DST=192.168.1.9 LEN=58 TOS=0x00 PREC=0x00 TTL=106 ID=20552 PROTO=UDP SPT=10312 DPT=51413 LEN=38 
May  9 19:39:51 dragondon-desktop kernel: [13257.271556] DROPPED IN=eth0 OUT= MAC=00:16:76:5f:25:a7:00:0f:66:a5:76:8a:08:00 SRC=41.178.159.134 DST=192.168.1.9 LEN=58 TOS=0x00 PREC=0x00 TTL=108 ID=18635 PROTO=UDP SPT=53768 DPT=51413 LEN=38 
May  9 19:39:52 dragondon-desktop kernel: [13257.553348] DROPPED IN=eth0 OUT= MAC=00:16:76:5f:25:a7:00:0f:66:a5:76:8a:08:00 SRC=68.69.201.190 DST=192.168.1.9 LEN=58 TOS=0x00 PREC=0x00 TTL=117 ID=47754 PROTO=UDP SPT=15154 DPT=51413 LEN=38 
May  9 19:39:52 dragondon-desktop kernel: [13258.268280] DROPPED IN=eth0 OUT= MAC=00:16:76:5f:25:a7:00:0f:66:a5:76:8a:08:00 SRC=84.208.84.231 DST=192.168.1.9 LEN=58 TOS=0x00 PREC=0x00 TTL=110 ID=42612 PROTO=UDP SPT=41297 DPT=51413 LEN=38 
May  9 19:39:54 dragondon-desktop kernel: [13259.420129] DROPPED IN= OUT=eth0 SRC=192.168.1.9 DST=192.168.1.255 LEN=209 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=189 

Any help in understanding this output would be greatly appreciated.

Ubuntu 10.04 LTS
Dell Dimension 1100 (1GB Ram, 2.8GHz Intel)

Don

---

