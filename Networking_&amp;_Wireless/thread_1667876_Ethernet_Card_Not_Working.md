---
title: "Ethernet Card Not Working"
date: 2011-01-15
forum: Networking &amp; Wireless
---

### Post by kurtzy317 on 2011-01-15
Recently I reinstalled my ethernet card and it has not been working.  The lights on it and my switch light up but it doesn't connect. Here is the output of lshw:

```
 *-network:0 UNCLAIMED
                description: Ethernet controller
                product: Cirrus Logic
                vendor: Cirrus Logic
                physical id: 8
                bus info: pci@0000:01:08.0
                version: 10
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=2 maxlatency=64 mingnt=32
                resources: ioport:1800(size=512) memory:40010000-400101ff
```As you can see there is no logical name which I think is the problem but have no idea how to assign it one.

Thanks in advance.

---

