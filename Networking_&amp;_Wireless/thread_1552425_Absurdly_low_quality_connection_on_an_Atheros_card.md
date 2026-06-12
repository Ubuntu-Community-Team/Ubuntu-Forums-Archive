---
title: "Absurdly low quality connection on an Atheros card"
date: 2010-08-13
forum: Networking &amp; Wireless
---

### Post by Birion on 2010-08-13
Well, apparently I'm not to have a working wifi without problems on my new computer. I have it already set up in its new place, but the wireless connection (to a router that's ~5 metres away) is incredibly strange - the signal strength is ~50% and the speed moves from 18 Mb/s to 1 Mb/s (i.e., it just pretends it's connected).

Compared to that, my netbook with a Broadcom card, which is about 20 cm away from the main computer, is running at 54 Mb/s (the max speed of the router) and 100% signal strength.

lspci

```
Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
```

lshw

```
*-network
     description: Wireless interface
     product: AR9285 Wireless Network Adapter (PCI-Express)
     vendor: Atheros Communications Inc.
     physical id: 0
     bus info: pxi@0000:04:00.0
     logical name: wlan0
     version: 01
     serial: 00:25:d3:e0:6a:f1
     width: 64 bits
     clock: 33MHz
     capabilities: bus_master cap_list ethernet physical wireless
     configuration: broadcast=yes driver=athk9k ip=10.0.0.4 latency=0 multicast=yes wireless=IEEE 802.11bgn
     resources: irq:19 memory:febf0000-febfffff
```

---

### Post by Birion on 2010-08-14
Anyone?

---

