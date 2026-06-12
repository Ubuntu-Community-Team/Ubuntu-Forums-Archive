---
title: "hack attack from 192.169.0.1 ?"
date: 2011-02-10
forum: Networking &amp; Wireless
---

### Post by Jethro_uk on 2011-02-10
looking in firewall logs, I notice the following line a few times:

> Time:Feb  7 14:41:03 Direction: Unknown In:wlan0 Out: Port:1900 Source:192.168.0.1 Destination:239.255.255.250 Length:161 TOS:0x00 Protocol:UDP Service:SSDP

Now I have 2 network cards in the machine. One on a 192.168.1.0/24 network, and one on a 192.168.9.0/24 network.

So where are these 192.168.0.1 messages coming from ?

Anything I need to be worried about ?

---

### Post by perspectoff on 2011-02-10
Do you have any routers on your network using 192.168.0.1?

---

### Post by Jethro_uk on 2011-02-10
> **perspectoff said:**
> Do you have any routers on your network using 192.168.0.1?

No. I have routers on 192.168.1.1, 192.168.9.1, and 192.168.2.1

---

### Post by Jethro_uk on 2011-02-10
DING !

My sons PC is on 192.168.9.x and has 2 network cards ... the other is 192.168.0.x which is required for Windows ICS - the whole reason I steered away from 192.168.0.0/24 on Ubuntu in the first place.

Looks like when it starts up, it's doing some sort of SSDP request all over the network.

---

### Post by kistenyer on 2011-02-10
[www.grc.com/port_1900.htm]("http://www.grc.com/port_1900.htm")

Up is some useful information about the package.

:popcorn:

---

