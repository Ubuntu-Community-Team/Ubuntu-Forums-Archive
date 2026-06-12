---
title: "Internet sharing still isn't working :P"
date: 2006-06-11
forum: Networking &amp; Wireless
---

### Post by kingedwin on 2006-06-11
I have two computers, each with wireless cards.  I have set them up as an ad-hoc network, and I've installed Firestarter, telling it to allow sharing of my internet connection, which is hooked to an ethernet card.

I can use the internet on the computer that it is directly connected to.

I can ping the computer through it's wireless address: 222.222.222.0.  It is set up as a static network.  The gateway IP for both is 222.222.222.225.

But I still can't use the internet on the computer that isn't connected directly to the internet.  Why am I having this problem, and how can I fix it?

---

### Post by kingedwin on 2006-06-11
ifconfig from computer with internet connection:

eth0      Link encap:Ethernet  HWaddr 00:07:E9:49:0C:C2
          inet addr:206.246.5.28  Bcast:206.246.5.255  Mask:255.255.255.0
          inet6 addr: fe80::207:e9ff:fe49:cc2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7227 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6273 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:5242771 (4.9 MiB)  TX bytes:989557 (966.3 KiB)
          Base address:0xac00 Memory:ff7e0000-ff800000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2412 (2.3 KiB)  TX bytes:2412 (2.3 KiB)

ra0       Link encap:Ethernet  HWaddr 00:16:B6:5C:F0:57
          inet addr:222.222.222.0  Bcast:222.222.222.255  Mask:255.255.255.0
          inet6 addr: fe80::216:b6ff:fe5c:f057/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1319 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12133 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:64624 (63.1 KiB)  TX bytes:0 (0.0 b)
          Interrupt:201

--

I've been working on this for almost a week, and all I've been able to do is get the wireless connection working.  What am I doing wrong?

---

