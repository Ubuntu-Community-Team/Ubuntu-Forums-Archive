---
title: "x700 Mobility and Ati Driver, Shutdown problems?"
date: 2007-03-22
forum: Multimedia &amp; Video
---

### Post by scr4p3r on 2007-03-22
Hello,

First of all I'am new to Ubuntu, and new to this forum (long time windows user), I wanted to try Ubuntu (Edy 6.10) on my laptop:

Acer Aspire 3020; AMD mobile Sempron 3000+, 512mb DDR ram, 80gig HD, Broadcom 4318wlan chipset, ATI x700 Mobility vga

Install went smoothly, sound was working out of the box after some searching/reading some guides I got my wireless working, most other things where working correctly, the only thing that would'nt work was display the native res of my laptop correctly. 

The native res of my laptop is 1280x800 and the default driver supports the resolution but I would'nt display correctly (it's hard to explain how it looks but if I switch from the working 1024x768 res to 1280x800 res you have a corerctly working area of 1024x768 and the remaining parts of the screen overlap and flikker etc). So decided to give the official ati drivers a try followed this guide as a start: [Unofficial ATI Linux Driver Wiki](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide") and tried the "Method 1: Install the 8.28.8 Driver the Ubuntu Way". Install went smoothly and rebooted and had a working 1280x800 res and I even had hardware acceleration so I was pretty happy until I wanted to shutdown the laptop.

After cliking the shutdown button, the shutdown music would play and after that the screen would hang ([image]("http://img340.imageshack.us/img340/4126/img0006kr9.jpg"), it looks like the default background but all messed up) and the last few tones of the shutdown music would play over and over again until I manualy shutdown the laptop (holding the power button for 5sec). So uninstalled the drivers and tried rebooting, works perfectly without the ati drivers but still couldn't change the res to 1280x800.

I've tried several driver install guides, tried the automatic ways, the manual ways nothing seams to matter, when the ati driver is installed the machine doesn't shutdown/reboot. Without the drivers I can't run 1280x800. When ubuntu runs in recovery mode (terminal only) I does shutdown/restart (with "shutdown (-r) now") so I think it is the graphical enviroment that has problems.

I also run Ubuntu on my desktop (wich runs a x1950pro pci-e) without any problems, also using the ati driver.

I hope anyone has any clue on what this is causing and how it could (if possibly) be fixed.

greetz and thanks for reading. :)

[SIZE="2"](ps english isn't my native language, so spelling mistakes enough)[/SIZE]

---

