---
title: "Need help with BCM 4318 on 10.04 Lucid 32 bit OFFLINE"
date: 2010-12-17
forum: Networking &amp; Wireless
---

### Post by Allmont on 2010-12-17
So, i'm a new user to ubuntu, sort of, its driven me away many times, and i've always come back for more.

Problem this time is i have no internet.

I'm using the Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
and been having LOTS of fun with it.

It doesn't show up in the network manager, obviously
I did what i could with trying to get it to work through ndiswrapper to no avail, and i'm starting to get tired of all these vague offline installations telling me to go download a file called 'patch' for obviously stupid reasons.


So some info:

I'm using 10.04 Lucid, a fresh install, 32bit
I HAVE NO INTERNET CONNECTED LINUX COMPUTERS and getting this one a hard connection is out of the question.

lshw -c network gives me this 
```

sudo lshw -c network

*-network
description: Ethernet interface
product: NetXtreme BCM5751 gigabit ethernet pci express
vendor: Broadcom Corp
physical id: 0
bus info: pci@0000:04:00.0
logical name: eht0
version: 01
serial: 00:13:72:1e:3b:2a
size: 100MB/s
capacity: 1GB/s
width: 64 bits
clock: 33MHz
capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt-fd 100bt-fd 1000bt-fd 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=full firmware=5751-v3.44a latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
resources: irq:17 memory:fe7f0000-fe7fffff

*-network
description: Network controller
product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Conroller
vendor: Broadcom Corp.
physical id: 5
bus info; pci@0000:05:05.0
version: 02
width: 32 bits
clock: 33mhz
capabilities: bus_master
configuration: driver=b43-pci-bridge latency=64
resources: irq:17 memory:fe6fe000-fe6fffff

```

ndiswraper -l :
```

allmont@ubuntu:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
wmp54gs : driver installed
	device (14E4:4318) present (alternate driver: ssb)
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
wmp54gsa : driver installed
	device (14E4:4318) present (alternate driver: ssb)

```

and my blacklist file (i have blacklist and blacklist.conf the same)

```



# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist b43
blacklist b43legacy
blacklist ssb

```

Help me out please, i've got no idea what to do. Best thing i can do for getting files is downloading them to a flash drive and plugging it into the linux computer.
If you need any more info i'll post it as requested.

I've got no idea whats going on, but according to my lshw isn't the wireless driver installed?
i don't really know if its working, since there is no wireless option in my network manager.

---

