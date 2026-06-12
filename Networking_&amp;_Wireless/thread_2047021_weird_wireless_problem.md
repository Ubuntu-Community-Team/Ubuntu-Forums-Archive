---
title: "weird wireless problem"
date: 2012-08-24
forum: Networking &amp; Wireless
---

### Post by hacker804 on 2012-08-24
Hi.I have a USB wireless adapter TL-WN422G.It works fine in Lubuntu and i can connect to my router but this is true only when i am near the router.when i get far from it,lubuntu fails to find the router.On the other hand in windows xp the adapter connects fine when i am far away.

Please help.What problem is this:mad:

---

### Post by Bucky Ball on 2012-08-24
Welcome. What release of Ubuntu (12.04 LTS Desktop?). Please open a terminal (Applications>Accessories>Terminal) and provide the output of these two commands:

```
sudo lshw -C network
iwconfig
```Please use code tags by clicking 'Go Advanced' under the editing post window, mark the code (your output) and click the hash icon (#). Cheers. ;)

---

### Post by hacker804 on 2012-08-24
I am running Lubuntu 12.04

Here is the output:
sudo lshw -C network
```

 *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@0000:02:0a.0
       logical name: eth0
       version: 10
       serial: 00:0a:e4:4f:d4:5b
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:11 ioport:3000(size=256) memory:e0200000-e02000ff memory:14000000-1400ffff
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@1:5
       logical name: wlan0
       serial: 00:25:86:ee:44:74
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=zd1211rw driverversion=3.2.0-23-generic firmware=4725 ip=192.168.1.8 link=yes multicast=yes wireless=IEEE 802.11bg
```

AND
iwconfig
```
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Apple AirPort"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 54:E6:FC:A4:DA:EA   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=5/100  Signal level=5/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1081  Invalid misc:223   Missed beacon:0

eth0      no wireless extensions.

```

When i ran sudo lshw -C network my router showed up??

---

### Post by Bucky Ball on 2012-08-24
You could try this:

> Download this file to your desktop: [http://www.orbit-lab.org/kernel/comp...6.39-1.tar.bz2]("http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.39/compat-wireless-2.6.39-1.tar.bz2")

#tar xjvf compat-wireless-2.6.39-1.tar.bz2
#cd compat-wireless-2.6.39-1
#./configure
#sudo make && sudo make install

 after that reboot.Post #86 from here:

[http://ubuntuforums.org/showthread.php?t=1473867&page=9](http://ubuntuforums.org/showthread.php?t=1473867&page=9)

It appears your TP-Link dongle uses an Atheros wireless chipset, I'm just trying to figure out which. I presume you are using 12.04 LTS? With the dongle plugged in, could you give the output of this:

```
lsusb
```Do you see 'Atheros' anywhere there? Just out of curiousity, is there anything in Additional Drivers (do an update with the dongle in first). Madwifi is specifically for Atheros. You might have more luck with that instead of Network Manager. Some do:

[http://sourceforge.net/projects/madwifi/](http://sourceforge.net/projects/madwifi/)

That is the download link, their homepage seems to be down at the moment.

---

### Post by hacker804 on 2012-08-24
here is lsusb:
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0ace:1215 ZyDAS ZD1211B 802.11g
```

---

### Post by hacker804 on 2012-08-25
BUMP
Please someone help

---

### Post by lakerssuperman on 2012-08-25
Several questions:

1) You say your works fine in Ubuntu, but Lubuntu it fails to connect at distance.  Are you installing both separately or are you installing the Lubuntu desktop on top of your Ubuntu install?

2) If you are installing Ubuntu and Lubuntu separately, did you run both with the latest updates and were you prompted to install any restricted drivers?

---

### Post by Bucky Ball on 2012-08-26
> **lakerssuperman said:**
> Several questions:

1) You say your works fine in Ubuntu, but Lubuntu it fails to connect at distance.  Are you installing both separately or are you installing the Lubuntu desktop on top of your Ubuntu install?

2) If you are installing Ubuntu and Lubuntu separately, did you run both with the latest updates and were you prompted to install any restricted drivers?

I think you have misunderstood OP. They mention nothing about booting Ubuntu, only Lubuntu. ;)

---

### Post by Miljet on 2012-08-26
> 1) You say your works fine in Ubuntu, but Lubuntu it fails to connect at distance. Are you installing both separately or are you installing the Lubuntu desktop on top of your Ubuntu install?

I do believe that the OP said that wireless only worked for a short distance with Lubuntu, but worked fine under XP. He said nothing about having Ubuntu installed at all.

@hacker804
> When i ran sudo lshw -C network my router showed up?? 
What makes you ask this?  The only thing I am seeing is your Ethernet (wired) connection and your wireless connection.

---

### Post by Bucky Ball on 2012-08-26
> **Miljet said:**
>   The only thing I am seeing is your Ethernet (wired) connection and your wireless connection.

+1. This is the bit that's relevant:

```
*-network        
description: Wireless interface
physical id: 2        
bus info: usb@1:5        
logical name: wlan0        
serial: 00:25:86:ee:44:74        
capabilities: ethernet physical wireless       
configuration: broadcast=yes **driver=zd1211rw driverversion=3.2.0-23-generic** firmware=4725 ip=192.168.1.8 link=yes multicast=yes wireless=IEEE 802.11bg
```The part in bold would signify that the driver being used is part of the kernel being used. This may or may not be good.

* Just did a bit more research and this all looks right. That is the correct driver. No idea about the firmware, though. I also notice this from your iwconfig:

```
Link Quality=5/100  Signal level=5/100
```Appalling. No wonder you're getting problems. That should be up 50+/100.

* Further update: You could try this:

                      > Looking for the latest version? **             [                 Download zd1211-firmware-1.4.tar.bz2 (39.1 kB)]("http://sourceforge.net/projects/zd1211/files/latest/download?source=files")**[B][]("http://sourceforge.net/projects/zd1211/files/latest/download?source=files")

[/B]Download and extract and there should be a 'Read Me' file telling you how to install.[B]
[             ]("http://sourceforge.net/projects/zd1211/files/latest/download?source=files")             [/B]

---

### Post by hacker804 on 2012-08-26
> **lakerssuperman said:**
> Several questions:

1) You say your works fine in Ubuntu, but Lubuntu it fails to connect at distance.  Are you installing both separately or are you installing the Lubuntu desktop on top of your Ubuntu install?

2) If you are installing Ubuntu and Lubuntu separately, did you run both with the latest updates and were you prompted to install any restricted drivers?

1.I tested my adapter on Ubuntu LiveCD.It wasnt installed on my system.I installed only Lubuntu

2.No,it did'nt ask me for the restricted drivers.

This is a very strange problem.Sometime it connects fine while sometimes it does'nt show at all.It works fine in Windows XP.Should i try it on Xubuntu?

Thanks for all the help

---

### Post by Bucky Ball on 2012-08-26
Probably wouldn't make any difference as the Ubuntu base installs (the nuts and bolts) are identical. Say the prob is 12.04. 

Please read my previous post #11 for further suggestions. You could also try Madwifi instead of Network Manager.

---

### Post by hacker804 on 2012-08-26
> **Bucky Ball said:**
> Probably wouldn't make any difference as the Ubuntu base installs (the nuts and bolts) are identical. Say the prob is 12.04

This is what confuses me.Why does it run on ubuntu.Does the version make a difference?

I tried it on Ubuntu 11.04 and it worked but not running on Lubuntu 12.04?

---

### Post by Bucky Ball on 2012-08-26
Different kernels for a start. 11.04 uses 2.6 kernel still I think (don't quote me) and 12.04 is at 3.2 at the moment. Think 12.10 is currently using 3.4 kernels for testing. 

Think of it like this: If you wanted to do a minimal install you would download the minimal install ISO. It installs on next to nothing. You have the linux kernel that is tweaked to be the Ubuntu base kernel. You then get the option to add what you want; DE, apps, file manager, etc., and create your flavour.

Before you install anything else you basically have a command line system that doesn't do a lot. If you decide to install KDE with no Kubuntu apps but all Xubuntu apps, do the research then go ahead and try it. You can create whatever techno Frankenstein Linux hybrid you like (with some effort). ;)

But, it is obvious from all this that finding bugs can be difficult, especially on home-built computers, as they can depend on the hardware configuration, the software config, or both.

---

