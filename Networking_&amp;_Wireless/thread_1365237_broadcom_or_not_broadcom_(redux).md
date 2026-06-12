---
title: "broadcom or not broadcom (redux)"
date: 2009-12-27
forum: Networking &amp; Wireless
---

### Post by martinshort on 2009-12-27
hi all... i had this broadcome post on the general section but figured this is the right place to post this.

little background... i just put ubuntu on this hp mini and initially the wireless card wasn't hooked up. the b43 and ssb modules weren't doing much. i was kinda surprised cause a distribution such as ubuntu should have all these covered. so i looked around and got the broadcom linux driver - wl module - from their website and following the instructions in their readme build it and installed it (btw, getting a bit bored with this sudo thing). it seemed to work. and kinda does. except it drops about a forth of the packets that go through it. here below is a ping from that machine to the access point it is directly hooked up to. i have 2 other bsd machines here hooked up to the same wireless access point and there are no dropouts there. 

hopefully somebody can explain how to improve this situation. thanks...
....................................................
64 bytes from 192.168.1.1: icmp_seq=123 ttl=150 time=4.73 ms
64 bytes from 192.168.1.1: icmp_seq=124 ttl=150 time=211 ms
64 bytes from 192.168.1.1: icmp_seq=125 ttl=150 time=2.59 ms
64 bytes from 192.168.1.1: icmp_seq=126 ttl=150 time=4.12 ms
64 bytes from 192.168.1.1: icmp_seq=129 ttl=150 time=3.38 ms
64 bytes from 192.168.1.1: icmp_seq=130 ttl=150 time=94.9 ms
64 bytes from 192.168.1.1: icmp_seq=131 ttl=150 time=65.3 ms
64 bytes from 192.168.1.1: icmp_seq=132 ttl=150 time=4.49 ms
64 bytes from 192.168.1.1: icmp_seq=133 ttl=150 time=5.00 ms
64 bytes from 192.168.1.1: icmp_seq=134 ttl=150 time=4.69 ms
64 bytes from 192.168.1.1: icmp_seq=135 ttl=150 time=4.64 ms
64 bytes from 192.168.1.1: icmp_seq=136 ttl=150 time=6.15 ms
64 bytes from 192.168.1.1: icmp_seq=137 ttl=150 time=2.79 ms
64 bytes from 192.168.1.1: icmp_seq=138 ttl=150 time=6.54 ms
64 bytes from 192.168.1.1: icmp_seq=140 ttl=150 time=5.49 ms
64 bytes from 192.168.1.1: icmp_seq=141 ttl=150 time=4.60 ms
64 bytes from 192.168.1.1: icmp_seq=143 ttl=150 time=4.76 ms
64 bytes from 192.168.1.1: icmp_seq=144 ttl=150 time=5.99 ms
64 bytes from 192.168.1.1: icmp_seq=145 ttl=150 time=7.01 ms
64 bytes from 192.168.1.1: icmp_seq=148 ttl=150 time=3.63 ms
64 bytes from 192.168.1.1: icmp_seq=149 ttl=150 time=3.72 ms
64 bytes from 192.168.1.1: icmp_seq=152 ttl=150 time=12.1 ms
64 bytes from 192.168.1.1: icmp_seq=153 ttl=150 time=3.74 ms
64 bytes from 192.168.1.1: icmp_seq=155 ttl=150 time=43.4 ms
64 bytes from 192.168.1.1: icmp_seq=156 ttl=150 time=6.85 ms
64 bytes from 192.168.1.1: icmp_seq=157 ttl=150 time=4.09 ms
..................................................................................
--- 192.168.1.1 ping statistics ---
157 packets transmitted, 111 received, 29% packet loss, time 156362ms
rtt min/avg/max/mdev = 2.008/14.514/211.636/34.038 ms



[B]edit: while i was writing this i was running a ping too. here are the fresh results:

--- 192.168.1.1 ping statistics ---
607 packets transmitted, 377 received, 37% packet loss, time 607593ms
rtt min/avg/max/mdev = 2.007/7.817/160.593/12.842 ms
[/B]

---

