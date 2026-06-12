---
title: "Dual Nic Facing Internet"
date: 2013-02-26
forum: Networking &amp; Wireless
---

### Post by jmazaredo on 2013-02-26
I have a problem configuring dual nic on linux that both facing the internet different isp.  As on my understanding I can only use one gateway.

---

### Post by albandy on 2013-02-26
> **jmazaredo said:**
> I have a problem configuring dual nic on linux that both facing the internet different isp.  As on my understanding I can only use one gateway.

Yes and no. You can use two default gateways defining the priority.
For example:

sudo route add default gw 192.168.1.1 metric 1
sudo route add default gw 192.168.1.2 metric 2

---

