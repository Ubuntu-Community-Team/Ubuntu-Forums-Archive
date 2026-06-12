---
title: "Wireless access on Jaunty 9.04 Live CD"
date: 2009-05-22
forum: Networking &amp; Wireless
---

### Post by John The Bad on 2009-05-22
Hi.  I run the 9.04 Live CD on a HP Compaq 7615s laptop and I cannot access my wireless network. Does anyone know if there is a way to do this?

---

### Post by ElevenWarrior on 2009-05-22
yah you have to install the drivers for your wireless card which requires you install Juanty.
thats the only fix I know of.

---

### Post by superprash2003 on 2009-05-23
in your terminal type **lshw -C network** and post output here

---

### Post by John The Bad on 2009-05-23
I assume you mean run "lshw -C network" from the terminal in my Ubuntu 8.04 installation.

This is the result:

  *-network               
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:c4:cb:6d:c3
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 latency=0 link=no module=tg3 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:30:00.0
       logical name: wlan0
       version: 02
       serial: 00:1a:73:f9:8e:d0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. ip=192.168.1.6 latency=0 link=yes module=ndiswrapper multicast=yes wireless=IEEE 802.11g

I ran the command from the termianl while running the 9.04 Live CD but was unable to save the output to file.

---

### Post by superprash2003 on 2009-05-24
your card seems to be recognized with ip 192.168.1.6 .. are you sure no internet access?? post output of the following
1)sudo iwlist scanning
2)ifconfig
3)iwconfig

---

