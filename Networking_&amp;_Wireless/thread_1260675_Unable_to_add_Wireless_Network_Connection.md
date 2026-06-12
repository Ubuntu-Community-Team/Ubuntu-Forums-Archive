---
title: "Unable to add Wireless Network Connection"
date: 2009-09-07
forum: Networking &amp; Wireless
---

### Post by edwin.donaldson on 2009-09-07
I have just entered the Linux world... so be kind :)  I have an older Dell Latitude Laptop that I wiped of Win98 and loaded Ubuntu.  Now I'm trying to get a LinkSys WPC-11 wireless PC card to work.  It's not.  It is showing up when I run a diagnostic command, but when I go to Preferences > Network Connections > Wireless > "Add" and enter all the information for the network the "Apply" button does not make itself even available to be clicked.
What do I do to add a wireless connection?

---

### Post by x22 on 2009-09-11
welcome to the forum

well, depending on the WPC11 version, you need either 
the b43 driver--version 3--or the rtl8180 driver--version 4.
These are included in the linux kernel.

once the appropriate driver is loaded, you can do something
like this to set up the card, substituting your own 
parameters, assuming WEP 64-bit encryption

ifconfig wlan0 up
iwconfig wlan0 essid 2236a
iwconfig wlan0 channel 40
iwconfig wlan0 mode managed
iwconfig wlan0 key ..........
iwconfig wlan0 key open
dhclient wlan0

---

### Post by edwin.donaldson on 2009-09-12
How do I load a driver? Is this driver included in the Ubuntu bundle or is it found on the web? and how do I see that that the driver is loaded properly?

---

### Post by BriarHood on 2010-07-06
I am having similar issues. After entering


lspci -v | grep -i Network
sudo lshw -C network

This is what I have

  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:12:3f:1a:57:8e
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=full firmware=5751-v3.29a ip=68.3.54.55 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:16 memory:dfdf0000-dfdfffff
  *-network
       description: Instant Wireless Network PC Card
       product: ISL37300P
       vendor: The Linksys Group, Inc.
       physical id: 0
       version: RevA
       slot: Socket 0
       resources: irq:3
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:06:25:0b:80:9a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Intersil 1.4.2 link=no multicast=yes wireless=IEEE 802.11b

One light is solid, the other is blinking. Network manager recognizes it because wireless networks is accessible, but no networks show up, even when I know I am near them. I have no idea what to do and have tried almost everything I could find. Many reinstalls later, I'm stuck in the same position. Can anyone help?

---

### Post by Joe Ker1086 on 2010-07-06
I had a lot of success with a wpc54g using ndiswrapper. Just download ndiswrapper, download the windows driver for the card and follow the instructions for ndiswrapper to create a wireless driver. More info here: [http://sourceforge.net/projects/ndiswrapper/files/](http://sourceforge.net/projects/ndiswrapper/files/)

---

