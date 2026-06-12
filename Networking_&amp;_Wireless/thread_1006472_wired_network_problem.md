---
title: "wired network problem"
date: 2008-12-09
forum: Networking &amp; Wireless
---

### Post by radiobot on 2008-12-09
i got a weird network problem:
wireless works well, problem is wired.
if i connect my laptop to the network at office after the comet spinning icon says that " the network connection has been disconnected"
but if i connect take my laptop home and connect by wire to the router, it connects!
i've configured manually ip, mask, gateway, but no connection

heres config

ath0
Link encap:Ethernet HWaddr 00:11:50:d9:20:bd
inet6 addr: fe80::211:50ff:fed9:20bd/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

eth0
Link encap:Ethernet HWaddr 00:0d:56:b2:73:c5
inet6 addr: fe80::20d:56ff:feb2:73c5/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:8028 errors:0 dropped:0 overruns:0 frame:0
TX packets:83 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:651107 (651.1 KB) TX bytes:20749 (20.7 KB)
Interrupt:7

lo
Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:366 errors:0 dropped:0 overruns:0 frame:0
TX packets:366 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:31316 (31.3 KB) TX bytes:31316 (31.3 KB)

wifi0
Link encap:UNSPEC HWaddr 00-11-50-D9-20-BD-00-00-00-00-00-00-00-00-00-00
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:524 errors:0 dropped:0 overruns:0 frame:47332
TX packets:349 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:199
RX bytes:41368 (41.3 KB) TX bytes:16054 (16.0 KB)
Interrupt:11

hope somebody can help me, thanks!! in advance

---

### Post by cariboo on 2008-12-09
How  did you set the ip address for eth0, as from your listing, eth0 doesn't have an ip address. Could paste the output of:

```
cat /etc/network/interfaces
```

in your next post. The above command must be run in a Applications-->Accessories-->Terminal.

Jim

---

