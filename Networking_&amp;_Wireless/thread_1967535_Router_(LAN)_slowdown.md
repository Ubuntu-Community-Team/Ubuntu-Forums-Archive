---
title: "Router (LAN) slowdown"
date: 2012-04-28
forum: Networking &amp; Wireless
---

### Post by Jimmey on 2012-04-28
Hello, 

I have a problem with my wireless. Every so often it slows down to a crawl, and is particularly noticable when I am playing enemy territory - Even between my housemates on the LAN. My router is a netgear wgr614v9.

When I do "dmesg" I get:

> 
[156541.671494] Inbound IN=wlan0 OUT= MAC=00:0f:66:6f:78:a5:00:1f:33:db:cd:50:08:00 SRC=192.168.1.1 DST=192.168.1.2 LEN=576 TOS=0x00 PREC=0xC0 TTL=64 ID=44143 PROTO=ICMP TYPE=3 CODE=4 [SRC=192.168.1.2 DST=85.90.254.227 LEN=1500 TOS=0x00 PREC=0x00 TTL=63 ID=65519 DF PROTO=TCP SPT=34153 DPT=80 WINDOW=65535 RES=0x00 ACK URGP=0 ] MTU=1492 


With 192.168.1.2 being my IP, and 192.168.1.1 being my router. There are several entries like this at the time of the slowdown.

I have had it in the past where the "SRC" IP has been 192.168.1.13, even though this IP never showed in the router's "attached devices" table.

Does anybody know what would cause this drastic slow down? What does the above message mean?

Any help is appreciated.

Cheers

---

