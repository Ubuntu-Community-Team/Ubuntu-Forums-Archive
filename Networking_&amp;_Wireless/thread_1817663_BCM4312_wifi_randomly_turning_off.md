---
title: "BCM4312 wifi randomly turning off"
date: 2011-08-03
forum: Networking &amp; Wireless
---

### Post by SlingerXL on 2011-08-03
10.04 BackTrack distro.
Broadcom BCM4312 NIC (rev 01)

lshw -C network
  ```
*-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f6cfc000-f6cfffff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 10
       serial: 00:98:63:de:ab:2b
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 firmware=sb v2.09 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:47 memory:f69f0000-f69fffff
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:22:5f:54:1d:b9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38 firmware=508.1084 ip=192.168.1.104 link=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
```

The little "WIFI" light at the top right side of my laptop (Dell studio 1535) will seemingly randomly turn off or flicker every few minutes. If I try to reconnect to the internet it pops back up every time. Sometimes it turns off multiple times in a minute and sometimes it stays up for 30 minutes or more. If I leave my computer for 20 minutes or so I can almost be guaranteed that I will have been disconnected to my wireless. Sometimes when I try to reconnect to the wireless Wicd gives me an error saying I either couldn't get an IP or the password is wrong (which it isn't). A reboot fixes that but I think that may be Wicd's fault and not my wifi card. I've been disconnected 4 times in the 15 minutes that I've been writing this post.

Is it a power management problem? If so, how do I fix that? And why did this problem seem to spring from nowhere?

---

