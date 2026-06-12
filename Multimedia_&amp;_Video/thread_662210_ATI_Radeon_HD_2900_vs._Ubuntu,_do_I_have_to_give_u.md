---
title: "ATI Radeon HD 2900 vs. Ubuntu, do I have to give up?"
date: 2008-01-08
forum: Multimedia &amp; Video
---

### Post by zollazolla on 2008-01-08
Hello there,
I know this problem is well known, and I know there many posts out there about this problem but...
I tried all the ways, I tried all the guides, but nothing...
I really want to use Ubuntu, but at this rate I have to give up.

I have a PC with: ATI Radeon 2900 HD PRO, 1GB DDR2, AMD Sempron 3200+, an ASRock motherboard (I can't remember the model right now).
I installed Ubuntu without problems, but when I try to install ATI Drivers and restart I cannot turn back to my desktop, the well known "black screen of death" does its "show"...

I tried all the ways, but had no luck...
Please guys, help me...
I don't wanna turn to M$ again...

Thanks a lot!

Stefano

---

### Post by LeBurt on 2008-01-08
I have given up, that's for sure. I have an AMD 64 3000+ and a Radeon All-In-Wonder 9600 and nothing has ever worked right since Gutsy. The same ugly "Black Screen of Death" still shows its face.

Well, in fact, I shouldn't say "nothing ever". When Gutsy came out, I installed it fresh and enabled the restricted ATI driver (fglrx version 8.37 I think) and yes, I was able to have 3D acceleration. I remember being disappointed that I couldn't try the new 3D desktop effects of Compiz-Fusion and waited patiently for the 8.43 release of ATI's fglrx driver that promised so much. That's when things started to go wrong.

Anyway, since then I tried pretty much every howto, hack, voodoo incantation ever published on the subject to no avail. It won't even work if I do a fresh install and try the old 8.37 restricted driver again (how is that possible?). Makes me wonder if Ubuntu's installation is as deterministic as they think. Sometimes it works, sometimes it doesn't, go figure. I'm not good (or patient) enough to get to the bottom of the problem so every time ATI comes out with a new version of its proprietary driver, I give it a try, it doesn't work, and I go back to a 2D environment.

Sucks.

---

### Post by sneakyzor on 2008-01-09
I was having trouble with with my setup as well (i have ati 9700 mobile), not sure if you have tried this already, but what solved my issue was installing xserver-xgl thru synaptic and then using Envy, i manually installed the 8.40.4 drivers.  That got everything working smoothly, even 3D acceleration.

Hope this helps, works alot better than the newer drivers from ati.

---

### Post by zollazolla on 2008-01-09
Nothing to do, I tried to install envy but the result is a "minimal graphic" Ubuntu, obviously without 3D...
It sucks a lot...

---

### Post by drguerra on 2008-02-10
I have the ATI/AMD 2900 also.

I bought this card based on this garbage article written in a Linux magazine that AMD/ATI are now putting tons of focus into their linux drivers. Pure garbage.

I will never ever ever ever buy anything ATI or AMD, and I hope they go out of business. 

In the mean time, anyone fix this yet? Anyone with the 2900 pro or XT that got the restricted driver working, PLEASE give us you STEP by STEP solution.

I always get the black screen of death.

---

### Post by Melcar on 2008-02-10
I'm running a HD2900XT with the latest fglrx with no issues, aside from the "bugs" that plague the current code base (no Xv/OGL with Compiz for example).  All I do is run the install script, and the driver install perfectly every time.  I don't bother with the Restricted Drivers Manager.

First, I would rebuild the xserver just in case:

> sudo dpkg-reconfigure xserver-xorg

And remove any mention of fglrx from your system (this will depend on what you have done while trying to install).

Then once back into a normal session open a terminal and do the following:

> sudo apt-get install build-essential fakeroot dh-make debhelper debconf libstdc++5 dkms

> sudo sh ati-driver-installer-8-01-x86.x86_64.run

Finish the installation wizard and initialize the driver:

> sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv


Reboot and enjoy.

Note:  I recommend you do not blacklist fglrx from linux-restricted-modules, because that will simply blacklist fglrx, regardless of its source, causing the module not to load.

---

### Post by drguerra on 2008-02-11
How do I edit the blacklist to make sure it isn't blacklisted?

---

### Post by drguerra on 2008-02-11
Oh my God.

Your guide worked.

You are a GENIUS sir. An absolute GENIUS.

Thank you SOOOO much. You have no idea how much pain this has caused me.

However, I have one issue.

I have a NEC AccuSync 75f monitor, and would like it to run in 1024x768 at 85hz, however, whenever I try to change the resolution in the "Screen and Graphics Preferences" and I test it, it won't work. Not with plug and play, not with Monitor 1024x768, and not if I manually pick the monitor. Is there a linux driver for this? Anyway I can do this?

It's at 1280x960 which my monitor can support, but only at 60hz, which is hurting my eyes.

Any ideas guys?

---

### Post by Melcar on 2008-02-11
Did you try adding the resolution to xorg.conf?  I don't know if modelines work; the last driver release broke modeline support and I'm not sure if it got fixed for this one.

---

### Post by drguerra on 2008-02-11
I can't seem to get compiz running, or any other desktop effects, and everything has become rather sluggish.

when I typed fglrxinfo

I got:
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

So is it really using the ATI driver?

I fixed the resolution issue, however.

---

### Post by Melcar on 2008-02-11
The module is not loading.  It should read something about ATI and not Mesa.  Did you check linux-restricted-modules to see if fglrx was not blacklisted?

> sudo gedit /etc/default/linux-restricted-modules-common

---

### Post by drguerra on 2008-02-11
# DISABLED_MODULES="ath_hal fc fglrx ltm nv"

DISABLED_MODULES=""

Doesn't that mean that nothing is disabled?

---

### Post by Melcar on 2008-02-11
Yes.  You're in the clear as far as blacklisted modules.  Did you initialize the driver?  What does the "driver" option under the Device section in xorg.conf say?  It should be fglrx.

---

### Post by drguerra on 2008-02-12
How can I check?

I am not experienced whatsoever with Linux and forget the most basic commands easily.

---

### Post by Melcar on 2008-02-12
> sudo gedit /etc/X11/xorg.conf

Near the end of that file should be a section called Device.  Check what it has in the "driver" subsection.

---

### Post by drguerra on 2008-02-12
Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

It's so incredibly laggy.

Everytime I scroll down while web surfing, the thing moves so slow, and I have a BEAST of a PC.

---

### Post by ScottLind on 2008-02-12
> **ATi]The following packages must be installed in order for the Catalyst&#8482 said:**
> 

