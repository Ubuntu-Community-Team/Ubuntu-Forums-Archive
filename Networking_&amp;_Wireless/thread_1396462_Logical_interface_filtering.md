---
title: "Logical interface filtering"
date: 2010-02-02
forum: Networking &amp; Wireless
---

### Post by mdewet on 2010-02-02
Hi All,

Ubuntu Server 9.04

I have created 2 logical eth interfaces (eth0:1, eth0:2) on my physical interface (eth0).  It was my understanding that by assigning the logical interfaces to another network, only the traffic destined for that network would reach the logical interface.

As it turns out, a tcpdump on all three interfaces (eth0, eth0:1, eth0:2) now shows the same traffic regardless of the packet's destination network.

Is this normal behaviour for logical interfaces? Is there a way to configure the kernel to forward only the appropriate traffic to the logical interfaces?

Regards,
MdW

---

