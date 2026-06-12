---
title: "Wireless driver update kills wired and wireless connection"
date: 2011-06-12
forum: Networking &amp; Wireless
---

### Post by Bucky Ball on 2011-06-12
Hi all,

*** UPDATE: This card now fixed in 11.04 kernel. See post #24 here: [http://ubuntuforums.org/showthread.php?p=11133342#post11133342](http://ubuntuforums.org/showthread.php?p=11133342#post11133342)

Sitting here tweaking and loving my new minimal install of Ubuntu 10.04 LTS with xfce4 DE. Smooth and fast and all working great ... until I updated the Realtek wireless driver. From 'lshw -C network':

```
*-network
       description: Wireless interface
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 10
       serial: b4:82:fe:3c:ad:72
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=**0019.1207.2010 **firmware=63 ip=192.168.0.111 latency=0 multicast=yes wireless=802.11bg
       resources: irq:17 ioport:2000(size=256) memory:d4000000-d4003fff
```The part in bold is the new driver. Previously it had a driver beginning with 0015. But that is all I remember. Of course, I should have backed up this file before tweaking it so don't waste time on that oversight ... ;)

I don't want to dig myself too much of a hole as it was working perfectly before (in fact wireless worked 'out of the box' in 10.04 which it didn't in my 10.10 install) so things can't be too much different. This is obviously something simple, I just can't figure what. Maybe I uninstalled something which has affected the network setup without me being aware. 

Naturally, what I would do first is revert back to the old driver, but as all I remember is it started with 0015. that could be tricky. Realtek don't seem to have anything like that on their website at this point.

I have a working and connected 10.10 install on the same machine so was able to copy the contents of /etc/network/interfaces and /etc/hosts to the 10.04 install (this time making copies of the originals so I could swap 'em back) but no difference.  

Neither wired or wireless are working on the 10.04 side now, although I can ping my router via the wired connection, but that is about it. Can't figure what made it change so radically or why the 0019. driver is working in 10.10 but not 10.04? (Realtek have a lot of drivers with different names but when you download them they are in fact the same driver!)

Any help or ideas much appreciated, just ask for required info. Things were looking sweet for about fifteen hours until I decided to fix a perfectly operational wireless driver: Thus, if it ain't broke, don't fix it! Tnx in advance ...

* PS: In lspci on 10.10 the card is described as 

```
Network controller: Realtek Semiconductor Co., Ltd. **RTL8191SEvB** Wireless LAN Controller (rev 10)'

```... while in 10.04, the dysfunctional one, the line looke like this:

```
Network controller: Realtek Semiconductor Co., Ltd. **Device 8172** Wireless LAN Controller (rev 10)
```

---

### Post by Bucky Ball on 2011-06-12
Have located the older 0015 driver and am going to install and see what happens. It just dawned on me: I did a 'sudo apt-get autoremove'. I reckon that might have dislodged something.

Is there any way I can see what was 'autoremoved' and re-install those packages to see if it makes a diff? If I do that and install the older 0015 driver things should be just about how they were. More I think about it the more I'm thinking the autoremove ripped out some of the dependencies. Remember, there is not much running on this machine as minimal install. A bit fragile at this point and trying to tread lightly ...

---

### Post by Bucky Ball on 2011-06-12
Yep, putting things back the way they were worked. Installed the 0015 driver and /etc/network/interfaces and /etc/hosts are as they were and all is good. But the wired connection is now not working. Not to worry, I'll get around to it. At least the 10.04 install is now back online and easier to work on ...

---

