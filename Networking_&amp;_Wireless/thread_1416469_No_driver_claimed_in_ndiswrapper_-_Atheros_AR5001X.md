---
title: "No driver claimed in ndiswrapper - Atheros AR5001X+ Wireless Network Adapter"
date: 2010-02-26
forum: Networking &amp; Wireless
---

### Post by darramonde on 2010-02-26
I recently switched from Windows XP to a clean install Ubuntu Karmic Koala 9.10 but it seems to be quite a problem to get the wifi up and running. 

In Windows the nearby network all appeared in network connections but the same section in Ubuntu is empty. So I decided to go with the ndiswrapper guide to solve the problem with an unclaimed driver. After an entire day messing with my computer I'm still not close...

Below follows excerpts taken from the Ndiswrapper guide with posted results from my computer.

"ndiswrapper won't work until it thinks that your Windows drivers have been properly installed and that they are the appropriate ones for your wireless card. You can run the command: **ndiswrapper -l**"

_result:_

WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
net5211 : driver installed
	device (168C:0013) present (alternate driver: ath5k)

So I've posted the result the name of my wireless card below: **lspci -nn**

_Result:_

00:00.0 Host bridge [0600]: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge [1106:0259]
00:00.1 Host bridge [0600]: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge [1106:1259]
00:00.2 Host bridge [0600]: VIA Technologies, Inc. CN333/CN400/PM880 CPU Host Bridge [1106:2259]
00:00.3 Host bridge [0600]: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge [1106:3259]
00:00.4 Host bridge [0600]: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge [1106:4259]
00:00.7 Host bridge [0600]: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge [1106:7259]
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8237/VX700 PCI Bridge [1106:b198]
00:06.0 Ethernet controller [0200]: Atheros Communications Inc. Atheros _AR5001X+ Wireless Network Adapter_ [168c:0013] (rev 01)
00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.3 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 82)
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8235 ISA Bridge [1106:3177]
00:11.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 50)
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 74)
01:00.0 VGA compatible controller [0300]: VIA Technologies, Inc. CN400/PM800/PM880/PN800/PN880 [S3 UniChrome Pro] [1106:3118] (rev 02)

I also tried to check if the device was claimed by another driver: _Command_:B] ndiswrapper -l[/B]

WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
net5211 : driver installed
	device (168C:0013) present (alternate driver: ath5k)

"To check whether another driver is trying to claim your device, use the command **lshw -C Network.**"

*-network:0 UNCLAIMED   
       description: Ethernet controller
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 6
       bus info: pci@0000:00:06.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=128 maxlatency=28 mingnt=10
       resources: memory:7c000000-7c00ffff
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:40:d0:93:e9:12
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 ip=192.168.0.107 latency=128 maxlatency=8 mingnt=3 multicast=yes
       resources: irq:11 ioport:e200(size=256) memory:d0000000-d00000ff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

It seems like the network is disabled or unclaimed or both. What to do? 
I'm stuck after spending an entire day trying to install the wifi. I had no problems in Windows XP but it seems to be quite impossible in Ubuntu. Help me please, anyone?

---

### Post by kerry_s on 2010-02-26
9.10 is a bad ubuntu, try 9.04 it should work from the get go. make sure it works with the live cd first before you install.

[http://releases.ubuntu.com/9.04/](http://releases.ubuntu.com/9.04/)

---

### Post by darramonde on 2010-02-26
I'd prefer not to roll back the Ubuntu 9.10 installation and solve the problem...

---

### Post by bkratz on 2010-02-26
> **darramonde said:**
> I'd prefer not to roll back the Ubuntu 9.10 installation and solve the problem...

This may be worth looking at (maybe not!)

[http://ubuntuforums.org/showpost.php?p=8232629&postcount=3](http://ubuntuforums.org/showpost.php?p=8232629&postcount=3)

---

### Post by darramonde on 2010-02-26
> **bkratz said:**
> This may be worth looking at (maybe not!)

[http://ubuntuforums.org/showpost.php?p=8232629&postcount=3](http://ubuntuforums.org/showpost.php?p=8232629&postcount=3)


As i said, I'm kind of a novice when it comes to Ubuntu and the Linux concept. How do I add** #blacklist ath5k** in **/etc/modprobe.d/madwifi.conf:**?

---

### Post by bkratz on 2010-02-26
Are you using madwifi at all? Apparently it went obsolete in about December of 2009.  It looks like from your earlier post the driver used is 

net5211 : driver installed
device (168C:0013) present (alternate driver: ath5k)

so blacklisting the ath5k might have been enough.  Most of the threads I have seen for Atheros devices recommend adding the following:


sudo apt-get install linux-backports-modules-karmic


Here is a typical posting, although it specifically mentions the 928x series the theory should hold true. Believe me i am no expert in Atheros--just  good at searching threads!

[http://art.ubuntuforums.org/showpost.php?p=8648042&postcount=1](http://art.ubuntuforums.org/showpost.php?p=8648042&postcount=1)

---

### Post by darramonde on 2010-02-26
> **bkratz said:**
> Are you using madwifi at all? Apparently it went obsolete in about December of 2009.  It looks like from your earlier post the driver used is 

net5211 : driver installed
device (168C:0013) present (alternate driver: ath5k)

so blacklisting the ath5k might have been enough.  Most of the threads I have seen for Atheros devices recommend adding the following:


sudo apt-get install linux-backports-modules-karmic


Here is a typical posting, although it specifically mentions the 928x series the theory should hold true. Believe me i am no expert in Atheros--just  good at searching threads!

[http://art.ubuntuforums.org/showpost.php?p=8648042&postcount=1](http://art.ubuntuforums.org/showpost.php?p=8648042&postcount=1)

I've already added the karmic backports and it didn't help at all.

---

### Post by darramonde on 2010-03-05
I tried to check if there's any kind of connection to the router, but I'm stuck with the same problem. What to do?

**iwconfig**

lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

---

