---
title: "Belkin F5D7050 Wireless"
date: 2009-06-25
forum: Networking &amp; Wireless
---

### Post by cdawley4 on 2009-06-25
Hi,

I have a Belkin F5D7050 v3000 adapter that I am trying to get to work better.  The reason I want to get this one working is I have a PCMCIA card that has been through a lot and is about to break, so I decided to use my extra USB wireless card.

I tried to get the Belkin adapter to work using ndiswrapper -i rt73.inf from the terminal.  That was no help.  I did, however, run across another post to use ndisgtk found in Synaptic Package Manager that I used to install the driver with.  That is working for right now.

The only problem I have with it at the moment is that whenever I reboot my laptop, the usb wireless isn't recognized, until I unplug it and plug it back in a few times.  Sometimes, that won't work and I have to reboot.

I would like to get the USB wireless card working without having to start the ndisgtk program everytime.

```
chris@chris-laptop:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
rt73 : driver installed
	device (050D:705A) present (alternate driver: rt2500usb)

```

[COLOR="Blue"]The only thing I see that doesn't make sense is the rt2500usb driver.  Would it help if I tried to install that driver?[/COLOR]

```
chris@chris-laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 015: ID 050d:705a Belkin Components F5D7050A Wireless Adapter
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

```
chris@chris-laptop:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:14:22:ba:76:d3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       configuration: latency=0
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 06:7c:c6:6b:31:de
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
  *-network:1 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan1
       serial: 00:1c:df:1c:24:00
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+rt73 driverversion=1.53+Belkin,08/02/2005, 1.00.00. multicast=yes wireless=IEEE 802.11g
chris@chris-laptop:~$ 

```

I am very sorry for the long post.  I hope the ndisgtk program will at least help other people out that are having problems with installing their network adapters.  I also hope someone will have some solutions for me to try.  Any help will be appreciated.  Again, I am very sorry for the long post.

Thanks,

Chris

---

### Post by MaindotC on 2009-06-25
I just plug mine and it uses the zd1211rw module.  nm-applet says it's only getting 24 mbps and it disconnects once in a while which is a drag.

[[IMG]http://img385.imageshack.us/img385/8484/screenshotconnectioninf.png[/IMG]](http://img385.imageshack.us/i/screenshotconnectioninf.png/)


Doesn't really seem to detect it properly:
```

 *-network:0
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:11:50:b2:0e:ec
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.104 multicast=yes wireless=IEEE 802.11b/g

```

  I'm watching this thread.  According to lshw it looks like it's using the proper ndiswrapper driver :(

---

