---
title: "Lost my wireless network"
date: 2011-04-17
forum: Networking &amp; Wireless
---

### Post by Sutam on 2011-04-17
Hi, I'm sorry if this is in the wrong section or format, if it is let me know where to go :-)

I have been running Ubuntu 9.10 on my desktop machine for about a month using a Linksys Compact Wireless-G USB Network Adapter and in typical Ubuntu style everything worked well, I just plugged it in and it worked. This morning I shut the machine down to have a look inside and when I switched it back on it would not recognize my wireless network. My iMac, my ubuntu netbook and my phone can all still see my wireless network and the Ubuntu desktop can see five of my neighbors networks, just not mine.

I've tried everything I can think of to get it back, but as a newb of about 4 months on Linux thats not much, namely:

-Disabled and re-enabled wireless networking.
-Logged out and logged back in.
Tried a different user
-Restarted the machine (many times)
-Shut down, left for an hour and restarted
-Tried a different USB port
-Used a USB extension cable to get the dongle clear of any nasty cables
-Begged the computer to work
-Looked for a long enough Ethernet cable to plug it in directly and failed

I'm confused because both the access point and the machine seem to be working fine according to other devices and have worked fine together for ages. Does anyone have any ideas?

---

### Post by uncaspi on 2011-04-17
Maybe you have to modprobe your driver.
Please post the content of
sudo lshw -C network

---

### Post by Sutam on 2011-04-18
OK, I've changed nothing, I just left the machine on over night and it seems to have picked up the network. I suppose this just needs to be put down as one of those things, but if anyone thinks there could have been a reason for this and nkows a way of stopping it happening again please let me know.

Thanks for the input uncaspi, I'll post the info you asked for even though its sort of sorted in case you can spot something that may mean I have this problem again. Thanks for your help so far!

>   *-network               
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:01:80:57:61:22
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=32 link=no maxlatency=11 mingnt=52 multicast=yes port=MII speed=10MB/s
       resources: irq:19 ioport:e000(size=256) memory:ed102000-ed102fff memory:40000000-4001ffff(prefetchable)
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1e:e5:2b:8c:6d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rndis_wlan driverversion=22-Aug-2005 firmware=Wireless RNDIS device, BCM4320b usb-0000:00:03.0-3.4 ip=192.168.1.8 link=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes


---

