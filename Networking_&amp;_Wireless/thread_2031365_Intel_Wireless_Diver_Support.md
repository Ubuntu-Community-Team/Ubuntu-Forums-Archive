---
title: "Intel Wireless Diver Support"
date: 2012-07-21
forum: Networking &amp; Wireless
---

### Post by 1992drewski on 2012-07-21
Hello Everyone!

This is my first post to the forum, I have used Linux a bit in the past, but I am still quite new. I am largely a Windows user, but I am finding doing any kind of development work is like trying to run in quicksand... 

So to start I have a Samsung QX411 laptop which I understand isn't the most supported laptop. I have it duel booted with Windows 7 and Ubuntu 10.04 LTS. Every thing works fine and dandy under Windows, but Ubuntu needs some driver support.

Right now I am making pathetic attempts to get my wireless card working in my laptop lol. Here is some information about my wireless card, I don't know how much help it will be, but I am willing to work with whomever will help me.

```
02:00.0 Network controller: Intel Corporation Device 0885 (rev 67)
    Subsystem: Intel Corporation Device 1305
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 11
    Region 0: Memory at e1600000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>

```

And here is some more stuff...
```

modinfo iwlagn
filename:       /lib/modules/2.6.32-41-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
alias:          iwl4965
license:        GPL
author:         Copyright(c) 2003-2009 Intel Corporation <ilw@linux.intel.com>
version:        1.3.27k
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
firmware:       iwlwifi-4965-2.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-2.ucode
firmware:       iwlwifi-6050-4.ucode
firmware:       iwlwifi-6000-4.ucode

```

You can tell I am bad at this...

Also wlan0 does not show up under my Network Connections. 

thank you
Andrew

---

### Post by NikTh on 2012-07-21
Hi , 
did you try the new Ubuntu LTS version , 12.04 ? 
I think it has better driver (and devices) support , newer kernel , newer packages .. etc. 

You can download the iso image from here --> [http://cdimage.ubuntu.com/releases/12.04/release/](http://cdimage.ubuntu.com/releases/12.04/release/) , 
burn it to a CD , or Usb (usb its better IMO ) and boot from there. 
Click "Try Ubuntu" to get in to Live Session  and check if wireless works there. 

PS: You can see a good tutorial here -->[http://ubuntuforums.org/showthread.php?t=811397](http://ubuntuforums.org/showthread.php?t=811397) , on how you can burn a live Ubuntu Usb from within windows , with unetbootin program. 

Thanks .

---

### Post by kurt18947 on 2012-07-22
I agree with NikTh, try a live CD/USB.  Wireless support in 12.04 is much better for recent Wifi chipsets.  Don't be put off by Unity.  It's certainly different but many people that have stuck with it for a few hours have come to like it and even prefer it over Gnome 2.    If you want a more traditional UI, you could try Xubuntu or Lubuntu instead.  The level of wifi support should be the same.  Or you could try Mint 13/Maya with the Mate environment.  Mate is a quite a good effort to make Gnome 3 look and act like Gnome 2.

---

### Post by 1992drewski on 2012-07-22
Okay okay I will give that a try. Yeah the only reason why I am using an older version of Ubuntu is because I installed it a while ago and never really got around to using it. I believe I even installed it through a USB. 

But shouldn't I be able to just install an updated kernel, I thought that was the whole idea of installing updates. I can connect to the internet perfectly fine through an Ethernet cable, is there any patches or updates I can install... or hell install Ubuntu 12.04 through a terminal.

I am just kind of wary of installing a new OS on my system and partitioning my HDD... scares me.

---

### Post by NikTh on 2012-07-22
Hi , 1992drewski 

You can upgrade an LTS version (10.04) to another LTS version (12.04) . 

Check out this tutorial --> [http://askubuntu.com/questions/110477/how-do-i-upgrade-from-10-04-or-11-10-to-12-04](http://askubuntu.com/questions/110477/how-do-i-upgrade-from-10-04-or-11-10-to-12-04). 

Thanks

---

### Post by kurt18947 on 2012-07-22
I would also consider trying a live CD/USB, not installing anything to your hard drive.  If your Intel adapter doesn't respond to 12.04 in a live session, installing to your hard drive may not help.  There are adapters that are helped by installing additional software or firmware.  Broadcom comes immediately to mind.   Intel has been proactive about its Linux support and most Intel adapters work out of the box, no need to install anything additional.  I have two wireless adapters that required post install software & tweeks to work in 10.04.  Both are recognized and function in 12.04 with no additional drivers or tweaks.

---

### Post by 1992drewski on 2012-07-22
Okay I will try the the live CD/USB with 12.04. If it doesn't work I wouldn't mind buying USB wifi antenna.

One more thing... should I go for the 64bit or the 32bit. It says 32bit is recommended, but will it interface with my hardware as well as 64bit?

---

### Post by 1992drewski on 2012-07-22
I am reposting but the problem has been solved!!

I updated to 12.04 through a live USB, man this thing is siiiiick:guitar: everything seems to working fine thus far. Thanks for the tips!

---

### Post by kurt18947 on 2012-07-23
> **1992drewski said:**
> I am reposting but the problem has been solved!!

I updated to 12.04 through a live USB, man this thing is siiiiick:guitar: everything seems to working fine thus far. Thanks for the tips!

Excellent!  Could you mark this solved using thread tools at the top?  Others having a similar problem can benefit from your proven solution.  Thanks.

---

