---
title: "Web adress wont work."
date: 2010-04-03
forum: Networking &amp; Wireless
---

### Post by AlexEttels on 2010-04-03
I cant access a website by tid web adress, only by its ip ardess.
im using firefox and ubunto 9.10;
thanks for your help

---

### Post by Iowan on 2010-04-04
Those symptoms ordinarily point to DNS problem. What's in */etc/resolv.conf*? As a side comment/question: DHCP clients ordinarily get nameserver information from the DHCP server. Does the machine get a DHCP address - or is it manually configured (either via Network Manager or */etc/network/interfaces)?*

Is it only one website that has a problem?

---

