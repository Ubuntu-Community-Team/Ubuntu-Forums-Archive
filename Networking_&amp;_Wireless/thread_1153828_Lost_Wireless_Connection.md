---
title: "Lost Wireless Connection"
date: 2009-05-09
forum: Networking &amp; Wireless
---

### Post by Tambaqui on 2009-05-09
Hey all!

Before, I've been having some problems with the video, and found a solution and that was to install the latest kernel as mentioned here:

[http://ubuntuforums.org/showthread.php?t=1134984](http://ubuntuforums.org/showthread.php?t=1134984)

But as I did that and now just realise that I've lost the wireless connection, and when I went to do the modprobe ndiswrapper, I've gotten this:

FATAL: Module ndiswrapper not found.

I am completely stumped, its almost like a chain, one leads to another!

Edit: Forgot to mention, my wireless card is: WG311v3

and when I did:

ndiswrapper -l

Got this if it helps:
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
wg311v3 : driver installed
	device (11AB:1FAA) present

---

### Post by superprash2003 on 2009-05-09
have you tried rebooting.. post output of **lshw -C network** from the terminal

---

### Post by Tambaqui on 2009-05-10
Hope this helps!

[sudo] password for michael: 
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32
  *-network:1
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 01
       serial: 00:0c:f1:d0:3b:f9
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.2 latency=32 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ea:f9:49:b3:d9:d1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by superprash2003 on 2009-05-11
[http://ubuntuforums.org/archive/index.php/t-208088.html](http://ubuntuforums.org/archive/index.php/t-208088.html)

---

