---
title: "Computer won't boot with Linksys wmp600n installed"
date: 2012-03-05
forum: Networking &amp; Wireless
---

### Post by ucal on 2012-03-05
Updated version of my difficulties:
Basically, trying to get a wireless card to work on my Desktop.  It's a linksys wmp600n.  The problem is thus:  so far, any driver other than the rt2860sta module (that I've tried) found on the main ralinks site will freeze the computer during boot up if the network card is installed.  However, the rt2860sta driver doesn't actually detect any networks.  Any attempt to get this driver to detect networks (such as modifying it to allow WPA, per the linked in the code block, or simply running ifconfig ra0 up) will result in the computer freezing.  Recently I booted into recovery mode with a known faulty driver installed.  The last terminal output displayed before the computer froze was: 
```
rt2800pci 0000:04:00.0 pci int a -> gsi 19 (level , low) -> irq 19
```.  

This has me worried it's a hardware issue now >_<.  
Code block is the beginning of the problem, in case it is still relevant.
```
I've tried this across multiple versions of Ubuntu, 11.04 all the way to 12.04.  Currently I'm booted into 12.04. 

When attempting to install a version of Ubuntu onto this computer, if the network card was installed, the boot process for the liveCD (the part where there's 5 dots changing from red to white to red sequentially) would freeze up.  Terminal output during this, obtained by pressing an arrow key revealed that the CPU was stalling.  

Without the network card in the computer, it boots flawlessly.  I was able to install 12.04.  With it, 12.04 will now not boot up.  The card is a Wireless-N PCI Adapter with Dual-Band Model WMP600N, which is supposed to work out of the box according to this link:  [https://help.ubuntu.com/community/WifiDocs/Device/Linksys%20WMP600N](https://help.ubuntu.com/community/WifiDocs/Device/Linksys%20WMP600N)

EDIT:  I would report all the information in [this thread]("http://ubuntuforums.org/showthread.php?p=6183681"), but I can't even boot with the card installed, so I don't think it's possible.  Sorry.
```

---

### Post by ucal on 2012-03-05
This is just a hunch, but here's what I'm trying right now:  I think I found what specific chipset the card uses (Ralink 2860), so I downloaded the linux driver for that on to a usb, which I will then try to install on the main computer, then plug in the card.  

The manual for the card seemed very admanant that drivers be installed first on windows, so I'll try the linux version of that process.  Anyways, how does one install drivers that are merely a .bin file?

---

### Post by ucal on 2012-03-05
That did not work, but perhaps I'm doing it wrong.  Does anyone know how to tell a system to load drivers at the start?

---

### Post by kevdog on 2012-03-05
You can put a reference to the driver in /etc/rc.local.

---

### Post by matt_symes on 2012-03-05
Hi

> **ucal said:**
> Does anyone know how to tell a system to load drivers at the start?

Add it to

```
/etc/modules
```

```
matthew@server1:~$ cat /etc/modules 
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
matthew@server1:~$
```

Kiind regards

---

### Post by ucal on 2012-03-05
> **kevdog said:**
> You can put a reference to the driver in /etc/rc.local.

I found another way.  I added the driver to /etc/modules.  This has gotten my computer to be bootable.  The problem is, I still have no wireless connectivity.  I've tried two things, both basically from [this thread]("www.ubuntuforums.org/showthread.php?t=1476007").

I tried modifying the drivers as shown in that thread.  When I modprobed the new driver in (after removing the old one), the machine froze.  This was quite annoying, as I had to open the machine up again, remove the card, boot, install the old driver again, shut down, put card in again, and boot back up. 

My device seems to be ra0.  So I tried 
```
sudo ifconfig ra0 up
```
This froze the machine as well.  

Any ideas?

EDIT:  Thanks Matt, that's exactly what I did.

---

### Post by ucal on 2012-03-06
Tried using compat-wireless.  As soon as I modprobe'd the appropriate driver from it, same freezing.  ctrl+alt+f1 doesn't work either.  It's a complete system freeze.

---

### Post by ucal on 2012-03-06
I can't try it now, but would installing the drivers that came on the CD in wine, then using ndiswrapper be plausible?  IIRC ndiswrapper is for drivers already located on your harddrive in a windows partition, but I'm probably wrong.

---

### Post by ucal on 2012-03-06
Well, ndiswrapper seems to have failed as well.  

Couple odd things about that.  After installing it and the driver recommended by the source forge wiki, I had the driver running, but wlan0 wasn't a recognized device.  I tried putting ra0 up (it was recognized), which resulted in instant freezing.  

One other thing.  It seems 12.04 has some oddities related to ndiswrapper, or at least my install does.  First:  ndiswrapper is installed on the computer, but apt-get remove doesn't uninstall (package not found), and apt-get install won't install it (package not found).  Second, modprobe ndiswrapper doesn't work, because for some reason, ndiswrapper isn't found.  All other commands that I tried respond as if ndiswrapper is on the system.  I compiled the latest version from source, and that fixed all the issues, but this might be something somebody who maintains packages might want to look into.

---

### Post by ucal on 2012-03-07
Edited the first post to include a nice summation so far as well as this new info:

Recently I booted into recovery mode with a known faulty driver installed.  The last terminal output displayed before the computer froze was: 
```
rt2800pci 0000:04:00.0 pci int a -> gsi 19 (level , low) -> irq 19
```.  

This has me worried it's a hardware issue now >_<.

---

### Post by ucal on 2012-03-08
24 hour bump.

---

### Post by wes2859 on 2012-07-05
I know this is gonna sound odd, but I was reading on an unrelated topic though strikingly similar to yours re: belkin 1394 firewire card. It seem the solution was to simply move the card to a different PCI bus slot. It's a reach, but you sound as desperate as I have been, and willing to try most anything. That solution btw was what Belkin's tech supt. recommended and it seemed to fix the persons lockups & general constipation.

My experience with the WPM600N w/ Ubuntu 10.04 using BKTRK 5 has been less than favorable. I meticulously followed MANY thread recommendations to get this card to work. I have had some success though unable to get Layer 2 or 3 up.

I am thinking that I am just lacking general knowledge, exposure to the 'linux' method of installing, make install etc. I am pretty CLI saavy w/ other OS's but just coming upto speed w/ yet another flavor.

For now, I am abandoning my new WPM600n for a legacy AR5005 b/g mini pci installed in a pci bus card adapter. Should be fun.

---

### Post by UltimateCat on 2012-07-05
I have a Linksys as well and long story short I have the:

rt8168 and until I blacklisted the rt8169 my Ubuntu 10.04  didn't have internet conductivity. 

Blacklisting the other driver might be the process for you.

Hopes this helps you.

---

