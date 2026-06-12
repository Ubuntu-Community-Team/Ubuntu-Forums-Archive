---
title: "Wireless option not in Net. Manager; no wireless connection"
date: 2010-08-01
forum: Networking &amp; Wireless
---

### Post by plzdontkillme11 on 2010-08-01
Hi,

For starters, when I click on the Netweork icon, only the Wired Network option shows up. The Wireless is not even there. I activated the Atheros madwifi driver in Hardware Drivers.

Here's some information that'll help.

```

vignesh@vignesh-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:a8:96:ac
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.5 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:27 ioport:3000(size=256) memory:d0410000-d0410fff(prefetchable) memory:d0400000-d040ffff(prefetchable) memory:d0420000-d043ffff(prefetchable)
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
       resources: memory:d4600000-d460ffff

```

---

### Post by plzdontkillme11 on 2010-08-01
No one?

---

### Post by plzdontkillme11 on 2010-08-01
I just noticed that the Atheros madwifi driver is "activated but not currently in use." Hopefully that helps.

---

### Post by viking350 on 2010-08-01
It could be your wireless card or some other way you access your internet

---

### Post by plzdontkillme11 on 2010-08-01
Is there any way to check?

I looked everywhere for my driver - AR5001 - but the closest I found was AR5001x or AR5001A. Would these work?

---

### Post by marc.verwerft on 2010-08-02
On this page there are some pointers to debugging your wireless connection:

[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

Take your pick.

---

### Post by plzdontkillme11 on 2010-08-02
Thank you. I'll take a look.

---

### Post by danman33 on 2010-08-04
I have the exact same problem, ever since i installed madwifi my wifi device doesnt even show up. im running 10.04 wit an atheros AR5001 card. i u figured it out id like to know how u did it

---

