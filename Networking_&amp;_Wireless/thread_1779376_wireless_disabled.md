---
title: "wireless disabled"
date: 2011-06-10
forum: Networking &amp; Wireless
---

### Post by Basickarma on 2011-06-10
Hey I'm very new to ubuntu, I have it installed on my Dell inspiron and it works great. I wanted rid of Windows so I installed it on my Sony Vaio PCG-21313M everything works fine on it except the bluetooth and the wireless. I can plug in an USB wireless adapter and that works but I don't want to have to use that when there is one inbuilt. I'm running ubuntu 10.04 I've used the help and when I put "sudo lshw -C network" it tells me the network is disabled. the help then says sometimes you have to turn the wireless on or off from windows. I don't have windows installed on it any more. Any help? then maybe help with the bluetooth...

---

### Post by TBABill on 2011-06-10
Perhaps the output of lsusb in a terminal would assist better (LSUSB in lowercase) since it's a USB device. This should let us know what chipset the device uses and then begin to work on why it's not working.

---

### Post by Basickarma on 2011-06-10
when I put in lsusb it gives 
> Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 050d:705a Belkin Components F5D7050A Wireless Adapter
Bus 001 Device 002: ID 0bda:5801 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I dont know if you would want everything it says for lshw -C network but its 
>  *-network DISABLED      
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt3090 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:16 memory:fe900000-fe90ffff
  *-network
       description: Ethernet interface
       product: JMC260 PCI Express Fast Ethernet Controller
       vendor: JMicron Technology Corp.
       physical id: 0.5
       bus info: pci@0000:02:00.5
       logical name: eth0
       version: 02
       serial: 54:42:49:6c:22:71
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msix msi bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.5 duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:27 memory:fe800000-fe803fff ioport:e100(size=128) ioport:e000(size=256)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:22:75:ad:24:96
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.65 multicast=yes wireless=IEEE 802.11bg


does this help?

---

