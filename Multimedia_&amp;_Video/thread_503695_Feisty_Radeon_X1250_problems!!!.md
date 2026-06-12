---
title: "Feisty Radeon X1250 problems!!!"
date: 2007-07-18
forum: Multimedia &amp; Video
---

### Post by ghstzr0 on 2007-07-18
I have an Asus M2A-VM HDMI motherboard with a X1250 integrated graphics card.  I would like to use the OPEN SOURCE RADEON drivers instead of FGLRX because I don't want to use XGL (for compiz).  However, Feisty won't recognize my integrated card!

It uses the "vesa" driver by default, and if I manually change it to "radeon" my X.org fails to start.  When I look at the logs, I see that it is trying to identify my card and goes through several, severl radeon cards, but does not find mine.  then it errors with "(EE) No devices found." (or something very similar to that - can't check right now...)

I checked the output of lspci and it says something like "VGA compatible... ATI Unknown device" for my video card.  How do I get feisty to recognize this device?  I really hate XGL!!!

---

### Post by overdrank on 2007-07-21
> **ghstzr0 said:**
> I have an Asus M2A-VM HDMI motherboard with a X1250 integrated graphics card.  I would like to use the OPEN SOURCE RADEON drivers instead of FGLRX because I don't want to use XGL (for compiz).  However, Feisty won't recognize my integrated card!

It uses the "vesa" driver by default, and if I manually change it to "radeon" my X.org fails to start.  When I look at the logs, I see that it is trying to identify my card and goes through several, severl radeon cards, but does not find mine.  then it errors with "(EE) No devices found." (or something very similar to that - can't check right now...)

I checked the output of lspci and it says something like "VGA compatible... ATI Unknown device" for my video card.  How do I get feisty to recognize this device?  I really hate XGL!!!

HI if you have not found any help yet try and run the command in the terminal 
```
sudo update-pciids
```
This may update you ids on the graphics controller and we can go from there.

---

### Post by ghstzr0 on 2007-08-21
Thanks for your reply!!!!

I tried that, and it did do something, it just didn't totally fix the problem.

After running `sudo update-pciids`, `lspci` now gives:
```

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon X1200 Series

```
(YAY!!!)

However, my X.org still fails if I try to use the radeon driver (with same error message).

Any other ideas!!!!

:confused::confused::confused:

---

### Post by mrhirsh on 2007-08-21
I can't seem to do anything because of my ATI Radeon x1200 graphics card.  I've tried a couple of different versions of Linux, GPart, and even what is supposed to be the ATI driver for Linux, but keep getting error messages and can't install any of it.

How do you get to the command prompt to type the command listed above?

Thanks,

---

### Post by ghstzr0 on 2007-08-22
I was referring to the terminal.

From the main menu > Applcations > Accessories > Terminal (Using Gnome, of course).

---

### Post by ghstzr0 on 2007-08-26
BUMP!!

BTW, its possible that the X1250 is an AVIVO based card (AVIVO is a new technology from ATI, and I think there are different os drivers for those cards, although they appear to be in early stages of development).  I have read this in a couple of places.  Now I know...  "You can't trust what you read on hte internet...", right?  Well this might explain why the "radeon" drivers are failing, but FGLRX works fine.

---

### Post by Dark Star on 2007-08-26
I guess X 1200 is a onboard solution which  has been problem with Linux from starting like Xpress 200 :x gosh just wait for newer release :) Hope for the best :D

---

### Post by ghstzr0 on 2007-08-27
> **Dark Star said:**
> I guess X 1200 is a onboard solution which  has been problem with Linux from starting like Xpress 200 :x gosh just wait for newer release :) Hope for the best :D
I guess...  However, if that was the case, I would expect it to be better documented.  The RadeonDriverHowTo in the wiki doesn't even MENTION this chipset... skips straight from the x800 series to the x1300 series...  Bummer!

---

