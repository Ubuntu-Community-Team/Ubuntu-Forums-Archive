---
title: "OpenDNS or ???"
date: 2010-11-25
forum: Networking &amp; Wireless
---

### Post by Xinerama on 2010-11-25
So, I'm trying out OpenDNS and when I run traceroute this is what I get

```

root@elias-desktop:/home/Desktop# traceroute 208.67.222.222
traceroute to 208.67.222.222 (208.67.222.222), 30 hops max, 60 byte packets
 1  192.168.1.1 (192.168.1.1)  15.419 ms  15.429 ms  15.442 ms
 2  59.14.0.254 (59.14.0.254)  17.384 ms  17.389 ms  17.393 ms
 3  211.226.36.57 (211.226.36.57)  17.387 ms  17.396 ms  17.397 ms
 4  59.14.0.253 (59.14.0.253)  19.681 ms  19.692 ms  19.694 ms
 5  221.150.170.29 (221.150.170.29)  20.567 ms  20.579 ms  21.102 ms
 6  125.130.3.77 (125.130.3.77)  22.881 ms  10.533 ms  16.550 ms
 7  220.73.149.121 (220.73.149.121)  16.545 ms  16.539 ms  16.547 ms
 8  112.174.82.106 (112.174.82.106)  16.546 ms  16.550 ms  19.029 ms
 9  112.174.84.138 (112.174.84.138)  20.143 ms  20.155 ms  20.153 ms
10  203.234.255.182 (203.234.255.182)  139.595 ms  140.818 ms  141.356 ms
11  as-1.r02.sngpsi02.sg.bb.gin.ntt.net (129.250.5.21)  212.829 ms  212.837 ms  228.735 ms
12  116.51.17.210 (116.51.17.210)  232.534 ms  219.017 ms  219.905 ms

```

and with my regular ISP's DNS server
```

root@elias-desktop:/home/Desktop# traceroute 168.126.63.1
traceroute to 168.126.63.1 (168.126.63.1), 30 hops max, 60 byte packets
 1  192.168.1.1 (192.168.1.1)  16.905 ms  16.920 ms  16.937 ms
 2  59.14.0.254 (59.14.0.254)  19.520 ms  19.533 ms  19.538 ms
 3  211.226.36.57 (211.226.36.57)  19.535 ms  19.542 ms  19.547 ms
 4  59.14.0.253 (59.14.0.253)  19.561 ms  19.566 ms  21.250 ms
 5  221.150.170.25 (221.150.170.25)  22.140 ms  22.155 ms  22.686 ms
 6  125.130.3.73 (125.130.3.73)  24.214 ms  10.551 ms  15.623 ms

```

Typically "less" is more right?? So, if my hop count is lower then my surfing is going to be faster. Right?
What's another way that can I can test this?
Wireshark?

Is anyone using OpenDNS?  What're your thoughts?

---

