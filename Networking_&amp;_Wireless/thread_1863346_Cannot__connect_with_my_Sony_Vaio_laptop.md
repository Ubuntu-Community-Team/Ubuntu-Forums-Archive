---
title: "Cannot  connect with my Sony Vaio laptop"
date: 2011-10-17
forum: Networking &amp; Wireless
---

### Post by elranu on 2011-10-17
Hi,
       I have a Sony Vaio FW490EJB. I have try serveral times to connect to any network (wired and wireless) with ubuntu 11.10 and 11.04 and a I could not. I always get the following message on Gnome: "wired network disconnected - you are now offline" on wireless also. I install also Debian 6, and during installation I successfully connect, but on Gnome in debian I get the same message. 

Below is the information for Ubuntu 10.10,  I will appreciated any help.


sudo lshw -C network; lsb_release -a; sudo rfkill list
  *-network               
       description: Wireless interface
       product: WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 00
       serial: 00:22:fb:7e:a7:f2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=3.0.0-12-generic firmware=8.83.5.1 build 33692 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:48 memory:d1500000-d1501fff
  *-network
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 14
       serial: 00:1d:ba:f3:6d:34
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:47 memory:d0120000-d0123fff ioport:9000(size=256) memory:d0100000-d011ffff
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 11.10
Release:	11.10
Codename:	oneiric
0: sony-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: sony-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

Regards,
Mariano Vicario

---

