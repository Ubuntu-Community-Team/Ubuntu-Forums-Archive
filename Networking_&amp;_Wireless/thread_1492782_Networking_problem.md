---
title: "Networking problem"
date: 2010-05-25
forum: Networking &amp; Wireless
---

### Post by gamulz on 2010-05-25
[[IMG]http://img541.imageshack.us/img541/4683/drawing2y.jpg[/IMG]]("http://img541.imageshack.us/i/drawing2y.jpg/")

Uploaded with [ImageShack.us]("http://imageshack.us")

I'am sorry, i can't write english well,

I have problem with my network,

**From 192.168.0.1 (Ubuntu Server)**
ping to 192.168.0.11 is rto
ping to 192.168.0.10 is rto
ping to 192.168.0.40 is reply <<< (notebook with Wireless & DHCP)
ping to 192.168.0.20 is rto
ping to 192.168.0.21 is rto
ping to 192.168.0.41 is reply <<< (notebook with Wireless & DHCP)
ping to 192.168.0.30 is rto
ping to 192.168.0.31 is rto
ping to 192.168.0.12 is reply <<< (Wireless Acces Point)
ping to 192.168.0.22 is reply <<< (Wireless Acces Point)
ping to 192.168.1.1 is reply
 ping to internet is reply

**From 192.168.0.11 (workstation)**
ping to 192.168.0.1 is rto
ping to 192.168.0.10, 20, 21, 30, 31, 12, 22, 40, 41 is reply
ping to 192.168.1.1 is rto
 ping to internet is rto

**From 192.168.0.20 (workstation)**
ping to 192.168.0.1 is rto
ping to 192.168.0.10, 11, 21, 30, 31, 12, 22, 40, 41 is reply
ping to 192.168.1.1 is rto
  ping to internet is rto

**From 192.168.0.30 (workstation)**
 ping to 192.168.0.1 is rto
 ping to 192.168.0.10, 11, 21, 20, 31, 12, 22, 40, 41 is reply
ping to 192.168.1.1 is rto
   ping to internet is rto

**From 192.168.0.40 ****(workstation >> notebook - DHCP)**
  ping to 192.168.0.1 is reply
  ping to 192.168.0.10, 11, 21, 20, 31, 12, 22, 30, 41 is reply
ping to 192.168.1.1 is reply
ping to internet is reply
[B]
From 192.168.0.41 (workstation >> notebook - DHCP)[/B]
   ping to 192.168.0.1 is reply
   ping to 192.168.0.10, 11, 21, 20, 31, 12, 22, 30, 40 is reply
ping to 192.168.1.1 is reply
ping to internet is reply

Help me please , i'am very confused...:confused:

I'm sorry, my english is bad :P:P:P

---

### Post by Iowan on 2010-05-25
rto = no response (timed out)?

---

### Post by gamulz on 2010-05-26
> **Iowan said:**
> rto = no response (timed out)?


Yup, RTO = Request Timed Out

---

### Post by Iowan on 2010-05-26
Aside from those noted as DHCP, the addresses are static?
What is result (from a terminal) of **route -n** both on the server and  one of the (non-DHCP) workstations?

---

