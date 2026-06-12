---
title: "activating my wireless card"
date: 2008-12-23
forum: Networking &amp; Wireless
---

### Post by silence88 on 2008-12-23
Hi folks. I've just entered the wonderful world of Linux and installed Ubuntu 8.04 on that old laptop of mine. And as expected, I'm having trouble installing my Linksys WPC54G wireless card : the light stays off and no network is detected.
I've tried installing the windows driver with ndiswrapper, but it doesn't seem to work. Hours of googling haven't brought me any closer to a solution, so I'm starting a thread here...

this is what I got from "ndiswrapper-l":
```

lsbcmds : driver installed
	device (14E4:4318 ) present (alternate driver: bcm43xx)

```

fom "lshw":
```

*-network               
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: 0d
       serial: 00:00:39:10:9b:8c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1d:7e:b9:33:1b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
```

and "dmesg":
```

[   36.186910] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   36.392036] ndiswrapper (load_wrap_driver:112): couldn't load driver lsbcmnds; check system log for messages from 'loadndisdriver'
[   36.392188] usbcore: registered new interface driver ndiswrapper
[  190.716654] usbcore: deregistering interface driver ndiswrapper
[  190.865240] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  190.914692] usbcore: registered new interface driver ndiswrapper

```
:confused:

Thanks for your help...

---

### Post by ieee488 on 2008-12-23
[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

---

### Post by silence88 on 2008-12-23
> **ieee488 said:**
> [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

I don't have a "Broadcom B43 wireless driver box" in the Hardware Drivers program. In fact, I don't have any boxes at all.
I've looked through some of the 193 pages in that thread, but at this time I haven't found anything really useful yet.

I've also tried the method from [this thread]("http://ubuntuforums.org/showthread.php?t=734003"), but no luck...

---

### Post by silence88 on 2008-12-24
Any idea why ndiswrapper can't load the driver?

Or what DISABLED means?

Could this driver "b43-pci-bridge" be a problem ?



Alternately, I've tried uninstalling ndiswrapper, and installing the firmware for the b43 driver instead. Now I get a checked box in the Hardware Drivers program but the light is still off.
Is there a way to check that I do have the proper firmware installed?

---

### Post by silence88 on 2008-12-25
Well, looks like the b43 driver finally consented to work after I did a full reinstall of Hardy...
I guess I'll never know why ndiswrapper wouldn't work. :confused:

---

### Post by mahasmb on 2008-12-30
I'm not so sure about this but maybe you needed to blacklist that alternate driver in:

```
 gksudo gedit /etc/modprobe.d/blacklist

```

---

### Post by 77midget on 2008-12-30
just went through a similar issue. I had a script that I ran to get my card working, but did not really understand it (someone else wrote it), so I decided to learn for myself. I found that ndiswrapper was working fine, but that the alternate driver, ssb in my case, was trying to take over. I blacklisted that driver, and then edited etc/modules to load the wl driver that I need after ndiswrapper starts. It all starts as it should now-on boot, without me having to run the script to modprobe -r the ssb driver and modprobe the wl.

---

