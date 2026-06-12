---
title: "Huge ping times with 3945abg"
date: 2009-03-18
forum: Networking &amp; Wireless
---

### Post by ogcub on 2009-03-18
Sometimes I start to get huge ping times to my wireless router, which normally are about 2 ms.
```
ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=230 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=255 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=153 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=237 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=64 time=666 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=64 time=1233 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=64 time=1940 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=64 time=2215 ms
64 bytes from 192.168.1.1: icmp_seq=10 ttl=64 time=2934 ms
64 bytes from 192.168.1.1: icmp_seq=11 ttl=64 time=3025 ms
64 bytes from 192.168.1.1: icmp_seq=12 ttl=64 time=3248 ms
64 bytes from 192.168.1.1: icmp_seq=13 ttl=64 time=2936 ms
64 bytes from 192.168.1.1: icmp_seq=14 ttl=64 time=2500 ms
64 bytes from 192.168.1.1: icmp_seq=15 ttl=64 time=2363 ms
64 bytes from 192.168.1.1: icmp_seq=16 ttl=64 time=1958 ms
64 bytes from 192.168.1.1: icmp_seq=17 ttl=64 time=1626 ms
^C
--- 192.168.1.1 ping statistics ---
20 packets transmitted, 16 received, 20% packet loss, time 19067ms
rtt min/avg/max/mdev = 153.748/1720.516/3248.929/1082.284 ms, pipe 4

```

I am using 3945abg wireless card, restarting router doesn't solve problem, restarting computer usually does. Sometimes closing transmission with also brings everything back, but not always. Most of the time problem solves automatically after some time.

Thanks for helping :)

---

