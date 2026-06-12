---
title: "Ubuntu routing problems"
date: 2005-03-15
forum: Networking &amp; Wireless
---

### Post by dcorreal on 2005-03-15
Hi

I 'd like to use my ubuntu like a router.   I has two networkcards, one has a public IP and the other one is configured with 192.168.1.1

When the two network cards are active, the network doesn't work, that means, I can not make ping to the gateway, My Browser doesn't work and the dig command responds nothing.  This is my ifconfig -a 

eth0      Link encap:Ethernet  HWaddr 00:08:54:24:15:F3
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:54ff:fe24:15f3/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:129 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:8120 (7.9 KiB)
          Interrupt:169 Base address:0xde00

eth1      Link encap:Ethernet  HWaddr 00:0D:56:02:69:0A
          inet addr:157.253.45.21  Bcast:157.253.45.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:fe02:690a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:512177 errors:0 dropped:0 overruns:0 frame:0
          TX packets:693673 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:41952657 (40.0 MiB)  TX bytes:969038153 (924.1 MiB)
          Base address:0xddc0 Memory:feae0000-feb00000

and this is my route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
157.253.45.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
0.0.0.0         157.253.45.1    0.0.0.0         UG    0      0        0 eth1

If I stop eth0, everything works fine again.

Is there something that I am missing in order to install a router, some aditional package or configuration? Is there a HowTo that explains step by step how to setup an Ubuntu box like a router.

Tanks in advance

---

### Post by alastair on 2005-03-15
No - with both active you have TWO default routes i.e.

0.0.0.0 192.168.1.1 0.0.0.0 UG 0 0 0 eth0
0.0.0.0 157.253.45.1 0.0.0.0 UG 0 0 0 eth1

A wireless interface can cause this as well.

Delete one of these e.g. the eth0 one I assume (private).

---

