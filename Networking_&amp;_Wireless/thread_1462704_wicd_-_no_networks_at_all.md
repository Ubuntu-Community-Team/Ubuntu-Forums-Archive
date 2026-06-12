---
title: "wicd - no networks at all"
date: 2010-04-26
forum: Networking &amp; Wireless
---

### Post by mathfreak123 on 2010-04-26
I installed wicd today over network-manager. As the title suggests, wicd can't detect any networks. I checked ifconfig, made sure wlan0 was up, clicked refresh several times, etc.

Nothing seems to work to get wicd to pick up on a wireless network.

It's not a big deal for now, since I switched back to NetworkManager, but I'm planning on trying out the LXDE with Ubuntu 10.04 when it comes out, and I know LXDE uses wicd, so I'm wondering if I can get this issues resolved on my side before I try Lubuntu. :D

EDIT: Almost forgot about my wireless card info: 

Intel Corporation PRO/Wireless 3945ABG
```

description: Wireless interface
                product: PRO/Wireless 3945ABG [Golan] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: wmaster0
                version: 02
                serial: 00:1f:3c:0e:6a:41
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 ip=192.168.1.65 latency=0 multicast=yes wireless=IEEE 802.11abg
                resources: irq:33 memory:c0100000-c0100fff

```
Ubuntu Karmic 9.10

EDIT: NetworkManager works fine in Lubuntu Lucid. :D

---

