---
title: "Default network connection"
date: 2012-02-09
forum: Networking &amp; Wireless
---

### Post by lpc921 on 2012-02-09
How to change default network connection if I have multiple network adaptors on Ubuntu 11.10?

Output of netstat -rn
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG        0 0          0 eth0
10.0.0.0        0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 wlan0
172.24.0.0      0.0.0.0         255.255.192.0   U         0 0          0 wlan0
```

Output of route
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
```
Then hangs

---

### Post by lpc921 on 2012-02-10
I installed firestarter and choose my wireless connection to be the Internet connected device and the wired connection to be the local network connected device. By I still don't have Internet when both wired and wireless are connected.

---

