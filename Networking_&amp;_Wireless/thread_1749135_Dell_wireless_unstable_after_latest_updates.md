---
title: "Dell wireless unstable after latest updates"
date: 2011-05-04
forum: Networking &amp; Wireless
---

### Post by onebir on 2011-05-04
I'm using Ubuntu 10.04 on a Dell Inspiron 640m (Wireless: Intel PRO/Wireless 3945ABG [Golan] Network Connection, Ethernet: Broadcom BCM4401-B0 100Base-TX, output from sudo lshw -C network below.)

This morning, the wireless connection, has gone down repeatedly, and signal strength looks a bit weaker. There was a period in January when there were similar problems that then improved. Seems like a recent system (perhaps this morning/yesterday) update broke something.

```
onebir@onebir-laptop:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 02
       serial: 00:13:02:a8:81:4a
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=10.0.0.2 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:27 memory:dfdff000-dfdfffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:af:b7:b3
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: irq:17 memory:df9fe000-df9fffff
```

---