Those two marked with big.. How do I get those packages? 
I'm new to Linux and I don't have a clue :P

EDIT: Melcar, I've tried your solution. I'm rebooting now and in sudo gedit /etc/X11/xorg.conf, everything looks fine, so I hope for the best :D

EDIT-EDIT: This came when I rebooted:

[QUOTE]Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:0:0"
	Driver		"fglrx"
	Screen	0
	Vendorname	"ATI"
EndSection

It said ATI Radeon HD 2400 before I rebooted.. Do you know what's wrong?

---

### Post by Melcar on 2008-02-12
Here is part of my xorg.conf:

```

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	HorizSync    30.0 - 82.0
	VertRefresh  56.0 - 75.0
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes	  "1680x1050" "1600x1200" "1440x900" "1280x1024"
	EndSubSection
EndSection
```


@ ScottLind

Just install the packages I listed on my previous post.  Those should be enough.  Also, I hope your card is not AGP, because a lot of people have been having major problems with AGP cards and fglrx.

@ drguerra

fglrxinfo should output this:
> 

principe@magicbox:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2900 XT
OpenGL version string: 2.1.7276 Release

If it says Mesa, then the driver is not loading.  I would uninstall the driver, make sure nothing referring to fglrx is on the system (search Synaptic for fglrx), rebuild your xserver, and re-install.

To uninstall (if you used the script):

> cd /usr/share/ati
sudo sh ./fglrx-uninstall.sh


To rebuild the xserver:

> sudo dpkg-reconfigure-xserver-xorg

# select vesa as your graphics driver


Another thing you could try when running the install script, is use "bash" instead of "sh", since I hear that sometimes causes problems:

> sudo bash ati-driver-installer-8-01-x86.x86_64.run

There is no reason for it not to work, since I'm using the same card with a standard Ubuntu install (which I'm sure you are too), unless you screwed up something really bad on one of the previous attempts at installing the driver.

---

### Post by Ikith on 2008-02-12
Wow... I get the mesa project problem even when rebuild the xorg.conf... This is seriously confusing the hell out of me... No matter which way I try to get this driver working it still says Mesa project! Ugh...

---

### Post by erniegeorge on 2008-02-12
I have the fg1rx driver installed for my HD 2900 and everything appears ok, but if I try to watch video it is very laggy. Also when I move windows around the edges appear to be redrawing slow. I can turn on all the compiz effects and they work fine. Is there some setting I'm missing somewhere?

---

### Post by drguerra on 2008-02-12
I followed your steps and now when I try to install the driver I get:

ERROR: vcdk is missing. Installation aborted.

---

### Post by ScottLind on 2008-02-13
> **Melcar said:**
> @ ScottLind

Just install the packages I listed on my previous post.  Those should be enough.  Also, I hope your card is not AGP, because a lot of people have been having major problems with AGP cards and fglrx.



My bus is AGP :/

---

### Post by Pettman on 2008-02-13
> **LeBurt said:**
> I have given up, that's for sure. I have an AMD 64 3000+ and a Radeon All-In-Wonder 9600 and nothing has ever worked right since Gutsy. The same ugly "Black Screen of Death" still shows its face.Have you tried forcing agp x4 in both BIOS and xorg.conf? 
```

Option          "AGPMode"       "4"
```And agp mode 4 in the BIOS made the ati (xserver-xorg-video-ati) driver work nicely for me (I also use the ati driver from xorg on the edge, see the wiki).> **zollazolla said:**
> Hello there,
I know this problem is well known, and I know there many posts out there about this problem but...
I tried all the ways, I tried all the guides, but nothing...
I really want to use Ubuntu, but at this rate I have to give up.

I have a PC with: ATI Radeon 2900 HD PRO, 1GB DDR2, AMD Sempron 3200+, an ASRock motherboard (I can't remember the model right now).
I installed Ubuntu without problems, but when I try to install ATI Drivers and restart I cannot turn back to my desktop, the well known "black screen of death" does its "show"...

I tried all the ways, but had no luck...
Please guys, help me...
I don't wanna turn to M$ again...

Thanks a lot!

StefanoHave you tried the xserver-xorg-video-radeonhd driver package?

---

### Post by Melcar on 2008-02-13
> **ScottLind said:**
> My bus is AGP :/


There is a little [discussion]("http://www.phoronix.com/forums/showthread.php?t=7799") over at the Phoronix forums about AGP cards with Rialto chips and the current fglrx.  Seems that the current code base is having problems with the bridge chip.


Have you guys tried generating/installing packages?  That seems to be the fail safe way to get the driver working.

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually")

---

