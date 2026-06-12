---
title: "Network is unreachable"
date: 2010-04-24
forum: Networking &amp; Wireless
---

### Post by Karnie86 on 2010-04-24
running ubuntu 9.04, internet randomly stopped working last night and i'm not clever enough to figure out the problem. I cant even log into my router so i think there's something wrong with my ethernet (i use a wired connection)
 
```

john@elric:~$ ifconfig
eth0    Link encap:Ethernet  HWaddr 00:26:18:44:b4:58
          inet6 addr: fe80::226:18ff:fe44:b458/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:260 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:30632 (30.6 KB)  TX bytes:3546 (3.5 KB)
          Interrupt:251
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:284 errors:0 dropped:0 overruns:0 frame:0
          TX packets:284 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:21572 (21.5 KB)  TX bytes:21572 (21.5 KB)

```
 
any suggestions?
 
btw the network is fine. My computer is dual-booted with windows 7 (64-bit) and that can connect no problem, as can all the other machines on the network.

---

### Post by Iowan on 2010-04-24
One quick/dirty... From a terminal, try:
```
dhclient eth0
```

---

