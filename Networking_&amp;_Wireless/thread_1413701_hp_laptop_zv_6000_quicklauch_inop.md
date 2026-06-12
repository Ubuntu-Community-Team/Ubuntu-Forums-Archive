---
title: "hp laptop zv 6000 quicklauch inop"
date: 2010-02-22
forum: Networking &amp; Wireless
---

### Post by Seraphimfishy on 2010-02-22
SO i have an hp zv 6000 laptop.   I cant get the wifi button to turn on.    It sees the card  has drivers loaded but because the quicklaunch will not function i cant get the thing to turn on.  is there a way to force the hardware on by bypassing the buttons.  Some of the button do work though.  the music button brings up the media player.

My system is a dual boot with xp.   buttons work with xp.    wlan on in bios.   if windows is not running i cant make the button work.  just so you know i am   kinda a noob at ubuntu.  used to run redhat back in compsci days.  been a while.

 *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:03:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:21 memory:b0204000-b0205fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:78:55:8f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.102 latency=128 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:22 ioport:a000(size=256) memory:b020a400-b020a4ff
  *-network DISABLED
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:14:a5:27:50:3c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

---

### Post by northd_tech on 2010-02-22
Hi.  I've got a HP DV98xx laptop, but it has the Broadcom "4328", which has an external slide switch (2 position- left/right with 2 different color LEDs), not a button.  If I'm understanding you correctly, yours has a single button that you push one time for on and another time for off (I think my Mom's old Compaq laptop had that kind IIRC).

Anyway, before I got my wireless figured out, the LED was always orange regardless of the switch position- it was NEVER blue/"working" (which I think is what you are describing).

From what you posted yours is a Broadcom 4318 wireless.  Broadcom has released a proprietary driver for that that you need to grant permission for it to use (kind of a technicality thing).  You go into System > Administration > Hardware drivers and see if there is any kind of a Broadcom driver listed (you also might see an ATI or NVIDIA video driver in there).

I'm pretty sure that the 4318 prefers the "b43" driver if you see that option, try to Activate it.  If the wireless still doesn't work, or if you don't see any drivers listed in there, then we have more work to do.

The 4318 has been discussed a lot lately here- I will give you a link that should take you to some of the newer threads.  You might want to read those a little before we change too many things.

Also if you could copy/paste the results here when you run the following commands in a terminal window, that would help to see what you have currently:

```
lsmod

ifconfig

iwconfig

sudo iwlist scan

cat /etc/modules

cat /etc/modules.conf

cat /etc/modprobe.d/blacklist

cat /etc/modprobe.d/blacklist.conf
```

That will be a lot of info- you might want to save it into a text editor- Kate and gedit are the nicer ones in ubuntu.  If you go to Applications > Accessories > Kate will find that, or if you type "gedit" in a terminal window should open up gedit (which most people prefer, but they're both good).  If you need to post from another machine, saving that text file to a USB stick is a good idea.

On the Red Hat thing- I hear you there brother!  That (and OLD school UNIX) were mainly what we used at my university, then I later used Mandrake, and Fedora, and Scientific Linux, and ...

Ubuntu is much more "user friendly" though, no?  I've even seen it hacked into a Mac-ish OS without much difficulty.

OK- here's all that reading on Broadcom 4318 wireless:

[http://ubuntuforums.org/tags.php?tag=broadcom+4318](http://ubuntuforums.org/tags.php?tag=broadcom+4318)

---

### Post by Seraphimfishy on 2010-02-25
no one huh..........geez i must have stumped the forums;)   Looks like i am gonna go get a pc card....... wish i didnt have to.

---

### Post by Seraphimfishy on 2010-02-27
so does ubuntu fix it self.   because quicklauch works now??????????????????  oh well.

---

