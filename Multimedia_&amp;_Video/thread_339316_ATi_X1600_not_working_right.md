---
title: "ATi X1600 not working right"
date: 2007-01-15
forum: Multimedia &amp; Video
---

### Post by SVFUSiON on 2007-01-15
I am trying to get my ATi X1600 512MB AGP to work with Ubuntu 6.10 Edgy. I install the drivers and my screen starts messing up. I used this guide [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")

and tried this guide [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")

Here is a screenshot of what it is doing.



[http://img156.imageshack.us/my.php?image=screenshotdg4.png]("http://img156.imageshack.us/my.php?image=screenshotdg4.png")

Thanks for your support,
svfusion

---

### Post by Blaze1024 on 2007-01-24
> **SVFUSiON said:**
> I am trying to get my ATi X1600 512MB AGP to work with Ubuntu 6.10 Edgy. I install the drivers and my screen starts messing up. I used this guide [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")

and tried this guide [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")

Here is a screenshot of what it is doing.



[http://img156.imageshack.us/my.php?image=screenshotdg4.png]("http://img156.imageshack.us/my.php?image=screenshotdg4.png")

Thanks for your support,
svfusion


This is a simple fix, I have no idea why no one has responded. 

In your bios setup change your  (AGP Aperture Size) to 128 its probably set to 32 or 64

Then If the line 
Option     "BusType" "PCI" 
is in your xorg.conf file comment it out. 

Make sure these lines are present 
Option	       "VideoOverlay" "on"
Option	       "OpenGLOverlay" "off"

It should look something like this.. >>>>> Don't change the Identifier line or the BusID
Section "Device"
	Identifier	"ATI Technologies, Inc. ATI Default Card" 
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option	       "VideoOverlay" "on"
	Option	       "OpenGLOverlay" "off"
#	Option      "BusType" "PCI" >> This is the line you want to comment out
EndSection

If you still have problems comment out this line 
	Load	"extmod"
and change it to this 

SubSection "extmod" 
     Option "omit XVideo" 
     Option "omit XVideo-MotionCompensation" 
     Option "omit XFree86-VidModeExtension"  
EndSubsection

It should look like this 
Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
#	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
SubSection "extmod" 
     Option "omit XVideo" 
     Option "omit XVideo-MotionCompensation" 
     Option "omit XFree86-VidModeExtension" 
EndSubSection

EndSection


That should get you up and running 

Then you can try adding these lines one at a time to improve stability and performance  add them one at a time under Section "Device"
Option       "UseInternalAGPGART" "no"
Option		"XaaNoOffscreenPixmaps"
Option          "EnablePageFlip" "on"
Option          "RenderAccel" "on"
Option          "AccelMethod"   "EXA" # or XXA
	  # acceleration
Option          "AGPMode" "8"
Option          "AGPFastWrite" "yes" 

Make sure you back up your xorg.conf before making any changes.

---

### Post by likwidsage on 2007-01-24
I just installed ubuntu for the first time coming from SuSE and love it. I got my X1600 card + Beryl installed twice in row with no problems what-so-ever. This is the tutorial I used: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Hope that helps someone.

---

### Post by Blaze1024 on 2007-01-25
> **likwidsage said:**
> I just installed ubuntu for the first time coming from SuSE and love it. I got my X1600 card + Beryl installed twice in row with no problems what-so-ever. This is the tutorial I used: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Hope that helps someone.

Is your x1600 AGP or PCIe

---

### Post by syroncoda on 2007-02-02
Hi, 

I also am having a similar problem. i too have an x1600 but here seems to be a catch. i also have a gigabyte board with an nforce3 250 chipset. 

i am pretty new to linux and this issue has been bugging me constantly. this is the 3rd reinstall i've gone through in 2 days due to my lack of knowledge. (although i realise now i could have fixed the problem instead of wasting a few mour hours of watching the install).

any ideas?

 fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series Generic
OpenGL version string: 2.0.6286 (8.33.6)

what else do i post?

thanks

---

### Post by RobNyc on 2007-02-04
> **SVFUSiON said:**
> I am trying to get my ATi X1600 512MB AGP to work with Ubuntu 6.10 Edgy. I install the drivers and my screen starts messing up. I used this guide [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")

and tried this guide [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")

Here is a screenshot of what it is doing.



[http://img156.imageshack.us/my.php?image=screenshotdg4.png]("http://img156.imageshack.us/my.php?image=screenshotdg4.png")

Thanks for your support,
svfusion

Wow I just got that problem today when I installed the 8.33 drivers with a fresh installation

---

### Post by syroncoda on 2007-03-23
bumpity bump forum spake.

anyone else come across the weird "mis-rendering" ? i posted on another thread a more indepth account of what i was doing [Here]("http://ubuntuforums.org/showthread.php?p=2343731#post2343731")

---

