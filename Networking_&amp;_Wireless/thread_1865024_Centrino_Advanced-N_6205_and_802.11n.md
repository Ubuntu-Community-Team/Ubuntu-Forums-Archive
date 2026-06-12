---
title: "Centrino Advanced-N 6205 and 802.11n"
date: 2011-10-19
forum: Networking &amp; Wireless
---

### Post by Chuwbacca on 2011-10-19
Hi all!

It is possible to get 11n on 6205 wifi card? I have Dell 6420 laptop, and in ubuntu natty (11.04) i got only 802.11abg, not 11n... How i can enable 11n?

I was used 2.6.38 kernel, 3.0.7 and 3.1rc9 (case kernel panic in wlan module) and still no 11n... modprobe iwlagn 11n_disable=0 not work too...

```
lshw
           *-network
                description: Wireless interface
                product: Centrino Advanced-N 6205
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 34
                serial: a0:88:b4:19:72:84
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn driverversion=3.0.7-030007-generic firmware=17.168.5.2 build 35905 ip=192.168.1.2 latency=0 multicast=yes **wireless=IEEE 802.11abg**
```

---

