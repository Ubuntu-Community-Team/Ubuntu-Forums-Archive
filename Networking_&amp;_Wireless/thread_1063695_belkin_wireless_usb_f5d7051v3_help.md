---
title: "belkin wireless usb f5d7051v3 help"
date: 2009-02-08
forum: Networking &amp; Wireless
---

### Post by JAYLIDS on 2009-02-08
i have recently installed ubuntu 8.10 intrepid on my advent 3518 desktop, i also have the dredded f5d7051 wireless usb adapter from belkin which i cant get to work.when i run the command lsusb it shows up as-

bus 005 device 004: id 4317:0711

i have also tried installing xp drivers from the disk (ndiswdm.inf ndiswdm.sys bcm43.cat) using ndiswrapper it says device not present, if i install vista drivers from cd (bcmusbdhd.inf bcmusbdhdlh.sys bcmusbdhdlh.cat) it says device present but doesnt work.

any help would be great thx.

---

### Post by Gomps on 2009-02-20
I can't get mine to connect either. This is what I'm looking at:

[FONT="Courier New"]gomps@gomps-desktop:~$ sudo lshw -C network
[sudo] password for gomps: 
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: 13
       serial: 00:11:2f:e1:3d:6e
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 firmware=N/A latency=64 link=no maxlatency=31 mingnt=23 module=skge multicast=yes port=twisted pair
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:30:bd:99:a0:c6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: fe:70:17:6b:32:6a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
gomps@gomps-desktop:~$[/FONT]

---

### Post by tupactim on 2009-03-24
Can anyone help with this please?

---

