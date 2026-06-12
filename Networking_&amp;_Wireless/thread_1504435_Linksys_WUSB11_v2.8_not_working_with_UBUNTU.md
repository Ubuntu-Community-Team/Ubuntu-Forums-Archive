---
title: "Linksys WUSB11 v2.8 not working with UBUNTU?"
date: 2010-06-08
forum: Networking &amp; Wireless
---

### Post by Jurgen Oscar on 2010-06-08
Hello guys,

I had been searching on this post, and almost come to a conclusion,
that the Linksys USB Wifi Adapter (WUSB11 v2.8) does not work with UBUNTU.

I am using UBUNTU DESKTOP 64-bit (x86_64) 10.04, but I think it is not
working in the 32-bit version as well.

I really love to get my Ubuntu work with my 64-bit hardware....

Could somebody help me please?

Or is there anybody could confirm that this is not going to work,
so I just need to dump my USB wifi adapter and move on.

Thanks a lot.

Cheers,
J.O
:-({|=

---

### Post by ibe2fly4chu on 2010-06-08
I cannot confirm that it works with 64 bit architecture. However if you are having trouble with a wireless adapter in about 95% of the cases, ndiswrapper will get you up and running. Now now, i know alot of people hate ndiswrapper because there are guides written to get you through it that simply confuse you even more (dont worry they make perfect sense after you have used the thing once via terminal  lol ^^). To make life easier i would suggest you follow these steps:

First pop your live cd in while logged into ubuntu.

Open the live cd, and navigate to pool/main/n
Install the ndiswrapper .deb files 

after installing the 2 files in the ndiswrapper folder, navigate to the ndisgtk folder and install that file as well.

At this point you might want to download your windows drivers for the usb adapter. (preferably xp..it is just my personal opinion that xp drivers work best with ndiswrapper).

Open Terminal and type: sudo ndisgtk
This should open the simple to use GUI for ndiswrapper. simply plug your adapter in, and choose the driver file you downloaded. Hit install and you should be good. 

Just a quick note: Alot of windows drivers are provided in .EXE file extensions. To use ndiswrapper you have to extract it..which will in turn provide something that looks like: "wirelessadapter.inf" AND "wirelessadapter.sys"....when choosing the driver from the nidswrapper Gui to install, you have to choose the .inf file.

---

### Post by Jurgen Oscar on 2010-06-08
> **ibe2fly4chu said:**
> I cannot confirm that it works with 64 bit architecture. However if you are having trouble with a wireless adapter in about 95% of the cases, ndiswrapper will get you up and running. Now now, i know alot of people hate ndiswrapper because there are guides written to get you through it that simply confuse you even more (dont worry they make perfect sense after you have used the thing once via terminal  lol ^^). To make life easier i would suggest you follow these steps:

First pop your live cd in while logged into ubuntu.

Open the live cd, and navigate to pool/main/n
Install the ndiswrapper .deb files 

after installing the 2 files in the ndiswrapper folder, navigate to the ndisgtk folder and install that file as well.

At this point you might want to download your windows drivers for the usb adapter. (preferably xp..it is just my personal opinion that xp drivers work best with ndiswrapper).

Open Terminal and type: sudo ndisgtk
This should open the simple to use GUI for ndiswrapper. simply plug your adapter in, and choose the driver file you downloaded. Hit install and you should be good. 

Just a quick note: Alot of windows drivers are provided in .EXE file extensions. To use ndiswrapper you have to extract it..which will in turn provide something that looks like: "wirelessadapter.inf" AND "wirelessadapter.sys"....when choosing the driver from the nidswrapper Gui to install, you have to choose the .inf file.

Okay...need to get into some details.

I did installed the ndiswrapper, using all the .inf i could get in the downloaded
drivers (both version 2.8 and 4.1). netusb.inf, etc.

NONE of them working, my network-manager could scan through all the available wifi,
but could not connect to either of them.

I posted some details in this thread:
[http://art.ubuntuforums.org/showthread.php?p=9390590](http://art.ubuntuforums.org/showthread.php?p=9390590)

But I cannot get the answers, so I started a new thread.

Thanks, if you have other idea beside ndiswrapper, just let me know please.

Cheers,
J.O.

---

### Post by davidmohammed on 2010-06-11
... sometimes wifi adapters need a non-free firmware load.

If you look in your kernal system logs - search for firmware.  If it says something like firmware needs to be loaded but is not available then that confirms it.

Using synaptic there is a firmware package (search for firmware).  Load it and reboot.  See if it works.  If it doesnt, take a closer look at the system log - it will tell you what firmware it needs.  Google it.  You should be able to download and install.


... edit...

see [this thread ]("http://ubuntuforums.org/showthread.php?p=9306475")for a resolution

---

