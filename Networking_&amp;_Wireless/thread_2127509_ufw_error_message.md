---
title: "ufw error message"
date: 2013-03-20
forum: Networking &amp; Wireless
---

### Post by M0pax on 2013-03-20
Hi I am running server 12.10
In the kern log and syslog i am getting this mesage every 2 mins
is this a problem?


Mar 20 11:53:07 "server name" kernel: [10700.399786] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:90:01:3b:97:de:18:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2

---

### Post by albandy on 2013-03-20
Not a problem, ufw is blocking multicast and usually this is right.

---

### Post by M0pax on 2013-03-20
hi albandy thanks for that

---

