---
title: "Wired Ethernet controller shows as  *-network UNCLAIMED???"
date: 2009-10-01
forum: Networking &amp; Wireless
---

### Post by Missebet on 2009-10-01
Update: 10-01-2009:    loaded and installed new updates and it is suddenly working.  all is well in my world atm


my wireless worked great without any config on my part, but I want to get the wired connection working.  Both cards work fine in windows.

I'm running Unbuntu 9.04 on an Acer Aspire 5516

Here is the info from lshw -c network

ebet@LinuxLaptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:25:56:57:3d:51
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci ip=192.168.1.100 latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network UNCLAIMED
       description: Ethernet controller
       product: Attansic Technology Corp.
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 12:8b:a4:03:86:b8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
ebet@LinuxLaptop:~$ 

-------------------------------------------------------------
This is the text of my /etc/network/interfaces file

auto lo
iface lo inet loopback

-------------------------------------
Being a Linux newbie I most likely did something to mess up my wired connection and would like to get it up and running.  I have Network Manager 0.7.0.100 and Network Tools 2.26.1 installed.

A friend advised to look at ndiswrapper, but I'm hesitant to use it as I do not understand all of the ends and outs of compiling a driver.

any help is appreciated.

cheers

---

