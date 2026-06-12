---
title: "High packet loss when using wireless network"
date: 2012-06-14
forum: Networking &amp; Wireless
---

### Post by TubeZ on 2012-06-14
Here's an attempt to ping my router; I'm utilizing a linksys WMP300N wireless network card, and am running ndiswrapper to utilize the drivers. Ubuntu 12.04, I'm fairly new to linux, by the way.
[U]```
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_req=2 ttl=64 time=941 ms
64 bytes from 192.168.1.1: icmp_req=6 ttl=64 time=917 ms
64 bytes from 192.168.1.1: icmp_req=7 ttl=64 time=0.966 ms
64 bytes from 192.168.1.1: icmp_req=8 ttl=64 time=0.971 ms
64 bytes from 192.168.1.1: icmp_req=15 ttl=64 time=69.9 ms
^C
--- 192.168.1.1 ping statistics ---
17 packets transmitted, 5 received, 70% packet loss, time 16088ms
rtt min/avg/max/mdev = 0.966/386.344/941.923/444.611 ms
```
[/U]

---

