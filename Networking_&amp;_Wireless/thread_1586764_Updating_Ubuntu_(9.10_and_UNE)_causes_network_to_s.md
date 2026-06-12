---
title: "Updating Ubuntu (9.10 and UNE) causes network to stop working..."
date: 2010-10-02
forum: Networking &amp; Wireless
---

### Post by Heidious on 2010-10-02
The other night I dual-booted my PC with Ubuntu 9.10 from the Live CD.  After working perfectly I then let Update Manager install some  much-needed updates. After restarting the PC Ubuntu no longer picks up  my wired connection (my router is a Belkin Wireless G).

And last night I did the same thing on Ubuntu Netbook Remix and now that  has stopped picking up my router (or any network in fact).

Is this a common problem with updating Ubuntu or is there some way of  rectifying it? I am new to Linux and am loving UNE but am getting  frustrated with network problems.

Thanks in advace for any help :)

PC SPEC
======

Intel Pentium 3.06Ghz
2Gb DDR2 RAM
120Gb HDD
GeForce 6200
Ubuntu 9.10 & Windows XP SP3

NETBOOK SPEC
==========

Intel Atom 1.6Ghz
1Gb  DDR2 RAM
160Gb HDD
Integrated Graphics
Ubuntu Netbook Edition & Windows XP SP3

---

### Post by sikander3786 on 2010-10-02
Can you connect to a wired network? If you can, the drivers might just appear under System > Administration > Hardware Drivers.

The drivers were supposed to work after the upgrade without needing to be reinstalled. Still you can try that one, in the mean time you will get more useful replies.

Regards.

---

### Post by Scott. on 2010-10-02
I've had similar problems with Ubuntu 10.04 & 10.1 64bit editions.  I finally broke down and backed up to 9.1, which eliminated a video problem I was having.  I went out and got a Netgear USB WG111v3 which was on the compatible hardware list - didn't work.  So I returned it and got a WG111v2 off Craigslist for $7.  It works like a charm.  I can connect and disconnect it all day and it won't fail me. And this is with native Linux drivers.  I know this isn't a direct answer to your question, but if you're just looking for anything that will work...

Scott

---

### Post by Heidious on 2010-10-03
> **sikander3786 said:**
> Can you connect to a wired network? If you can, the drivers might just appear under System > Administration > Hardware Drivers.

The drivers were supposed to work after the upgrade without needing to be reinstalled. Still you can try that one, in the mean time you will get more useful replies.

Regards.

It runs perfectly through a wired connection (I'm using it as I type this) but nothing appears under Hardware Drivers. I had this problem the first time I installed UNE and I had to run some commands in ndiswrapper. Not sure if this is something I can try again.

Thanks for the reply :)

---

### Post by Heidious on 2010-10-03
UPDATE:

Okay, here's what I've tried. I've done a search for my Wireless ID after typing lspci -nn into terminal with the following output for my adapter:

> 03:00.0 Network controller [0280]: RaLink RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]
But the search yielded nothing so I ran a Google search for the actual product name (RaLink RT3090) which, funnily enough, brought me back to the Ubuntu forums where I downloaded the support files linked [here]("http://ubuntuforums.org/showthread.php?t=1314747") which everyone said helped them. However, my netbook states that I already had it installed. So I installed it again just to make sure.

Still nothing. So I've opened ndiswrapper and am trying to locate the correct .inf file for my adaper. It's weird because my wireless light on my Belkin router isn't even on.

Where do I go from here?

Also, this is the output for the command lshw -C Network:

> 
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f0100000-f010ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:03:0d:f0:91:0b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.2.3 latency=0 multicast=yes
       resources: irq:27 ioport:2000(size=256) memory:f0510000-f0510fff(prefetchable) memory:f0500000-f050ffff(prefetchable) memory:f0520000-f053ffff(prefetchable)


---

### Post by Heidious on 2010-10-03
UPDATE AGAIN:

Sorry for the multiple posts. I restarted and it's now working again. I'm not 100% sure what corrected the problem but I sincerely hope UNE isn't going to make a habit of this... :)

---

