---
title: "Ubuntu 12.10 with BCM4321 works, except with N routers"
date: 2013-01-13
forum: Networking &amp; Wireless
---

### Post by Maladju on 2013-01-13
I'm running Ubuntu 12.10 and am new to Linux. I have a wireless card that is working via b43, but will not work with STA, wl, or b43-lpphy. I am attempting some network streaming from this machine to another over the network, and the b/g router & modem isn't cutting it. I have an N router that I would prefer to use.

My wan0 will connect to the 2wire b/g router with no issues. I can see my N router, but cannot connect - the connection symbol on the top continues to cycle until it simply says that I am disconnected.

I have run an lshw -C network
```
*-network
       description: Network controller
       product: BCM4321 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:20 memory:f9bfc000-f9bfffff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:23:69:73:a4:7c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.5.0-21-generic firmware=666.2 ip=192.168.1.66 link=yes multicast=yes wireless=IEEE 802.11bg

```

I just noticed that under my Wireless interface information, it does list wireless as only bg. I know my card supports N. Any assistance would be greatly appreciated.

---

