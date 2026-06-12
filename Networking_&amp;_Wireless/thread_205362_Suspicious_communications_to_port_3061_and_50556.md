---
title: "Suspicious communications to port 3061 and 50556"
date: 2006-06-28
forum: Networking &amp; Wireless
---

### Post by mibadt on 2006-06-28
Hi
,
My Kubuntu 6.0.6 is connected to a router with a static IP address for its single, on-board Ethernet card.
Scanning the syslog, I noticed 2 suspicious communication trial which have been blocked by my firewall to ports 3061 and 50556.

The communication to port 3061 takes place multiple times only and the end of an (otherwise) flawless boot. The other communication takes place during normal operation. I've checked and found that port 3061 is related to Visinet Gui- haven't clue what's that and if I need it. Could not find reference to port 50556 (neither of these appears in my /etc/services).

Please advise how to get rid of these communication trials.

TIA:) 

---------copy of my syslog---------------
Jun 28 17:42:44 localhost kernel: [4294956.520000] DROPPED IN=eth0 OUT= MAC=00:14:85:18:62:ee:00:30:0a:2a:d2:f7:08:00 SRC=87.106.4.56 DST=10.0.0.1 LEN=1452 TOS=0x00 PREC=0x00 TTL=54 ID=6033 DF PROTO=TCP SPT=80 DPT=3601 SEQ=3248314172 ACK=3261826868 WINDOW=1996 RES=0x00 ACK URGP=0


Jun 28 17:46:28 localhost kernel: [4295180.966000] DROPPED IN=eth0 OUT= MAC=00:14:85:18:62:ee:00:30:0a:2a:d2:f7:08:00 SRC=84.19.115.24 DST=10.0.0.1 LEN=48 TOS=0x00 PREC=0x00 TTL=117 ID=25559 DF PROTO=TCP SPT=2698 DPT=50556 SEQ=3271339402 ACK=0 WINDOW=16384 RES=0x00 SYN URGP=0 OPT (0204058401010402)

-----------end-------------

---

