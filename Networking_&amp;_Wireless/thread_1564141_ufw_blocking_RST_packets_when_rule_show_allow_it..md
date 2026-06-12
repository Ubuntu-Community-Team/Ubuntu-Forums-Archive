---
title: "ufw blocking RST packets when rule show allow it."
date: 2010-08-30
forum: Networking &amp; Wireless
---

### Post by ojconcentrate on 2010-08-30
hello all,

I've setup ufw rules on my system but noticed that the rule i created to allow traffic from my local network is still dropping some RST packets.

here's part of the output of dmesg


[43627.361500] [UFW BLOCK] IN=wlan0 OUT= MAC=00:16:ea:03:9c:3a:00:1f:a7:3d:d5:eb:08:00 SRC=192.168.0.4 DST=192.168.0.3 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=2210 PROTO=TCP SPT=59521 DPT=9000 WINDOW=0 RES=0x00 RST URGP=0 
[43647.118603] [UFW BLOCK] IN=wlan0 OUT= MAC=00:16:ea:03:9c:3a:00:1f:a7:3d:d5:eb:08:00 SRC=192.168.0.4 DST=192.168.0.3 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=35357 PROTO=TCP SPT=59461 DPT=9000 WINDOW=0 RES=0x00 RST URGP=0 
[43666.856684] [UFW BLOCK] IN=wlan0 OUT= MAC=00:16:ea:03:9c:3a:00:1f:a7:3d:d5:eb:08:00 SRC=192.168.0.4 DST=192.168.0.3 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=1261 PROTO=TCP SPT=59388 DPT=9000 WINDOW=0 RES=0x00 RST URGP=0 
[43686.844727] [UFW BLOCK] IN=wlan0 OUT= MAC=00:16:ea:03:9c:3a:00:1f:a7:3d:d5:eb:08:00 SRC=192.168.0.4 DST=192.168.0.3 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=39390 PROTO=TCP SPT=59314 DPT=9000 WINDOW=0 RES=0x00 RST URGP=0 
[43706.741870] [UFW BLOCK] IN=wlan0 OUT= MAC=00:16:ea:03:9c:3a:00:1f:a7:3d:d5:eb:08:00 SRC=192.168.0.4 DST=192.168.0.3 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=5719 PROTO=TCP SPT=59248 DPT=9000 WINDOW=0 RES=0x00 RST URGP=0 
[43726.989422] [UFW BLOCK] IN=wlan0 OUT= MAC=00:16:ea:03:9c:3a:00:1f:a7:3d:d5:eb:08:00 SRC=192.168.0.4 DST=192.168.0.3 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=25190 PROTO=TCP SPT=59154 DPT=9000 WINDOW=0 RES=0x00 RST URGP=0 
[43747.003785] [UFW BLOCK] IN=wlan0 OUT= MAC=00:16:ea:03:9c:3a:00:1f:a7:3d:d5:eb:08:00 SRC=192.168.0.4 DST=192.168.0.3 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=10602 PROTO=TCP SPT=59062 DPT=9000 WINDOW=0 RES=0x00 RST URGP=0

192.168.0.3 is my local computer.
192.168.0.4 in this case is the PS3.
port tcp port 9000 is what is used by twonky media server. The media server itself is working so all other communication is working fine.

Here's the output of my ufw status verbose

Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing)
New profiles: skip

To                         Action      From
--                         ------      ----
Anywhere                   ALLOW IN    192.168.0.0/24
22                         ALLOW IN    Anywhere
62552                      ALLOW IN    Anywhere

root@phillip-laptop:/home/hhomolka#

Just to be sure i didn't have any strange iptables rule that i didn't know of I reset both iptables and ufw to default with no rules and reconfigured just the default outgoing and incoming policies and the three rules listed above.

anyone have any ideas why this RST packet is being blocked?

---

### Post by ojconcentrate on 2010-08-30
same thing is happening with ACK packets 

[60215.002233] [UFW BLOCK] IN=wlan0 OUT= MAC=00:16:ea:03:9c:3a:00:1f:a7:3d:d5:eb:08:00 SRC=192.168.0.4 DST=192.168.0.3 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=27623 DF PROTO=TCP SPT=61847 DPT=9000 WINDOW=62804 RES=0x00 ACK URGP=0 
[60215.002300] [UFW BLOCK] IN=wlan0 OUT= MAC=00:16:ea:03:9c:3a:00:1f:a7:3d:d5:eb:08:00 SRC=192.168.0.4 DST=192.168.0.3 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=5896 DF PROTO=TCP SPT=61847 DPT=9000 WINDOW=65535 RES=0x00 ACK URGP=0 
[60215.002360] [UFW BLOCK] IN=wlan0 OUT= MAC=00:16:ea:03:9c:3a:00:1f:a7:3d:d5:eb:08:00 SRC=192.168.0.4 DST=192.168.0.3 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=6906 DF PROTO=TCP SPT=61847 DPT=9000 WINDOW=64252 RES=0x00 ACK URGP=0 
[60234.150629] [UFW BLOCK] IN=wlan0 OUT= MAC=00:16:ea:03:9c:3a:00:1f:a7:3d:d5:eb:08:00 SRC=192.168.0.4 DST=192.168.0.3 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=39385 DF PROTO=TCP SPT=61847 DPT=9000 WINDOW=65535 RES=0x00 ACK URGP=0 
[60255.311089] [UFW BLOCK] IN=wlan0 OUT= MAC=00:16:ea:03:9c:3a:00:1f:a7:3d:d5:eb:08:00 SRC=192.168.0.4 DST=192.168.0.3 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=47237 DF PROTO=TCP SPT=61847 DPT=9000 WINDOW=65535 RES=0x00 ACK URGP=0

---

### Post by ojconcentrate on 2010-08-31
bump. 
any ideas are much appreciated.

OJ

---

### Post by ojconcentrate on 2010-09-02
problem has been resolved. It turns out (best guest) that it resides with the PS3 DNLA client was sending packets which were classified as invalid which matched a rule before the allow rule on the network. 

see [http://www.linuxforums.org/forum/ubuntu-help/168888-solved-ufw-blocking-rst-ack-packets-when-rules-should-allow.html](http://www.linuxforums.org/forum/ubuntu-help/168888-solved-ufw-blocking-rst-ack-packets-when-rules-should-allow.html) for full details.

---

