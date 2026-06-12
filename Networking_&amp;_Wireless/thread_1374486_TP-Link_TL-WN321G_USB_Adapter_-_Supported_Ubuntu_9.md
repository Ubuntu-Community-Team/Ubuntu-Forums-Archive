---
title: "TP-Link TL-WN321G USB Adapter - Supported Ubuntu 9.10 100% Packet Injection Also"
date: 2010-01-06
forum: Networking &amp; Wireless
---

### Post by Project PWNED on 2010-01-06
As of Ubuntu 9.10, with kernel 2.6.31-17-generic, support works out of the box without an additional driver (the ASPj driver) and so does packet injection.


lsusb output:

> Bus 001 Device 002: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter

> root@pwnbuntu:~# aireplay-ng -9 mon0
21:36:39  Trying broadcast probe requests...
21:36:39  Injection is working!
21:36:41  Found 3 APs


$9 from Amazon.com, $15 something including shipping..

---

### Post by alcohol52 on 2010-05-22
Hey mine is not working in both karmic and lucid.
It is the same Device. 
Please check what modules you are using and please post.
I am getting a hell lot of headache getting it work.

---

