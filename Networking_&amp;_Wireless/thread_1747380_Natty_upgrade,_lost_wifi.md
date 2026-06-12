---
title: "Natty upgrade, lost wifi"
date: 2011-05-02
forum: Networking &amp; Wireless
---

### Post by ephemerian on 2011-05-02
After being prompted by UpdateManager, I upgraded my Compaq Presario CQ71 from 10.10 to 11.04 yesterday. Most things seem fine, except that my wifi is disabled (it was working fine in 10.10). Here are some details:

```
root@ian-laptop # lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 0c:60:76:3d:5e:02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-8-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:d3500000-d350ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:26:9e:2d:37:0a
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.122 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:d1410000-d1410fff memory:d1400000-d140ffff memory:d1420000-d142ffff

``````
root@ian-laptop # uname -a
Linux ian-laptop 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```Any suggestions as to what I can try or do next? 

Thanks,
Ian

---

### Post by ephemerian on 2011-05-02
Not quite sure what the issue was, but a quick trip via the Win7 dual boot seems to have restored wifi functionality. As well as the Natty upgrade, I was doing my once-in-a-blue-moon apply all Windows updates, so I'm guessing that something there left my wireless nic in an unusual state. But I hardly ever use the dual boot (hence only infrequent updates), so I'm anticipating few problems in future.

---

