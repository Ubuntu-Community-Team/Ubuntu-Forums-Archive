---
title: "Vostro 1500 Intel 4965agn Wireless not to be found"
date: 2013-02-22
forum: Networking &amp; Wireless
---

### Post by ctechbob on 2013-02-22
First off, thanks in advance all!



I'm fairly new to Linux/Ubuntu (Although not to tromping around an OS, its just usually some form of Windows) and am having an issue with my Vostro 1500 and the Intel 4965agn wireless card.  It just flat refuses to work, or even detect.  Here are some details:
 

 Dell Vostro 1500
 OS Installed  Dual Boot XP and 12.10
 

 Wireless card works and has worked fine in XP for years now.  Not a single problem.   

I've got a cheapie Rosewill USB dongle that I can pop in and its off and running with no problem.  Obviously, just a temporary fix on my part.  Don't really like dragging around a dongle that could get knocked off the side/back of the laptop.
 

 Turned off the wireless switch in the bios so that it has no effect on any of the RF radios.  Tried with this turned on and off, no change.  Currently set to off.
 

 From what I've been able to search, people are generally asked to provide some of the following info:
 

 **rfkill** lists nothing &#8211; I have bluetooth disabled in Bios
 

 

 shawn@shawn-Vostro-1500:~$ l**shw -c network **
 WARNING: you should run this program as super-user. 
   *-network UNCLAIMED      
        description: Network controller 
        product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection 
        vendor: Intel Corporation 
        physical id: 0 
        bus info: pci@0000:0c:00.0 
        version: 61 
        width: 64 bits 
        clock: 33MHz 
        capabilities: cap_list 
        configuration: latency=0 
        resources: memory:fe8fe000-fe8fffff 
 

 shawn@shawn-Vostro-1500:~$** iwconfig **
 

 lo        no wireless extensions. 
  
 eth0      no wireless extensions. 
  
 shawn@shawn-Vostro-1500:~$ **lspci -nn | grep 0280 **
 0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4229] (rev 61)

shawn@shawn-Vostro-1500:~$ **sudo modprobe iwlagn**
[sudo] password for shawn: 
FATAL: Module iwlagn not found.


shawn@shawn-Vostro-1500:~$** uname -a**
Linux shawn-Vostro-1500 3.5.0-25-generic #38-Ubuntu SMP Mon Feb 18 23:28:26 UTC 2013 i686 i686 i686 GNU/Linux
shawn@shawn-Vostro-1500:~$ 


Hope I got most of what people would ask for.  I know I've been searching and messing with this thing all afternoon without much luck.

Thanks again all!

SH

---

### Post by Hadaka on 2013-02-22
oops

---

### Post by steeldriver on 2013-02-22
Hmm... well I have a 4965 AG or AGN [Kedron] Network Connection [8086:**4230**] on my Thinkpad and that works out of the box on 12.04 using the iwl4965 driver - the thinkwiki page lists 8086:**4229** as also using iwl4965 

They sometimes don't play nice with 802.11n mode and so you may need to disable n to make it connect - maybe try

```
sudo modprobe **iwl4965 **11n_disable=1
```

---

### Post by ctechbob on 2013-02-22
shawn@shawn-Vostro-1500:~$ sudo modprobe iwl4965 11n_disable=1
[sudo] password for shawn: 
shawn@shawn-Vostro-1500:~$ 


Nothing, I don't think it is even getting to the point of installing the driver for the card at this point.

Thanks though!


> **steeldriver said:**
> Hmm... well I have a 4965 AG or AGN [Kedron] Network Connection [8086:**4230**] on my Thinkpad and that works out of the box on 12.04 using the iwl4965 driver - the thinkwiki page lists 8086:**4229** as also using iwl4965 

They sometimes don't play nice with 802.11n mode and so you may need to disable n to make it connect - maybe try

```
sudo modprobe **iwl4965 **11n_disable=1
```

---

### Post by ahallubuntu on 2013-02-22
~

---

### Post by steeldriver on 2013-02-22
My apologies, we should have tried to remove the module first

```

sudo modprobe -rv iwl4965
sudo modprobe -v iwl4965 11n_disable=1

```

Also, do you get anything relevant in dmesg?

```
dmesg | grep iwl
```

---

### Post by ctechbob on 2013-02-22
> **ahallubuntu said:**
> Have you tried enabling Bluetooth in the BIOS just to see what happens?  (Why would you disable it anyway?)


Well, I don't use it for anything, and one of the recommended steps back when I first started this quest was the suggestion that for some reason the BT could be blocking the wireless from working.  

Doesn't make any difference if it is enabled or not.  Same result.

---

### Post by ctechbob on 2013-02-22
> **steeldriver said:**
> do you get anything relevant in dmesg?

```
dmesg | grep iwl
```

I hadn't done that one yet.  Yes an interesting result finally:

shawn@shawn-Vostro-1500:~$ dmesg | grep iwl
[   12.548618] iwl4965: Intel(R) Wireless WiFi 4965 driver for Linux, in-tree:
[   12.548622] iwl4965: Copyright(c) 2003-2011 Intel Corporation
[   12.548772] iwl4965 0000:0c:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4
[   12.592200] iwl4965 0000:0c:00.0: Unsupported (too old) EEPROM VER=0x32 < 0x2f CALIB=0x3 < 0x5
[   12.593431] iwl4965: probe of 0000:0c:00.0 failed with error -22
shawn@shawn-Vostro-1500:~$


Unsupported...hrm, dead in the water then?

---

### Post by ahallubuntu on 2013-02-22
~

---

### Post by ctechbob on 2013-02-22
> **ahallubuntu said:**
> If you wish to replace that card because you can't get it to work, you could snag an Intel WiFi Link 5100 from eBay for about $5 USD shipped.  I've done this upgrade on lots of Dells, though usually I am either getting rid of a Broadcom card or upgrading a G card; the 4965 is N but I guess is Intel's first, and maybe yours is one of the oldest.  I use the 5100 in several laptops successfully.

Replacing the card is probably pretty easy: a couple of screws, unsnap the two antenna wires (not screwed on), swap cards, snap the antenna wires on the new card, screw back in.  Dell probably has a service manual on its website to show you exactly where the card is located; it's either accessible on the bottom from under a panel (screws to remove) or it's under the keyboard.  I upgraded a Vostro 1510 and it was under one of the bottom panels.  There are lots of YouTube videos demonstrating how to replace wireless cards in laptops too.

You need a FULL height 5100, not HALF height.  There are several flavors of the 5100 for different laptops, but you don't need a "Dell" flavor; the card for a Toshiba, Acer, Sony, etc. will also work...but *NOT* from an HP, Lenovo, or IBM - that's an incompatible version of the card that may not work in a Dell.  (Actually, it may still work in Linux but won't work at all if you ever need to use Windows.)

Yep, well versed in that.  This laptop didn't come with an 'n' based card, so that's when it got the 4965.  I might go digging for a 'new' one.  Its not any kind of deal at all to swap them out.  Although part of me (the stubborn) part wants to beat it into submission.....just because...but if its going to cause me to stroke out, then a 'new' card it will be!  :)

---

### Post by ctechbob on 2013-02-25
Yep, I think I've given up on this problem.  I've Ebay'ed another net card, so it will go in in a day or so. I tried the ndiswrapper route, but it looks as though its broken as well.  I was never able to get the module to work properly (Which is mainly my fault).  

I'm taking the (hopefully) easy way out.

---

