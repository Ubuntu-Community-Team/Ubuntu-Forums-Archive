---
title: "Network manager no network devices available"
date: 2011-03-26
forum: Networking &amp; Wireless
---

### Post by RobotGymnast on 2011-03-26
I installed a minimal Ubuntu build, and then NetworkManager. When I run it, though, I get a "no network devices available" message. Any help?

---

### Post by conneco on 2011-03-26
network manager wont monitor devices that are in ```
etc/network/interfaces
``` check the file if its got anything in there?

also what does this show

```
lshw -C network
```

---

### Post by RobotGymnast on 2011-03-26
> **conneco said:**
> network manager wont monitor devices that are in ```
etc/network/interfaces
``` check the file if its got anything in there?


```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```

> **conneco said:**
> 
also what does this show

```
lshw -C network
```

```
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:19 memory:f4000000-f4003fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:b1:62:95
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.19 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:44 ioport:5000(size=256) memory:f8610000-f8610fff memory:f8600000-f860ffff memory:f8620000-f862ffff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:22:69:3f:34:46
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-28-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

```

---

### Post by TBABill on 2011-03-26
Probably the b43-pci-bridge driver. The BCM4312 LP (low power) is not supported well by the b43 (or at all?). You should be running the wl driver, also called the STA, and instructions are all over the forums for doing so.

---

### Post by RobotGymnast on 2011-03-26
> **TBABill said:**
> Probably the b43-pci-bridge driver. The BCM4312 LP (low power) is not supported well by the b43 (or at all?). You should be running the wl driver, also called the STA, and instructions are all over the forums for doing so.

Strange, with a normal ubuntu install, the LP driver worked great.

---

