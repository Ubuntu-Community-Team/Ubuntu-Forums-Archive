---
title: "How can I start the dc driver for ethernet controller"
date: 2010-03-23
forum: Networking &amp; Wireless
---

### Post by Laysan_A on 2010-03-23
Hi,

I just installed the latest version of Mint xfce on my old inspiron 8000 with a microsoft MN-120 pci ethernet card, and though the card shows up as hardware, it is not recognized as a network interface. I believe there is no driver loaded for it.

It's an old card, but it seems the kernel still supports it. There are instructions for activating the dc driver that appears to be the proper driver for this chip set, but those instructions originated from freebsd and I'm not sure they translate well. See here:[http://manpages.ubuntu.com/manpages/lucid/en/man4/dc.4freebsd.html](http://manpages.ubuntu.com/manpages/lucid/en/man4/dc.4freebsd.html)

I did find a kernel config file, but I was afraid to add the suggested lines to it because there were no other lines specifying "devices". They all started with "config".

I'm going to be off line for a while, so I won't be available to reply, but if anyone can offer some pearls of ubuntu wisdom I will appreciate it greatly.

---

### Post by Laysan_A on 2010-03-23
Okay, I did some looking around and decided to put dc in /etc/modules (the ubuntu version of loader.conf?). I rebooted and...nothing. I listed all the loaded modules with modprobe -l and it didn't show.

Any ideas?

---

### Post by Laysan_A on 2010-03-24
Okay, I found a thread where the poster had the same adapter as I. The thread isn't complete, but it's pointing in what I think is the right direction. 
[http://ubuntuforums.org/showthread.php?t=1105037](http://ubuntuforums.org/showthread.php?t=1105037)
It appears that my driver module may be either the tulip module or the dfme module. I've modprobed tulip and there seems to be no change. I'll remove tulip and give dfme a shot. Once more thanks go to chili555, who in my wanderings here seems to help a lot of folks.

UPDATE: Well, it appears the dfme module isn't part of my installation. Oops! It's dmfe, not dfme, and it is located in the tulip folder. I removed tulip and modprobed dmfe, but nothing changed (as far as I could tell). 

I'm beginning to think this isn't a driver issue, per se, but that something is actually preventing ubuntu from recognizing the hardware and associating the drivers - network manager, perhaps?

UPDATE: It seems it might be a kernel issue, and an update to 2.6.31-17 might be necessary (I have the 31-14 kernel). See this thread:
[http://ubuntuforums.org/archive/index.php/t-1338022.html](http://ubuntuforums.org/archive/index.php/t-1338022.html)

---

