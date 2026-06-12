---
title: "Cannot get wireless working"
date: 2009-11-22
forum: Networking &amp; Wireless
---

### Post by max6701 on 2009-11-22
Hi guys,
 
I just bought a Dell Inspiron 1545, Intel Core 2 Duo T6500, 2.1GHz, 800Mhz, 2M L2 
running with Window 7 64bit
 
Installed Ubuntu 9.10, all working except wifi. I cannot see any network (I have a home network, broadcasting and working in window).
 
My wireless card is a Dell Wireless 1397 802.11g Half Mini Card
 
Any idea of what I can do?
If you do, please provide me with dumb proof instructions, as I didn't use unix based systems for the last 20 years...:-k:-k:-k
 
Cheers,
Max

---

### Post by jeb800e on 2009-11-22
NDISwrapper may work

---

### Post by The Dragon Master on 2009-11-22
Try all the stuff suggested here and post the output
[http://ubuntuforums.org/archive/index.php/t-1308533.html](http://ubuntuforums.org/archive/index.php/t-1308533.html)

Here's an example using that approach which I just got working after waaaaaaay too long.
[http://ubuntuforums.org/showthread.php?t=1334424](http://ubuntuforums.org/showthread.php?t=1334424)

good luck
TDM

---

### Post by max6701 on 2009-11-22
> **The Dragon Master said:**
> Try all the stuff suggested here and post the output
[http://ubuntuforums.org/archive/index.php/t-1308533.html](http://ubuntuforums.org/archive/index.php/t-1308533.html)
 
Here's an example using that approach which I just got working after waaaaaaay too long.
[http://ubuntuforums.org/showthread.php?t=1334424](http://ubuntuforums.org/showthread.php?t=1334424)
 
good luck
TDM
 
Thanks a lot, I'll try. If it doesn't work, I'll have to come back to windows 7 to reply :roll:

---

### Post by coffeecat on 2009-11-22
Before you are tempted to frustrate yourself into an early grave with ndiswrapper, madwifi, wicd or anything else suggested in those links, have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=1196224](http://ubuntuforums.org/showthread.php?t=1196224)

It would seem that you have a Broadcom chipset wireless card and according to the last post there, all you need do is install the Broadcom driver by going to System > Administration > Hardware drivers.

If you have any problems, open a terminal and post the output of:

```
sudo lshw -C network
```... so that we can double-check that wireless chipset.

Please, everyone. **It's the chipset that matters.** There's no point in recommending anything until the chipset is known.

---

### Post by max6701 on 2009-11-23
thank you guys, did all I was advised to do...
 
 *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: [EMAIL="pci@0000:0c:00.0"]pci@0000:0c:00.0[/EMAIL]
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: [EMAIL="pci@0000:09:00.0"]pci@0000:09:00.0[/EMAIL]
       logical name: eth0
       version: 13
       serial: 00:25:64:5d:95:c9
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:29 memory:f68fc000-f68fffff ioport:de00(size=256)
 
 

Try going to System > Administration > Hardware Drivers
gives No property drivers fund
 
while:
I applied your indication:
sudo dpkg-reconfigure bcmwl-kernel-source
sudo modprobe -r b43 ssb wl
sudo modprobe wl
 

[EMAIL="massimo@ubuntu:~$"]massimo@ubuntu:~$[/EMAIL] iwlist scan
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
[EMAIL="massimo@ubuntu:~$"]massimo@ubuntu:~$[/EMAIL] sudo modprobe -r b43 ssb wl
[sudo] password for massimo: 
FATAL: Module wl not found.
[EMAIL="massimo@ubuntu:~$"]massimo@ubuntu:~$[/EMAIL] sudo modprobe wl
FATAL: Module wl not found.
[EMAIL="massimo@ubuntu:~$"]massimo@ubuntu:~$[/EMAIL] sudo iwlist scan
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
[EMAIL="massimo@ubuntu:~$"]massimo@ubuntu:~$[/EMAIL] 

 
Shall I scratch and re-install??? I must admit I am a bit lost...:confused:
 
Any support is welcome!
 
Cheers,
Max

---

### Post by max6701 on 2009-11-23
> **coffeecat said:**
> Before you are tempted to frustrate yourself into an early grave with ndiswrapper, madwifi, wicd or anything else suggested in those links, have a look at this thread:
 
[http://ubuntuforums.org/showthread.php?t=1196224](http://ubuntuforums.org/showthread.php?t=1196224)
 
It would seem that you have a Broadcom chipset wireless card and according to the last post there, all you need do is install the Broadcom driver by going to System > Administration > Hardware drivers.
 
If you have any problems, open a terminal and post the output of:
 
```
sudo lshw -C network
```... so that we can double-check that wireless chipset.
 
Please, everyone. **It's the chipset that matters.** There's no point in recommending anything until the chipset is known.
 
*-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: [EMAIL="pci@0000:0c:00.0"]pci@0000:0c:00.0[/EMAIL]
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: [EMAIL="pci@0000:09:00.0"]pci@0000:09:00.0[/EMAIL]
       logical name: eth0
       version: 13
       serial: 00:25:64:5d:95:c9
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:29 memory:f68fc000-f68fffff ioport:de00(size=256)

---

### Post by ublintu on 2009-11-23
Hi,
Did you try this (the first post)? :  [http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)

---

### Post by AFI420 on 2009-11-23
ive seen quite a few problems with the broadcom not working OOTB, but it can be done rather easily

---

### Post by ublintu on 2009-11-23
"ive seen quite a few problems with the broadcom not working OOTB, but it can be done rather easily"

That`s why I`m posting the link, which was helpful 4 me and I hope it can help for the others too.

---

### Post by max6701 on 2009-11-24
> **ublintu said:**
> Hi,
Did you try this (the first post)? : [http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)
 
Cool, I'll try the same this evening. :D
Thanks a lot!
Max

---

### Post by ublintu on 2009-11-24
Do the same, like in the first post and reboot. After this I had wireless.
Let me know what has happened!

---

### Post by kr651129 on 2010-01-03
> **max6701 said:**
> Cool, I'll try the same this evening. :D
Thanks a lot!
Max

I did this on my dell and it worked perfectly until I did a reboot and then my system seemed to forget all the settings?  I also went to broadcoms website and they provide a driver and install directions but they also seem to be forgoten after a reboot.  Any sugestions?

---

