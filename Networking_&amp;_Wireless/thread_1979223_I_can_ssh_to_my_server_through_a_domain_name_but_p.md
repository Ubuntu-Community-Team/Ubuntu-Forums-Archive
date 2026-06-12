---
title: "I can ssh to my server through a domain name but ping is broken"
date: 2012-05-13
forum: Networking &amp; Wireless
---

### Post by sirspazzolot on 2012-05-13
I can ssh to [mydomain].com (not just my local network) but I can't ping or do anything internet-y from it. ifconfig shows that the server is connected
```
matt@mattserver:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:25:86:b6
          inet addr:192.168.1.108  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe25:86b6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:54 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:6493 (6.4 KB)  TX bytes:6947 (6.9 KB)
          Interrupt:16 Base address:0x3000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2548 (2.5 KB)  TX bytes:2548 (2.5 KB)
```

ping gets unknown host.

ehhh?

---

