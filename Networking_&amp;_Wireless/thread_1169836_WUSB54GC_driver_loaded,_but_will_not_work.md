---
title: "WUSB54GC driver loaded, but will not work"
date: 2009-05-25
forum: Networking &amp; Wireless
---

### Post by colli012 on 2009-05-25
Thanks in advance for any help that can be offered.

Installed Ubuntu 9.04 yesterday, but can not get my wireless-g usb adapter to work, even though it works on my other PC running Windows XP.  The adaptor was made in 01/2007, but does not have a version number listed.

When I run   ndiswrapper   it reads...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
rt73 : driver installed
    device (13B1:0020) present (alternate driver: rt73usb)

When I run   lsusb   it reads...
Bus 001 Device 003: ID 13b1:0020 Linksys WUSB54GC 802.11g Adapter [ralink rt73]

When I run   sudo ndiswrapper -a 13b1:0020 rt73   it reads...
Driver 'rt73' is already used for '13B1:0020'

uname -m = i686

When I run   lshw -C Network  it does not mention the wireless adaptor or mention anthing being unclaimed...
*-network               
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation..........
...and...     
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0....

When I run   sudo modprobe ndiswrapper  it reads...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Could not open '/lib/modules/2.6.28-11-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko': No such file or directory

I have googled WUSB54GC & Ubuntu & rt73  13b1:0020 and tried many things over the past several hours.  Most fixes were from 2006/2007. The approaches I tried didn't wook.  Other approaches let me to bad web links after completing some of the steps.

Under System / Preferences / Network Connections  nothing appears under wireless.

I would greatly appreciate any help that can be provided.

Frank

---

### Post by colli012 on 2009-05-27
I reinstalled 9.04 and tried the WUSB54GC v.1 wireless again.  I've tried several things on the forums and still can not get it to work.  Some of the external links in the forums no longer work.  

I can't even get the driver loaded.  Do I need RT73 or RT73USB?  How do I load it?
Here is some info.

ellie@ellie-desktop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 13b1:0020 Linksys WUSB54GC 802.11g Adapter [ralink rt73]

ellie@ellie-desktop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: c
       bus info: pci@0000:02:0c.0
       logical name: eth0
       version: 78
       serial: 00:06:5b:aa:5d:da
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=3c59x ip=192.168.1.105 latency=64 maxlatency=10 mingnt=10 module=3c59x multicast=yes
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:18:f8:a8:ea:35
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ea:cd:6c:d5:c5:31
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

ellie@ellie-desktop:~$ ndiswrapper -l
-- nothing comes up --

I spent many hours the first go around.  I reinstalled 9.04 and seem to be moving backwards after hours of trying.  The WUSB54GC v1 works with my windows computer.  Do you think installing the previous version of Ubuntu would work.  Would another usb wireless device work.  The forums often recommend the one I have.

Thanks

---

### Post by colli012 on 2009-07-31
I spent over 20 hours over several days trying to get the WUSB54GC to work with Ubuntu 9.04, but it would not work.  I tried everything mentioned in this forum and at other locations online.  I reloaded Ubuntu 9.04 several times and started over from scratch with no results.  I even tried an older wireless access point that I use with my TIVO.  This would not work with Ubuntu either.  The USB port is fine, the access point is recognized, but I could not get it to work following a several compilations of detailed instructions.

SOLVED - (not really) - The solution was to rearrange my daughter's room so that her PC with Ubuntu 9.04 was next to the cable outlet.  I then moved the modem and wireless router to her room and plugged her PC directly into the router.   Her PC with Ubuntu 9.04 accesses the internet just fine now.  My PC with Windows XP now uses the WUSB54GC and it works just fine.  Both PCs are working and have internet access.  Maybe this lo-tech solution will help someone.

I really like the functionality of Ubuntu 9.04.  Except for the wireless issue, the operating system seems to be as good as Windows.  I was able to assemble some old PC parts load Ubuntu and create a great new PC for my daughter.  However, if your only option for internet access for PC is wireless, I would consider other options.  Its not worth the hassle trying to get wireless to work.

---

### Post by Aizawa on 2009-09-23
I found this through google, and thought other's might do so too, so I am sorry for bringing it back from the dead... :)

In 9.04 a WUSB54GC doesn't need to be fiddled with - just plug it in, and it'll work. This was true for 8.10 and most likely 8.04 too (I am sure of this, as I've used one for quite some time now, both in Intrepid and Jaunty).

---

### Post by rorist on 2009-09-24
Depends on the version, my new WUSB54GC Ver. 3 does not work out of the box on Jaunty, neither with the official 2.2.0 drivers from Ralink.

Version 3 has **RT2070L** chip, and should be supported by the **last rt2x00 driver** (rt2800usb). Device ID is **1737:0077** Linksys.

rt2800usb is present in Karmic daily-build, but it does not work with WUSB54GC Rev3. Wireless interface is recognized but link isn't established. Commands are not possible.

rt2x00 2800 drivers is in developement stage and it's not possible to test it right now. So I get we have to wait

---

### Post by tagawa on 2009-10-14
I've found the same thing with 9.10 (Karmic) using WUSB54GC version 3. There is a bug report here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446889](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446889)

If you login to launchpad and click "Does this bug affect you?" it may give the issue more attention.

---

### Post by pgar23 on 2009-10-15
Check out these posts, I read through them and they seem very relevant to your situation. 

1.  [http://ubuntuforums.org/showthread.php?t=225206&highlight=javajake](http://ubuntuforums.org/showthread.php?t=225206&highlight=javajake) (this is the TUTORIAL i used when i used to have that adapter, IT IS FOR version 1 and 2, might work for version 3 but idk, worth a try at least)

2.  [http://ubuntuforums.org/showthread.php?t=1230312&highlight=wusb54gc](http://ubuntuforums.org/showthread.php?t=1230312&highlight=wusb54gc)

3.  [http://linux.derkeiler.com/Mailing-Lists/Debian/2009-08/msg00047.html](http://linux.derkeiler.com/Mailing-Lists/Debian/2009-08/msg00047.html)

---

### Post by pgar23 on 2009-10-15
PS..
Dunno how linux-saavy you are, but I am almost %100 positive that you will need ndiswrapper and making a few modifications to it will probably get your driver up and running.

---

