---
title: "ubuntu intrepid Atheros AR5007 wireless"
date: 2009-02-11
forum: Networking &amp; Wireless
---

### Post by andrewkillandrew on 2009-02-11
Ok, I seriously need some help getting wireless working on my laptop (acer aspire 5313). I have been at this for weeks with no success. I have ubuntu intrepid installed and have followed all the step from this thread [http://ubuntuforums.org/showthread.php?t=981276](http://ubuntuforums.org/showthread.php?t=981276). I installed the drivers (I have an Atheros AR5007EG Wireless Network Adapter) and made all the modifications to the relevant files but still cannot 'see' my router. I am using wicd manager as I do not have network-manager installed. Any help will be much appreciated. Oh and the network is not hidden as far as I can tell.

---

### Post by andrewkillandrew on 2009-02-11
*-network               
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:ec:45:6d:a1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 ip=10.0.0.6 latency=0 module=tg3 multicast=yes
  *-network DISABLED
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 01
       serial: 00:1f:e1:5c:3e:ee
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ea:9e:73:4a:c7:4d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

Don't know if this might help.

---

### Post by FishRCynic on 2009-02-11
take a look at this might help

[http://ubuntuforums.org/showthread.p...ghlight=DV9700](http://ubuntuforums.org/showthread.p...ghlight=DV9700)

---

