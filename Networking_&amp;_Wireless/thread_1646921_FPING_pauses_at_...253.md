---
title: "FPING pauses at *.*.*.253"
date: 2010-12-16
forum: Networking &amp; Wireless
---

### Post by tjsullivan1 on 2010-12-16
Hi All:

I have a script that I am trying to speed up that invokes fping several times to gather live (responding to ping) and dead (not responding to ping) IPs. I have noticed that when I run fping manually it will take about ten seconds for it to scan a subnet (192.168.1.0/24); however it will then pause at 192.168.1.253 for about five to six seconds. This wouldn't make a big difference, except I scan fifty subnets everytime I run this script (meaning that 250 seconds appears to be wasted).

Does anyone know what might be causing this? The actual command I run is /usr/local/sbin/fping -a -g 192.168.1.0/24 -r1. The OS is RHEL 5. fping is version 2.4b2

Thanks in advance.

---

