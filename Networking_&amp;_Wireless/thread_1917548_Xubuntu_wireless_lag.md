---
title: "Xubuntu: wireless lag"
date: 2012-01-30
forum: Networking &amp; Wireless
---

### Post by isebarn on 2012-01-30
My wi-fi is lagging, 80% of the time its useless, cant connect to anything and then the next minute its fine

---

### Post by nothingspecial on 2012-01-30
*Thread moved to **Networking & Wireless**.*

Post your wireless card. Open a terminal and paste

```
sudo lshw -C network
```

Then paste the output back here.

---

### Post by isebarn on 2012-01-30
*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: 60:eb:69:96:2f:66
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:bc00(size=256) memory:d0200000-d0200fff memory:d0000000-d0003fff memory:d0020000-d003ffff
  *-network
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 01
       serial: c0:cb:38:68:91:d3
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.0.0-15-generic firmware=N/A ip=192.168.1.36 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:c000(size=256) memory:d0600000-d0603fff

---

### Post by isebarn on 2012-01-30
> **nothingspecial said:**
> *Thread moved to **Networking & Wireless**.*

Post your wireless card. Open a terminal and paste

```
sudo lshw -C network
```

Then paste the output back here.

*-network 
description: Ethernet interface
product: RTL8111/8168B PCI Express Gigabit Ethernet controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: 03
serial: 60:eb:69:96:2f:66
size: 10Mbit/s
capacity: 1Gbit/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
resources: irq:42 ioport:bc00(size=256) memory:d0200000-d0200fff memory:d0000000-d0003fff memory:d0020000-d003ffff
*-network
description: Wireless interface
product: RTL8188CE 802.11b/g/n WiFi Adapter
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:08:00.0
logical name: wlan0
version: 01
serial: c0:cb:38:68:91:d3
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=rtl8192ce driverversion=3.0.0-15-generic firmware=N/A ip=192.168.1.36 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
resources: irq:17 ioport:c000(size=256) memory:d0600000-d0603fff

---

