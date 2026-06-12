---
title: "Centrino(R) Wireless-N 1030 BGN High ping"
date: 2011-07-18
forum: Networking &amp; Wireless
---

### Post by Chilly_Willy on 2011-07-18
I have a new Dell Inspiron 15R (N5110) with a Centrino(R) Wireless-N 1030 BGN single band wireless card. The network connection is really flaky. I get some high pings.

I'm on 11.04 Natty.

```

PING 192.168.0.254 (192.168.0.254) 56(84) bytes of data.
64 bytes from 192.168.0.254: icmp_req=1 ttl=64 time=7.05 ms
64 bytes from 192.168.0.254: icmp_req=2 ttl=64 time=471 ms
64 bytes from 192.168.0.254: icmp_req=4 ttl=64 time=102 ms
64 bytes from 192.168.0.254: icmp_req=5 ttl=64 time=739 ms
64 bytes from 192.168.0.254: icmp_req=6 ttl=64 time=764 ms
64 bytes from 192.168.0.254: icmp_req=7 ttl=64 time=583 ms
64 bytes from 192.168.0.254: icmp_req=8 ttl=64 time=13.4 ms
64 bytes from 192.168.0.254: icmp_req=10 ttl=64 time=11.4 ms
64 bytes from 192.168.0.254: icmp_req=11 ttl=64 time=34.4 ms
64 bytes from 192.168.0.254: icmp_req=12 ttl=64 time=6.20 ms
64 bytes from 192.168.0.254: icmp_req=13 ttl=64 time=6.34 ms
64 bytes from 192.168.0.254: icmp_req=14 ttl=64 time=6.99 ms
64 bytes from 192.168.0.254: icmp_req=15 ttl=64 time=6.93 ms
64 bytes from 192.168.0.254: icmp_req=16 ttl=64 time=6.81 ms
^C
--- 192.168.0.254 ping statistics ---
16 packets transmitted, 14 received, 12% packet loss, time 15017ms
rtt min/avg/max/mdev = 6.208/197.175/764.020/287.952 ms

```

I've tried 2 different access points, both with the same symptons.

---

### Post by jmoorse on 2011-07-18
What does the output of iwconfig show?

Do you have any other wireless clients that use these access points from the same room/area that you can compare the ping latency to?

---

### Post by Chilly_Willy on 2011-07-18
I do have another laptop with an Intel 6300 wireless card, allso on 11.04 Natty and it word fine on both access points.

---

