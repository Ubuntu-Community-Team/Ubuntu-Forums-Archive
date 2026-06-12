---
title: "[SOLVED] can't see any wireless networks"
date: 2009-01-02
forum: Networking &amp; Wireless
---

### Post by Jimi180 on 2009-01-02
I've finally got Ubuntu up and running but now I'm having real problems connecting to the internet. There is an icon in the top left of two monitors with a little orange warning symbol on them, I click that and just get options for VPN, connect to hidden, and create - the other ones are grayed out and no wireless networks are found. This is on my desktop with a full install of 8.10, so I've booted up the live cd on my laptop, click the networks icon and it displays the name of my network adaptor and 3 wireless networks in range including mine I want to connect too. I assume this means I need to install a driver for the one on my desktop, but have tried absolutely EVERYTHING and nothing works :( I've read every single bit of info I can, downloaded various things but still nothing works. If I go to system > administration > hardware drivers it says I can install the "B43" driver but when I try and do that it doesn't seem to do anything, a status bar which says something like "downloading and installing" pops up and then closes while still at 0% (same thing happens if I try and install the nvidia driver listed there) and it remains unactivated. I've tried ndiswrapper with no luck at all. I've got a BT wireless PCI card, something to do with Broadcom 802.11g (sorry, not very technical)

What can I do?
Thanks for any help

---

### Post by ieee488 on 2009-01-02
Instead of scattergun approach, read the Sticky at the top of the 1st page about how to troubleshoot your wireless card.

---

### Post by Jimi180 on 2009-01-02
I've already scanned through that, but presume I don't even need ndiswrapper as there appears to be a driver preinstalled which I can use. The problem is I don't seem to be able to activate it, I mean, I can't activate any of the drivers listed in the hardware drivers section - so wasn't sure if I could use terminal for example to install that B43 driver.

---

### Post by superprash2003 on 2009-01-02
connect your laptop via LAN.. and then run hardware drivers again..

---

### Post by Jimi180 on 2009-01-02
Thanks for the reply, ubuntu is installed on my desktop which is at the opposite end of the house from my router and I was just using the laptop to run ubuntu live to check the networks were showing up (which they do fine on the laptop). 

I've just gone through the ndiswrapper sticky in full and although I've still not got it working, I don't know if anyone could take a look at these outputs and see if they can make anything of them? 

Firstly, I used ndiswrapper to install a driver called "bcmwl5.inf" - everywhere seems to suggest you need an .inf AND a .sys file for the driver, I also have bcmwl5.sys but ndiswrapper only accepts .inf files and just one of them, I don't see how you install multiple files (probably being stupid there)

Anyway, this is what I get from a couple of the commands in terminal:

[SIZE="1"]
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: ssb)
james@james-ubuntu:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:04:07.0
       logical name: eth0
       version: 02
       serial: 00:1a:a0:1c:ce:0b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:04:09.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:11:f5:14:cb:e7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 96:57:53:2f:7f:fb
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
james@james-ubuntu:~$ 
[/SIZE]

Thanks again :)

---

### Post by oseney on 2009-01-02
you need the .sys file in the same place as the .inf file

---

### Post by Jimi180 on 2009-01-02
Oh in that case they are, though they aren't in the partition where ubuntu is installed if that matters, they are in a partition I'm using for storage, downloading things I need for ubuntu in vista where my wireless works, saving them in there and they accessing them in ubuntu.

---

### Post by Jimi180 on 2009-01-02
Problem solved, moved my whole desktop downstairs and was able to plugin to the router via ethernet and download the driver from within the hardware drivers section, wireless seems to be working fine, marked as solved.

---

