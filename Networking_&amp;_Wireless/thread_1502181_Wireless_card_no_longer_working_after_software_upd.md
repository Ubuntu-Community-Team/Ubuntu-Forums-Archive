---
title: "Wireless card no longer working after software update"
date: 2010-06-05
forum: Networking &amp; Wireless
---

### Post by pieman711 on 2010-06-05
My friend recently installed 10.04 on his hp pavilion laptop and we got everything working fine, including the wireless internet. When he installed some recommended software updates his card is no longer being detected although wired networking is still fine.


ryan@ryan-laptop:~$ sudo lshw -c network
[sudo] password for ryan: 
  *-network:0 UNCLAIMED   
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:03:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=64
       resources: memory:b0200000-b0201fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:76:b2:73
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=128 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:22 ioport:a000(size=256) memory:b0203000-b02030ff
ryan@ryan-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:76:b2:73  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fe76:b273/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:723 errors:0 dropped:0 overruns:0 frame:0
          TX packets:732 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:651032 (651.0 KB)  TX bytes:152178 (152.1 KB)
          Interrupt:22 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5584 (5.5 KB)  TX bytes:5584 (5.5 KB)

ryan@ryan-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

In the Hardware drivers in the system>administration menu it detects the modem but no longer shows the wireless card at all.

Any advice would be greatly appreciated. I've tried google but found nothing.

---

### Post by wojox on 2010-06-05
Try: 

```
sudo apt-get install bcmwl-kernel-source
```

Then reboot with the Ethernet cable unplugged and click your Network Manager Applet and configure from there.

---

### Post by pieman711 on 2010-06-05
We tried that, what exactly did you mean by 'configure in network applet manager' the only thing we could find was the icon at the top of the screen that normally shows the signal strength. If you right click it it used to say 'enable wireless' but now it just has 'enable networking' and ' enable notifications'
Oh and his card still doesn't appear in the hardware driver menu, which I would expect even if the driver wasn't working.

---

### Post by wojox on 2010-06-05
Yeah network applet manager is the same thing.

What driver where you using before?

---

### Post by pieman711 on 2010-06-05
we used information from this site to get it working before the update 

[http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)

Have tried that again but it didn't help

---

### Post by wojox on 2010-06-05
Looks like your not alone [http://ubuntuforums.org/showthread.php?t=1475006&highlight=b43](http://ubuntuforums.org/showthread.php?t=1475006&highlight=b43)

---

### Post by pieman711 on 2010-06-05
I saw that thread but our problem sounds slightly different. They seem to have a wireless card that isn't functioning properly whereas my friends laptop seems to be denying he even has a card...
If there any way to undo the last updates, revert to a previous working set up?

---

### Post by wojox on 2010-06-05
Can you boot into the previous kernel and try that?

---

### Post by pieman711 on 2010-06-05
When he restarts his laptop it doesn't automatically come up with a list of kernals to select like mine does (when I can also choose to boot windows instead) he only had ubuntu on his laptop and no other OS'es 
Is there a way to turn that on?

---

### Post by wojox on 2010-06-05
Hold down the left Shift key.

---

### Post by pieman711 on 2010-06-05
Thanks for that, that solved it!
We rolled it back to a previous kernal and his card then appeared in the 'hardeware drivers' thing I mentioned above. We activated teh driver from there and hey presto.

A bit of googling brought this as up another way of showing the grub loader when you restart your computer in case anyone else is having a similar problem but I think your way would have been a lot easier! 

[http://www.easy-ubuntu-linux.com/grub-menu-visible.html](http://www.easy-ubuntu-linux.com/grub-menu-visible.html)


I think it must have been a problem with  one of the up dates. I'll look into it later when I have more time.

Thanks for all your help.
:) :) :)

---

### Post by pieman711 on 2010-07-04
My friends been making do with going back to the previous working version of his ubuntu (the one before the upgrade) by just selecting it from the grub menu. Seeing as he never uses the top one can he simply delete it? 
This article shows how to edit the order and what appears in grub but how do you completely remove the entry for his recent version off of the hard-drive?

[http://ubuntuforums.org/showthread.php?t=538009](http://ubuntuforums.org/showthread.php?t=538009)

---

