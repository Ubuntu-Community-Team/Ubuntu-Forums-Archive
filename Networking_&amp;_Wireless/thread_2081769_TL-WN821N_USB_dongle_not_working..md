---
title: "TL-WN821N USB dongle not working."
date: 2012-11-07
forum: Networking &amp; Wireless
---

### Post by Laize on 2012-11-07
A few weeks ago I was wrestling for over a week with a Broadcom BCM4321 chipset that just refused to work with Precise 12.04.

So I gave up and bought a USB dongle that would work with my network and had a readily compatible chipset.  Only ONE version of that dongle had a problematic chipset and **lucky me**, here I am.

After following all processes to the best of my ability, NM is telling me *device not ready (firmware missing)*.

$ uname -a
```
3.2.0-32-generic #51-Ubuntu SMP Wed Sep 26 21:33:09 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

$ sudo lsusb   (bold is the device in question)
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
**Bus 005 Device 002: ID 0cf3:7015 Atheros Communications, Inc. TP-Link TL-WN821N v3 802.11n [Atheros AR7010+AR9287]**
Bus 001 Device 003: ID 1532:0015 Razer USA, Ltd 
Bus 001 Device 004: ID 1532:010d Razer USA, Ltd 
Bus 006 Device 002: ID 13fe:5200 Kingston Technology Company Inc. 
Bus 002 Device 003: ID 22b8:4366 Motorola PCS 
```

$ lshw -C network
```
  *-network               
       description: Network controller
       product: BCM4321 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:19 memory:f7ff8000-f7ffbfff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 06
       serial: 50:e5:49:c5:d8:aa
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:45 ioport:ee00(size=256) memory:fbbff000-fbbfffff memory:fbbf8000-fbbfbfff
[b]  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:70:3a:a3:f9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.2.0-32-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg[/b]
  *-network:1
       description: Ethernet interface
       physical id: 2
       logical name: easytether0
       serial: 06:3d:76:e2:47:4f
       size: 10Mbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full firmware=N/A ip=192.168.117.2 link=yes multicast=yes port=twisted pair speed=10Mbit/s
```

wlan0 is the interface Ubuntu grants my Broadcom NIC.  I disabled that intentionally.  easytether0 is me tethering my phone to my PC and connecting through it.  It's not an ideal situation.

I really appreciate any help.

---

### Post by Laize on 2012-11-07
Problem solved.  Occam's Razor wins again.

Next time I spend 4 hours troubleshooting a problem I might want to make sure I'm not plugging a USB 2.0 device into a USB 3.0 port.

---

### Post by Laize on 2012-11-07
New problem with it now.  The connection is highly erratic (sometimes falling a slow as 3 MB/s and sometimes as high as 25 MB/s).

---

### Post by golimpio on 2013-05-07
> **Laize said:**
> New problem with it now.  The connection is highly erratic (sometimes falling a slow as 3 MB/s and sometimes as high as 25 MB/s).

Any luck with the speed issue?

Thanks!

---

