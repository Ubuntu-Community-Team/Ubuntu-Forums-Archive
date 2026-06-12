---
title: "syslog seems too busy"
date: 2009-07-07
forum: Networking &amp; Wireless
---

### Post by dirkraft on 2009-07-07
```

Jul  7 10:11:19 GATEWAY kernel: [235138.574722] Inbound IN=eth0 OUT= MAC=00:50:8b:9a:e8:23:00:01:5c:22:64:82:08:00 SRC=99.240.95.245 DST=72.48.211.132 LEN=48 TOS=0x00 PREC=0x00 TTL=119 ID=20620 DF PROTO=TCP SPT=1186 DPT=39018 WINDOW=65535 RES=0x00 SYN URGP=0
Jul  7 10:11:21 GATEWAY kernel: [235140.423281] Inbound IN=eth0 OUT= MAC=00:50:8b:9a:e8:23:00:01:5c:22:64:82:08:00 SRC=120.28.142.57 DST=72.48.211.132 LEN=95 TOS=0x00 PREC=0x00 TTL=115 ID=23684 PROTO=UDP SPT=19564 DPT=39018 LEN=75
Jul  7 10:11:22 GATEWAY kernel: [235141.563677] Inbound IN=eth0 OUT= MAC=00:50:8b:9a:e8:23:00:01:5c:22:64:82:08:00 SRC=99.240.95.245 DST=72.48.211.132 LEN=48 TOS=0x00 PREC=0x00 TTL=119 ID=20634 DF PROTO=TCP SPT=1186 DPT=39018 WINDOW=65535 RES=0x00 SYN URGP=0
Jul  7 10:11:24 GATEWAY kernel: [235143.158383] Inbound IN=eth0 OUT= MAC=00:50:8b:9a:e8:23:00:01:5c:22:64:82:08:00 SRC=201.253.182.11 DST=72.48.211.132 LEN=131 TOS=0x00 PREC=0x00 TTL=119 ID=5064 PROTO=UDP SPT=15633 DPT=39018 LEN=111
Jul  7 10:11:25 GATEWAY kernel: [235144.019529] Inbound IN=eth0 OUT= MAC=00:50:8b:9a:e8:23:00:01:5c:22:64:82:08:00 SRC=78.63.142.73 DST=72.48.211.132 LEN=131 TOS=0x00 PREC=0x00 TTL=117 ID=49393 PROTO=UDP SPT=14157 DPT=39018 LEN=111
Jul  7 10:11:26 GATEWAY kernel: [235145.598157] Inbound IN=eth0 OUT= MAC=00:50:8b:9a:e8:23:00:01:5c:22:64:82:08:00 SRC=69.255.2.122 DST=72.48.211.132 LEN=95 TOS=0x00 PREC=0x00 TTL=119 ID=60443 PROTO=UDP SPT=17492 DPT=39018 LEN=75
Jul  7 10:11:26 GATEWAY kernel: [235145.860118] Inbound IN=eth0 OUT= MAC=00:50:8b:9a:e8:23:00:01:5c:22:64:82:08:00 SRC=74.64.62.53 DST=72.48.211.132 LEN=95 TOS=0x00 PREC=0x00 TTL=118 ID=7507 PROTO=UDP SPT=18632 DPT=39018 LEN=75
Jul  7 10:11:26 GATEWAY kernel: [235145.869074] Inbound IN=eth0 OUT= MAC=00:50:8b:9a:e8:23:00:01:5c:22:64:82:08:00 SRC=74.45.39.111 DST=72.48.211.132 LEN=95 TOS=0x00 PREC=0x00 TTL=118 ID=57698 PROTO=UDP SPT=60617 DPT=39018 LEN=75

```

I am still relatively new to Ubuntu/Linux. This stuff seems to get constantly streamed into my syslog:

1. What am I seeing here? Is it normal?
2. If the answer to #1 doesn't make it go away and it is normal and safe traffic, how can I make it stop logging to syslog (so that I can see more important messages)?

Some background info: This machine is an Apache server and therefore always on. It's also a router to my home network (hence the uncreative naming "GATEWAY" that appears in the logs). It has Firestarter managing firewall rules and Samba shares to my other PCs (and a Mac which doesn't call itself a PC for some reason). There are multiple people using this network, so I'm not always sure what all they might be running (nothing malicious though). Not sure how this might affect the above questions, but I thought it worth mentioning. 

TIA for your tips! :)

---

### Post by puppywhacker on 2009-07-07
I supsect it's your firewall logging all attempts of computers connecting to port UDP/39018

I don't know how/why, but I think your firestarter may have some logging turned on.

---

