---
title: "RT2870/RT3070 Ralink Driver Bug"
date: 2010-10-29
forum: Networking &amp; Wireless
---

### Post by s|icer on 2010-10-29
I am making this thread to announce a bug, as well as perhaps give a few newbies ways to get around this quicker.

I started out rebooting my machine over and over because NetworkManager wouldn't connect to my network (wireless, obviously). Ubuntu 10.10 Maverick comes with this:
```
slicer@slicertool:~$ modinfo rt2870sta
filename:       /lib/modules/2.6.35-22-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
version:        2.1.0.0
license:        GPL
description:    RT2870/RT3070 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
firmware:       rt3071.bin
firmware:       rt3070.bin
firmware:       rt2870.bin
srcversion:     93E93E3E336F412601AF0FA

```
And apparently this doesn't work well. To get it to connect, rather than rebooting endlessly I just started doing:
```
sudo killall NetworkManager
```
and then attempting to reconnect.

Something that may (if only to my imagination) have sped up the process of getting a successful connection was blacklisting rt2800usb, rt2x00usb and rt2x00lib.
```

gedit /etc/modprobe.d/blacklist.conf

```
Add these lines to the bottom:
```

# Blacklist borked RT28xx drivers so RT2870STA will work.
rt2800usb
rt2x00usb
rt2x00lib

```

I also then went to Ralink's website, to try to get the new drivers for Linux. They do have 2010_0709_RT2870_Linux_STA_v2.4.0.1 out as their latest driver, however it works with the generic kernel that was on the 10.4 release of Ubuntu..whichever one that may be and not the most current release.

Any further insight or attention of the devs would be excellent.

---

### Post by ahsile on 2010-10-30
I'm actually in the same boat. I just installed Ubuntu 10.10 on my parents' old PC. They use a wireless usb dongle (DLINK DWA-125) in order to connect to the wifi network they have at home.

I've been struggling with this for hours! Basically I'm to the point where I've compiled the drivers from ratech. I can plug in the dongle and unplug it and the driver (rta3370sta) will load and unload properly. 

Network manager will not find any wireless networks at all... It continues scanning over and over, but never gets anywhere.

If I use iwlist, on the other hand... The networks in my area are seen perfectly fine.

Does anyone have a clue why this might be?

---

### Post by ahsile on 2010-10-30
I rolled the PC back to 10.04 and followed the instructions the following post, which made everything work again. The only change I made was replacing the id from lsusb with my own.

[http://ubuntuforums.org/showpost.php?p=9445731](http://ubuntuforums.org/showpost.php?p=9445731)

I don't know if it will work for 10.10 though...

---

### Post by chili555 on 2010-10-30
> I don't know if it will work for 10.10 though...I believe it will. > the driver (rta3370sta) will load and unload properly. I think you mean rt3070sta. It has been merged with rt2870sta:```
$ modinfo rt2870sta
filename:       /lib/modules/2.6.35-22-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
version:        2.1.0.0
license:        GPL
description:    RT2870/[COLOR="Red"]RT3070[/COLOR] Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
firmware:       rt3071.bin
firmware:       [COLOR="Red"]rt3070[/COLOR].bin
firmware:       rt2870.bin
```

The quirk that two or more driver modules claim the same device requiring blacklisting is known. There are many posts here about rt2800usb especially. Nontheless, the newbies, searchers and I appreciate a reminder.

---

### Post by ahsile on 2010-10-30
Aye, you are correct I made a typo on the module name :)

I think the root of the issue is that (as a launchpad bug I found states), the rt3070sta driver was depreciated, and some of the cards which were mapped to it were not remapped to the rt2870sta module.

By adding the mappings the linked post recommends, everything gets loaded properly again.

Since I've got things working in 10.04 I'll most likely leave it as is. My parents don't need the latest and greatest.

---

### Post by fivetide on 2010-12-12
so, i got it working for my belkin device (050d:935a).
previously i used rt3070sta v2.1.2., and after failing never version of 2870 i patched my old driver similar to what they do here:
[http://www.linuxcrew.de/2010/10/11/rt2870-compile-error-under-kubuntu-maverick-10-10/?lang=en](http://www.linuxcrew.de/2010/10/11/rt2870-compile-error-under-kubuntu-maverick-10-10/?lang=en)


so step by step:

grab the sources for rt3070 

edit include/iface/rtmp_usb.h with some editor..

change lines 99 & 100 to

[PHP]#define RTUSB_URB_ALLOC_BUFFER(pUsb_Dev, BufSize, pDma_addr)            usb_alloc_coherent(pUsb_Dev, BufSize, GFP_ATOMIC, pDma_addr)
#define RTUSB_URB_FREE_BUFFER(pUsb_Dev, BufSize, pTransferBuf, Dma_addr)    usb_free_coherent(pUsb_Dev, BufSize, pTransferBuf, Dma_addr)
[/PHP]make && make install && modprobe rt3070sta

voila!

---

### Post by damanbaird on 2011-10-07
so whats the real solution for rt3071 for ubuntu?

---

