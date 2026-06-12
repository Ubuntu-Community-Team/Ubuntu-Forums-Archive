---
title: "Micro$oft NIC Problem"
date: 2006-02-10
forum: Networking &amp; Wireless
---

### Post by uwhahn on 2006-02-10
I am having trouble with my NIC.
I just installed Ubuntu on an older machine I have, which contains a Microsoft brand NIC (:( ), which I'm not sure if it's even compatible.

I am fairly new to Linux and definitely new to configuring my own setup.

The short of it is I have no connectivity.

This is what I got:

>>lspci
...
0000:00:08.0 Ethernet Controller: Microsoft Corportation: unknown device 0002 (rev 11)

>>ifconfig
lo Link encap: Local Loopback
inet addr: 127.0.0.1 Mask: 255.0.0.0
inet6 addr:  ::1/128  Scope:Host
UP LOOKBACK RUNNING MTU:16436 Metric:1
RX packets:59940 errors:0 dropped:0 overruns:0 frame:0
TX packets:59940 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes4471907 (4.2 MiB) TX bytes4471907 (4.2 MiB)

Any help would be appreciated.

---

