---
title: "Network not working, OK in Windows, Intel845 mainboard"
date: 2011-05-25
forum: Networking &amp; Wireless
---

### Post by 01jack on 2011-05-25
Installed Natty on an old PC built around an Intel 845GLAD mainboard with built-in (wired) nic. Dual boot: in Windows networking works fine, no go in Ubuntu.

```
ifconfig -a
ubuntu@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:07:e9:f3:d7:3d  
          inet6 addr: fe80::207:e9ff:fef3:d73d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1317 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:389835 (389.8 KB)  TX bytes:8242 (8.2 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1442 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1442 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:110988 (110.9 KB)  TX bytes:110988 (110.9 KB)
```

In System-Administration-Network Tools, I can see "Received packets:" steadily incrementing a about 2 per second.

---

