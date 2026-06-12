---
title: "show bytes received, how much have I downloaded?"
date: 2009-06-06
forum: Networking &amp; Wireless
---

### Post by hachel on 2009-06-06
hi

how can I see how much bytes have been received during the active session?
I've seen conky do it and apparently it just uses available information provided by the system.

thanks

---

### Post by Brandon Williams on 2009-06-06
You can do this with ifconfig. Here's some sample output:
```
$ ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:21:63:bf:ef:89  
          inet addr:192.168.1.28  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:63ff:febf:ef89/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16804 errors:0 dropped:0 overruns:0 frame:37526
          TX packets:8411 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9315972 (9.3 MB)  TX bytes:1348303 (1.3 MB)
          Interrupt:17 
```
The info is available in a way that's easier to parse but not as readable in /proc/net/dev:
```
$ cat /proc/net/dev
Inter-|   Receive                                                |  Transmit
 face |bytes    packets errs drop fifo frame compressed multicast|bytes    packets errs drop fifo colls carrier compressed
    lo:  115295     897    0    0    0     0          0         0   115295     897    0    0    0     0       0          0
  eth0:       0       0    0    0    0     0          0         0        0       0    0    0    0     0       0          0
  eth1: 9347221   17192    0    0    0 38355          0         0  1356142    8464    6    0    0     0       0          0
```

---

