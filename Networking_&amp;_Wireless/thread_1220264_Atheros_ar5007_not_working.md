---
title: "Atheros ar5007 not working"
date: 2009-07-22
forum: Networking &amp; Wireless
---

### Post by naomibrown on 2009-07-22
I've followed the tutorial:
[https://help.ubuntu.com/community/WifiDocs/Device/AR5007]("https://help.ubuntu.com/community/WifiDocs/Device/AR5007")

and I still can't get my wireless working on 9.04. I have a Toshiba Satellite Pro.

:confused:

---

### Post by superprash2003 on 2009-07-23
post output of **lshw -C network** from the ubuntu terminal

---

### Post by naomibrown on 2009-07-23
*-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:38:41:eb:23
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.3 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 3a:f2:ea:56:2e:95
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by superprash2003 on 2009-07-23
try this [http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html](http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html)

---

