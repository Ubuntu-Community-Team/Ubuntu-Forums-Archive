---
title: "Broadcom BCM43228"
date: 2012-11-15
forum: Networking &amp; Wireless
---

### Post by DuckZoro on 2012-11-15
So, I am sitting on a brand-new installation of 12.10 64bit, alongside windows 7 on a brand-new computer. Right after installation, the wireless worked, however, after installing the 97 updates that were needed and rebooting, there is no wifi to be had (ethernet works fine though, that's how I'm posting this). I have looked in software sources, and it claims that the proprietary driver is being employed.

Running lshw -C network:

```
lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetLink BCM57785 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: b8:88:e3:09:5b:5f
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.123 duplex=full firmware=sb ip=192.168.0.183 latency=0 multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:16 memory:b3430000-b343ffff memory:b3440000-b344ffff memory:b3450000-b34507ff
  *-network UNCLAIMED
       description: Network controller
       product: BCM43228 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:b3500000-b3503fff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

```From another thread (here: [http://ubuntuforums.org/showthread.php?t=1816292](http://ubuntuforums.org/showthread.php?t=1816292)), I saw that the below information might be useful?

```
lspci -nn | grep 0280 
03:00.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]
 
```Of course I also tried the fix from that thread, but that gave me nothing - at the end I just got the message that "this card has not actually been tested, please install the driver manually", or something along those lines.

Any suggestions?

EDIT: I apologise for the uninformative title, don't know what happened there.

---

### Post by mörgæs on 2012-11-15
> **DuckZoro said:**
> I apologise for the uninformative title, don't know what happened there.

Changed that for you.

---

### Post by DuckZoro on 2012-11-15
thanks :)

---

### Post by NikTh on 2012-11-15
Hi , 
open a terminal and try this (you need an active Internet connection , eg: through Ethernet cable)
```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
``` 

Then unplug Ethernet cable and reboot. 

Working ? 

Thanks

---

### Post by DuckZoro on 2012-11-15
actually, I didn't even have to reboot (did it anyway though).

thanks :)

---

### Post by Godproducks on 2013-01-21
> **NikTh said:**
> Hi , 
open a terminal and try this (you need an active Internet connection , eg: through Ethernet cable)
```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
``` 

Then unplug Ethernet cable and reboot. 

Working ? 

Thanks

Thanks, it works for me too. &#1057;ould you explain how you found the solution?

---

### Post by wijit on 2013-02-26
Solved mine too. Thanks, Nikky.

Oops!
The problem came back again after stopping wireless connection and using wired connection for printing some paper works.

However, I followed [http://pkgs.org/ubuntu-12.04/ubuntu-multiverse-i386/broadcom-sta-common_5.100.82.112-4_all.deb/download/](http://pkgs.org/ubuntu-12.04/ubuntu-multiverse-i386/broadcom-sta-common_5.100.82.112-4_all.deb/download/)
and felt a bit better. Not sure if the problem coming back.

---

### Post by alysonoliveira on 2013-04-23
The solution provided for NikTh worked for me too, but also happened the same situation that wijit reported. I tried the installation of the broadcom-sta-common package. Then I had no problem.

Thanks!

---