### Post by Dark Star on 2007-08-28
Cause X1200 -1250 are recently released Onboard solution which comes with latest AMD 690G boards and as far as drivers are concerned :( Sorry ATI has pathetic driver support :| So lets hope for the best ;)

---

### Post by crimsonsoul on 2007-08-31
Or you can just download the drivers from the official site worked just fine for me i`m eaven playin quake :D [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html) just select linux86_64 , integrated motherboard , Radeon Xpress 1250 and the download the file in the home dir , after wich you press ctrl+alt+f4 and go into console mode ;) and then just type killall gdm (requires root) and run the file with root ,  sh ati-driver-installer-8.40.4-x86.x86_64.run and follow the wizzard ;) 

hope it helps you in any way ;)

---

### Post by ghstzr0 on 2007-09-06
> **crimsonsoul said:**
> Or you can just download the drivers from the official site worked just fine for me i`m eaven playin quake :D [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html) just select linux86_64 , integrated motherboard , Radeon Xpress 1250 and the download the file in the home dir , after wich you press ctrl+alt+f4 and go into console mode ;) and then just type killall gdm (requires root) and run the file with root ,  sh ati-driver-installer-8.40.4-x86.x86_64.run and follow the wizzard ;) 

hope it helps you in any way ;)
Unfortunately, this is an unacceptable solution for those of us who want compositing.

BTW, that's a really round-about way to install the proprietary drivers.  just open the restricted drivers manager and enable the driver; reboot and you're done.

BTW Again...  I heard ATI is going to release its specs.  Anyone know if that's true?

---

### Post by coldguy on 2007-10-21
I'm still a noob. I have a 690g mobo with the integrated ATI Radeon express 1250 gfx, Athlon64x2+4600, 2Gig 800MHz DDR2. I enabled the ATI accelerated driver in the restricted drivers manager.

How do I check to see if it's really working, and that I have 3D hardware acceleration? 

I installed UT2004 linux version and its running really s l o w , even on low settings. My laptop with winXP pentiumM1400 radeon mobile 9700 runs UT2004 awesome with high settings. I installed the latest WIne from Ubuntu repositories, and Steam. The HL1 based games work fine, but source engine games don't work at all.

Is the driver enabled in Restricted Drivers Manager the same as the Proprietary Driver from ATI's website?

---

### Post by Dave_Man on 2007-12-29
Hi, 
I'm considering buying that motherboard, did it eventually work for you?
Does compositing run on it?
What about AVIVO support, did you manage to enable it?

Thanks.
Dave.

---

### Post by philinux on 2008-01-09
Any updates on this welcome. My next pc may have the same motherboard with the inbuilt x1250.

Using gutsy though

---

### Post by intel on 2008-01-19
AVIVO does not work under linux at all, for any GFX card.
other than that this board works really good.

right now all current GFX from Intel, ATI & NVIDIA have big problems under Linux.

---

### Post by Dark Star on 2008-01-19
> **coldguy said:**
> I'm still a noob. I have a 690g mobo with the integrated ATI Radeon express 1250 gfx, Athlon64x2+4600, 2Gig 800MHz DDR2. I enabled the ATI accelerated driver in the restricted drivers manager.

How do I check to see if it's really working, and that I have 3D hardware acceleration? 

I installed UT2004 linux version and its running really s l o w , even on low settings. My laptop with winXP pentiumM1400 radeon mobile 9700 runs UT2004 awesome with high settings. I installed the latest WIne from Ubuntu repositories, and Steam. The HL1 based games work fine, but source engine games don't work at all.

Is the driver enabled in Restricted Drivers Manager the same as the Proprietary Driver from ATI's website?

```
glxinfo |grep direct
``` Do this in Terminal :)

---

### Post by twstd3bc on 2008-01-19
The new RADEONHD Xorg driver works for the X1250 just fine.  Composite works (in, e.g., Xfce4) but there is neither 2D nor 3D acceleration.

---

