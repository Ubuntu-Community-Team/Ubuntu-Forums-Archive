---
title: "2 hdd, same install one with problems"
date: 2009-02-10
forum: Networking &amp; Wireless
---

### Post by ubucrap on 2009-02-10
I have two hdd that I installed 8.10 on recently. One of them is a back up drive, and then other is my operating drive. I did nothing different with the installation, yet when I plug in the back up, I have no problems with the wireless. I have a dell mini wireless card (broadcom) and the STA broadcom proprietary drivers is working and allowing me no problems with wireless networks. 
When I plug in normal operating drive though, I can not get the wireless to work at all. I have no idea what the problem is. I will have both the drives plugged in at the same time and boot between the two seemlessly, but the wireless only works on one!
This is driving me crazy!!
This is my output on the drive that is not working correctly
 for: ~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:6f:eb:fd
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.202 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: d6:3b:74:83:b1:18
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

Thanks

---

### Post by ubucrap on 2009-02-16
not everyone at once!!

---

### Post by Gramps on 2009-02-16
Did you compare the output of lshw -C network on the drive that works.

I might try reinstalling 8.10 on the primary drive, maybe there was a glitch when it was installed and it didn't get the wireless card right.

---

