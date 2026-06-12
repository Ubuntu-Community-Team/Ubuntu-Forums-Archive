---
title: "Computer Hanging - Video Issue?"
date: 2006-07-13
forum: Multimedia &amp; Video
---

### Post by R3M3 on 2006-07-13
Hello All,

I'm having problems with my computer locking up - no mouse control, no keyboard, not even Num Lock. There doesn't seem to be a particular time when it hangs - I've seen it happen overnight with no activity, when loading a program, in the middle of using a program, even when the computer first boots. Unfortunately, I don't have an ability to telnet in to see if it's the entire system locking, or just X.

I recently upgraded to Xubuntu Dapper (with apt-get dist-upgrade - I originally installed Kubuntu Breezy, switched to Xubuntu due to poor performance on the old computer), but that doesn't seem to fix the problem. 

From the best I can tell from reviewing the forums, it's possibly an issue with my graphics card driver. I can't recall exactly what the card is (the system is 8 years old - I think maybe an ATI Xpert 98 ), but the chips on the physical card itself are labeled "ATI 3D Rage Pro AGP 2x". I haven't changed any of the default settings for the graphics drivers since install.

I'd appreciate any help with troubleshooting this issue.

---

### Post by yager on 2006-07-13
You wil want to rule out any problems with your memory.  On boot up, choose memtest and allow it to run through all of the tests at least once.

I had very similar symptoms and it turned out to be be a bad memory module.

After this, you can work on the graphics card driver issue.  You may want to back up to the VESA driver until you sort out which graphics card you have.

---

### Post by R3M3 on 2006-07-14
> **yager said:**
> You wil want to rule out any problems with your memory.

Done that. Not only does my BIOS not report any memory problems when it checks during the POST, when selecting the memtest option from the GRUB menu, I noticed no errors. (I assume if errors were found, it would be obvious something was wrong.)

---

### Post by yager on 2006-07-15
On to phase 2 then,

See if the Device Manager reports back the exact kind of graphics card.  With Ubuntu, I go to System>Administration>Device Manager.  I am not sure where you go in the menus on Xubuntu to get to the equivalent function.  Once you are in the device manager, scroll down to find the AGP or PCI bridge, you should be able to recognize the name of the card in the device tree.  Note the name of the card that is provided.  Do a search on the internet to find the correct driver for that card.  I was not able to find what cards are supported by the ati drivers.  Perhaps you will have more luck with this detail.

Once you find the correct graphics driver, you should install it according to the directions provided.

In the event that you are unsuccessful, tseliot has put together a good HOWTO on how to recover from X problems and replace the video driver with VESA or VGA.  Here is the link.

[http://www.ubuntuforums.org/showthread.php?t=187177&highlight=vesa](http://www.ubuntuforums.org/showthread.php?t=187177&highlight=vesa)

---

### Post by R3M3 on 2006-07-18
> **yager said:**
> See if the Device Manager reports back the exact kind of graphics card. ... Do a search on the internet to find the correct driver for that card. 

I assume you mean the executable 'hal-device-manager' from the package of the same name. (I had to install it and run from the command line.)

Here's what it reports:

Devices Tab
-----------
Vendor: ATI Technologies Inc.
Device: 3D Rage Pro AGP 1X/2X
Status: Status
Bus Type: PCI
Device Type: Unknown
Capabiliteis: Unknown

PCI Tab
-------
Vendor: ATI Technologies Inc.
Product: 3D Rage Pro AGP 1X/2X
OEM Vendor: ATI Technologies Inc.
OEM Product: Rage Pro Turbo AGP 2X

I can't find anything specifically for those products. The best I can tell, the ati driver should work. The Xorg website is not quite helpful, but mentions that the ati driver is a wrapper that should load the appropriate driver.

> **yager said:**
> tseliot has put together a good HOWTO on how to recover from X problems and replace the video driver with VESA or VGA. 

Tried that. X wouldn't load with the VGA driver, and I encountered the same hanging problem with the VESA one.

While dealing with dpkg-reconfigure xserver-xorg, I came across some settings which I wonder are connected to the issue:

Previously X was set with framebuffer:no - Should this be set to yes?
Currently I have all modules set to load. Are there some that might be causing a problem?
I also know nothing about the PCI BusID setting. I just accepted the default of PCI:1:0:0 

Unfortunately, on reconfiguring the Xserver, I have now lost my Applications menu, and the desktop background starts off black, and only goes to wallpaper color when it gets redrawn (say when a window passes over it). *sigh*

Just wondering - is there some log I could check which could give an indication of what is precipitating the hang? (Of course, it would have to be accessable after the reboot.)

---

### Post by R3M3 on 2006-08-03
Just a quick update if anyone happens to be searching the archive for the same problem:

I was able to fix the missing menu by right clicking on the menu bar and fooling around with the options there in.

I finally ended up reinstalling xubuntu dapper from scratch. I haven't used the computer much since reinstallation, so I don't know if the problem is fixed or not, but I'm beginning to get the feeling that it might not be X related, as I had a brief hanging issue during text mode reinstallation.

*Fingers crossed that the computer stays well*

---

