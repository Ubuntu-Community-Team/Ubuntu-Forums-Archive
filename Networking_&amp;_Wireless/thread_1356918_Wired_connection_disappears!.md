---
title: "Wired connection disappears?!"
date: 2009-12-16
forum: Networking &amp; Wireless
---

### Post by zonination on 2009-12-16
So I got my installation when it came out, but there's still a tiny bug that I can't seem to get past:

Every now and then, my wired (auto eth0) connection will disappear. Disappear from the network manager menu, disappear from ifconfig, and even if I disconnect and re-plug it in, it still doesn't work. The rest defaults to wireless.

This is okay, since I normally reboot and find it connecting to auto eth0 again. But for the last two days, it's been rejecting the idea that there's even a connection. I.e., it refuses to connect to wired. I've tried different kernel packages, different jacks on my wall, different commands, and none of them seem to work.

I would appreciate any help regarding this problem.

Cheers!

---

### Post by Iowan on 2009-12-16
What kind of card is it (brand/model)?

---

### Post by zonination on 2009-12-16
The wireless is Broadcom. Apparently the driver for the wired connection has either disappeared or I can't find it in system>admin>hardware.

More help on how to find out what my ethernet drivers are would be appreciated. :)

---

### Post by Iowan on 2009-12-16
Check **sudo lshw -C network**.

---

### Post by zonination on 2009-12-16
Broadcom as well, apparently. Why is it disabled?

```
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:fc:d1:e6:5f
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=129.21.104.179 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:c0200000-c0203fff
  *-network DISABLED
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth1_rename
       version: 02
       serial: 00:1c:23:8a:11:7a
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 latency=64 link=no multicast=yes port=twisted pair
       resources: irq:21 memory:c0300000-c0301fff

```

---

### Post by Iowan on 2009-12-17
> **zonination said:**
> Broadcom as well, apparently. Why is it disabled?Wired connection is *probably* disabled because the wireless is active (has an IP address - which you may wish to obscure). 

Wait... why is it "eth1_rename"? (just asking myself...)
BTW, the drivers are listed in the output.

---

### Post by zonination on 2009-12-21
> **Iowan said:**
> Wired connection is *probably* disabled because the wireless is active (has an IP address - which you may wish to obscure). 

Wait... why is it "eth1_rename"? (just asking myself...)
BTW, the drivers are listed in the output.

Well, I hardware-disabled wireless and was surprised to see that even the wired would not connect. It's not the ethernet cable as I switched to different cables and got the same effect.

---

### Post by vikram1 on 2010-01-04
Maybe once a day or so my home wireless network disappears from the iPAQ list of Available Networks, instead just showing two unsecured networks from neighbors who are broadcasting their SSID.  When the problem is going to occur I'll often get a balloon message saying something about the Network Key being wrong with a place to enter a key in.  Once I go to the Wireless Settings area I'll briefly see the home connection and then it usuallly disappears.    I was able to catch it twice before the "disappearing" stage and saw that the Key setting had changed by itself from being manually entered in by myself to having a checkmark next to Automatically Provided.   

When this happens I've been adding the network info in again by clicking New...entering in the SSID and the key.  After that it will work great until it happens the next time.  
==================
[saturn ac compressor](http://www.1airconditioning.com/saturn_ac_compressor.htm)
[chicago party bus](http://www.chicagolimousine1.com)

---

