---
title: "dell d410 no wireless"
date: 2008-12-24
forum: Networking &amp; Wireless
---

### Post by endacoz on 2008-12-24
When I type sudo iwconfig

lo   no wireless extensions

eth0 no wireless extensions

wmaster0  no wireless extensions

wlan0 ieee 802.11bg essid:''
     mode:managed frequency:2.412 GHz  Access Point: Not-Associated
     TX-power=27 dBm
.....

pan0 noe wireless extensions

sudo iwlist eth1 scan
eth1   interface doesn't support scanning

What can I do to get the wireless to work in ubuntu 8.1 UP TO DATE (used wired connection for updates) really need to get wireless to work!

Please help

---

### Post by superprash2003 on 2008-12-24
post output of the following commands
1)lshw -C network
2)iwlist scanning

---

### Post by endacoz on 2008-12-24
$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 01
       serial: 00:12:3f:21:eb:9e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 firmware=5751-v3.29a latency=0 module=tg3 multicast=yes
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:d7:2e:a1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: a2:48:45:c0:9e:18
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes



 iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

---

### Post by ieee488 on 2008-12-24
Do a search on this forum about 'Broadcom Air Force'.
It's popular.

---

### Post by john89521 on 2011-09-15
These directions did the trick for my Dell D410 (w/11.04). A **big thanks** to Chili555 for them!
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)

---

