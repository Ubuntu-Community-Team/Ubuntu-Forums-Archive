---
title: "Getting ndiswrapper to work with an Atheros-based EUB-362 EXT USB Wireless dongle"
date: 2009-09-26
forum: Networking &amp; Wireless
---

### Post by jr0dy on 2009-09-26
So I have spent two days trying to get this work, and I'm getting nowhere.

I am attempting to set up a wireless broadcaster that will sit next to a router and broadcast WiFi for an adhoc connection over a cantenna to bridge two houses in a rural area.

Therefore, given the nightmare of ICS in Windows, I was hoping to accomplish this with an Ubuntu box.  From what I can tell, my only option is ndiswrapper since madwifi apparently doesn't support USB devices.  However, I am at a standstill at this point.

I have been using this site as an outline thus far: [http://www.keenansystems.com/nub362_eub362_linux_ndiswrapper_driver_howto.htm](http://www.keenansystems.com/nub362_eub362_linux_ndiswrapper_driver_howto.htm)

However, things go awry once I get to the load_fw_ar5523 ar5523.bin 0cf3 0002 command, which supposedly was rendered obsolete with ndiswrapper-utils-1.7 and later (currently running the 1.9 ver. supplied through Synaptic).  The problem is, my card will not engage without it; I have found some other sites which have recommended, in addition to loading the net5523.inf driver, loading athfmwdl.inf, which does nothing for me other than put another nonfunctional device in my network device list.

Without doing this, the light never lights on my device, nor does a wlan0 device appear - which is confirmed when I attempt to bind wlan0 mentioned towards the end of the aforementioned tutorial, and it tells me that 'WLAN0' is not a valid device ID.

The only thing I can think of at this point is to track down an old version of ndiswrapper-utils, from prior to 1.7, which has proven impossible for me.  Has anyone else had experience with this?  Unfortunately many of the existing threads on the topic are pretty old and applicable to old distros, etc.  For this reason, I have tried this in both Ubuntu 9.04 and 8.04, with identical results.

If someone could help me out I would be incredibly grateful.  If someone could just point me somewhere where I can download an old version of ndiswrapper-utils and a ndiswrapper build that works with it, I think I'll be able to take it from there.

---

### Post by jr0dy on 2009-09-29
In the past three days, I have also tried Hardy and Intrepid with no luck.  I'm actually about to go all the way back to Dapper.  I have been trying to solve the many compile errors that result when attempting to compile ndiswrapper-1.6 from source on a newer kernel and have just about driven myself crazy - I don't code aside from messing around AutoHotKey in Windows, so it's been a challenge to say the least.  I did recently stumble across the following:
> 
1.
Card: Linksys WUSB54GSC, 802.11b/g, USB 2.0

*
Chipset: Broadcom
*
USBID: Vendor=13b1 ProdID=0026 (13b1:0026)
*
Driver: Downloaded driver [http://www.linksys.com/servlet/Satel...VisitorWrapper](http://www.linksys.com/servlet/Satel...VisitorWrapper) here and install. Copied the win files (usb8023.sys and rndismp.sys) from the F5D7051.exe F5D7051 Drivers download to the /etc/ndiswrapper/wusb54gsc/ folder. Lastly, use the script detailed HOWTO: WUSB54GS v1 (only?) on (X)(K?)Ubuntu - Ubuntu Forums here , modidifed with the correct USB ProdID (0026), to get the power working. It’s in the section ‘Getting WUSB54GS to Work in Edgy and Feisty’ Also check out the thread Is WUSB54GS (SpeedBooster) linux-friendly? - Page 3 - LinuxQuestions.org here for why the script is needed and works.
*
Other: With 2.6.16 and later kernels, RNDIS devices are not initialized (when device is plugged in, nothing happens). To get it going, you need to set the variable bConfigurationValue in sysfs. An easy way to do this is to add this: BUS==”usb”, SYSFS{idProduct}==”0026”, SYSFS{idVendor}==”13b1”, PROGRAM=”/bin/sh -c ‘echo 1 > /sys/%p/device/bConfigurationValue’” to /etc/udev/rules.d/<ruleFilename> file and restart udev. For FC6 <ruleFilename> is 50-udev.rules.

I found it here: [http://www.linuxforums.org/forum/linux-applications/100649-ndiswrapper.html]("http://www.linuxforums.org/forum/linux-applications/100649-ndiswrapper.html")

Can someone tell me if this is also applicable to Atheros chipsets?

I neglected to specify the manufacturer (if it's even applicable), which is EnGenius.  Might help others to find this thread at least.

From everything I've found, ar5523 devices are extremely poorly supported all-around.  I'm going nuts here, but I really can't afford to replacement devices.

---

### Post by cariboo on 2009-09-29
Depending on the device, it may already be detected and the driver loaded. What is the output of:

```
lsusb
```

and

```
sudo lshw -C network
```

Edit: you can create text files by appending > filename.txt to the end of each command, where filename is whatever you want to call it.

---

### Post by jr0dy on 2009-09-30
Thanks for your response, cariboo907 - I appreciate it.

Output of lsusb:

```

lsusb
Bus 005 Device 003: ID 0cf3:0002 Atheros Communications, Inc. AR5523 (no firmware)
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04fc:0003 Sunplus Technology Co., Ltd CM1092 Optical Scroller Mouse
Bus 001 Device 002: ID 047b:0011 Silitek Corp. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Output of sudo lshw -C network:

```

sudo lshw -C network 
  *-network               
       description: Ethernet interface
       product: RTL8139 Ethernet
       vendor: D-Link System Inc
       physical id: c
       bus info: pci@0000:00:0c.0
       logical name: eth0
       version: 10
       serial: 00:50:ba:56:98:2e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.100 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 2e:10:ca:7a:48:52
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

As you can see, the wireless device does not appear to be recognized whatsoever.

---

