---
title: "XGL and video playback are not happy together.  Please help."
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by azdragon on 2007-10-21
OK here is my problem with the solutions I have found so far.

I had everything working in Feisty.....    Upgraded to Gutsy.....

Most all programs were upgraded and work great..

The major problem was the new compiz program.
Because I was using beryl and that was removed I was stuck with compiz to do all the cool 3d stuff.  First off it did not like to use emerald.  I was able to get it to work one time, but when I rebooted I was never able to get it to work again.   I have a nVidia card and I am using the restricted drivers.     

After a long time of trying different things I got most everything working....except I still did not have emerald running correctly so I did not have borders on my windows...and that is not good.   So I found that there is this thing called XGL.....so I installed it.   It is odd cause most of the forums talking about XGL talk about ATI cards in the same section, and because I use nVidia I was unsure if this was for my card.   So I installed it, rebooted and presto I had borders and window controls.

I used this for a day, played with Compiz and was generally happy.  Then I decided to play a movie, and OMG, it did not work correctly.   When I use the totem player I get a green bar on the top of the movie, and all the other colors in the movie work.   The funny thing is that if I hit “I” on my keyboard and put it out of deinterlace mode then IT WORKS, then I can put it into full screen and toggle on deinterlace and then I can watch the movie, but if I leave full screen it breaks again.   

I did not like this.....so I tried Mplayer.   Mplayer had the correct colors but it made the move like two screens wide and only about 200 pixles high.....I could stretch it to the correct aspect ratio but that was hard to do by eyeball.  I also can select video output to be X11(Ximage/Shm) and that shows it correctly BUT I can not scale it at all, it only shows in a 1:1 ratio.   This also sucks, because it is way too small.

Now I do want to let you know that only about 30% of my movie collection is having this problem, the rest are PERFECT.  I also have many music videos and all work also.   So I wanted to confirm that XGL was the problem.  I uninstalled XGL and then tried the movies and guess what, they ALL worked PERFECT.   But again I had no window borders or controls.   So, I had to install XGL again and I am back to the problems.    

OK any ideas?    What is XGL?   Is it for nVidia?  How do I fix the video?  Could it just be a shared lib file that is messing it all up?   I am not a total expert at this so help me please.

---

### Post by azdragon on 2007-10-21
To keep you updated, I installed VLC...same problem.   I also downloaded every codec I could find and it is exactly the same.    Hmmmm....maybe next is to try the glx version of compiz instead of using emerald......unless anyone has a cool command line thing I can type that will fix it.

---

### Post by matthew on 2007-10-23
Since you have an nVidia card, I can't think of any good reason to use xgl, which can be a bit buggy sometimes, but is useful for ATI card owners because the binary video drivers produced by ATI do not yet support aiglx.

So...first off, remove xgl. You shouldn't need it. Question: what nVidia card do you have? I don't have anything by them, but this info will be likely to help someone who knows more about their equipment assist you.

Second, do you have the nVidia binary drivers, the 3D ones, installed correctly? How do you know?

If you think you do, do your desktop effects work properly?

Next step, please attach the contents of your /etc/X11/xorg.conf file. Sometimes there are settings in there that can be adjusted to help with this sort of thing.

Well, hopefully this can help get things started anyway... :)

---

### Post by JBAlaska on 2007-10-23
In compiz settings enable the video playback utility and the workarounds, that should cure your problems.

---

### Post by azdragon on 2007-10-23
To answer both of these suggestions.   First I have tried all of the video settings in compiz with now help.     On XGL, before I had XGL I was lacking windows decorations, which then gave me no borders or controls for my windows, and that was much worse.    But I can tell you that without XGL I did not have the video problem.  

I will try to remove it again, maybe with all the other things I have added into the mix I will still have windows decorations without XGL.

For you matthew, I have a nVidia 7600 gts PCI-E video card with 256mb.   I have a MSI motherboard, with a dual core 3800 athlon.  I have a Viewsonic 22" widescreen, which is set to a very unique resolution.  You gotta get one of these monitors, they are totally awesome.  I can't uninstall XGL now because I am using adept to install Ubuntu Studio....all 500MB of it.    It has been going for hours and is only 40% of the way done, and I can't uninstall software when another thing is installing software.

---

### Post by azdragon on 2007-10-23
> Second, do you have the nVidia binary drivers, the 3D ones, installed correctly? How do you know?

If you think you do, do your desktop effects work properly?

Next step, please attach the contents of your /etc/X11/xorg.conf file. Sometimes there are settings in there that can be adjusted to help with this sort of thing.

Well, hopefully this can help get things started anyway... :)


I am fairly sure the drivers are installed correctly.  Yesterday in trying to fix the problem I deleted the drivers and then used the System > Administration > Screen and Graphics program to select Geforce by nVidia.  It downloaded the newest restricted driver.   

I think that all of the effects work as they should.   I have the cube thing, the wobble windows, the water effects....the exit and minimize animation......the transparent windows and all that stuff....it all works great  (Except the part where each side of the cube has a different background, I set it to work but it always shows one that is not even in the list, also even though I set wobble windows to not snap, they still snap to the sides of my screen, very annoying)  

After reading much of what is on this forum I think I have been quite lucky.  I have had no hardware not work, other than my lame printer.  And 95% of the problems that I see other people have I did not have, mine just worked.


Here is that file you wanted.  > 
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"NVIDIA GeForce"
	Busid		"PCI:2:0:0"
	Driver		"nvidia"
	Screen	0
	Vendorname	"NVIDIA"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1680x1050"
	Horizsync	31.5-65.5
	Vertrefresh	56.0	-	65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1680	1050
		Modes		"1680x1050@60"	"1600x1024@60"	"1440x900@60"	"1280x800@60"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@56"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection
Section "device" #  
	Identifier	"device1"
	Boardname	"NVIDIA GeForce"
	Busid		"PCI:2:0:0"
	Driver		"nv"
	Screen	1
	Vendorname	"NVIDIA"
EndSection
Section "screen" #  
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" #  
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

---

### Post by azdragon on 2007-10-23
I just found a file called xorg.conf.1   It was my old xorg.conf file before I upgrated to Gutsy.   It is quite a bit different.   Should I try using it instead?

> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation G70 [GeForce 7600 GS]"
	Driver		"nvidia"
	Busid		"PCI:2:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"VX2235wm"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G70 [GeForce 7600 GS]"
	Monitor		"VX2235wm"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1680x1050"	"1600x1200"	"1440x1440"	"1400x1050"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x640"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1680x1050"	"1600x1200"	"1440x1440"	"1400x1050"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x640"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1680x1050"	"1600x1200"	"1440x1440"	"1400x1050"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x640"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1680x1050"	"1600x1200"	"1440x1440"	"1400x1050"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x640"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1680x1050"	"1600x1200"	"1440x1440"	"1400x1050"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x640"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1680x1050"	"1600x1200"	"1440x1440"	"1400x1050"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x640"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by matthew on 2007-10-23
I can't see anything in either version that I know would make a difference...then again, as I said, I have no experience with nvidia cards.

I can't see the harm in trying the old version and seeing what happens. Make sure you backup the current version first and that you know how to restore it from the command line if necessary. :)

Hopefully someone else with more history using your specific hardware will jump in now.

---

### Post by azdragon on 2007-11-03
OK I seem to have this problem fixed.   In the past when I uninstalled XGL it did not fix the problem.  This time when I uninstalled it I selected for it to unistall config files also....that did the trick.  It may be something else that fixed it because I have installed about 200 updates from the last time I tried.   

Anyway it is working now.  Today a update for compiz and for my nVidia driver both were avalible.   I am tasking my PC to download them as I write this.   I hope it makes it all work.  

BTW XGL made my computer very slow....without it it is much faster.

---

### Post by matthew on 2007-11-03
I'm glad to hear there has been positive progress. Please keep the updates coming as events warrant. :)

---

### Post by azdragon on 2007-11-04
OK well this is fixed now.   Everything worked for a while, even after all the new updates.  

Then something crashed and now the default player shows a green screen.   At least in all my time looking to fix my main problem shows some people who had this other problem.  Also when I have fresh boot it works for a while.    I will figure it out later.

Right now I am spending a good deal of time posting to Wikipedia.......They are looking for people who translate English articles into Arabic....maybe you or your wife can do that.   Wikipedia is built on the same idea as Ubuntu, that information should be free.

---

### Post by matthew on 2007-11-04
> **azdragon said:**
> Right now I am spending a good deal of time posting to Wikipedia.......They are looking for people who translate English articles into Arabic....maybe you or your wife can do that.   Wikipedia is built on the same idea as Ubuntu, that information should be free.It's a great concept. I have so much on my plate right now I can't even consider adding something else. :)

I'm glad the video thing was working, and bummed for you that it broke. Hopefully you can get it up and running again.

---

### Post by azdragon on 2007-11-04
Yea I got it up and going again.   I just have to hit   Control-Alt-Backspace.   and wait like 10 seconds and relog in and it works.   It is working right now.    I don't know what I do to break it.   The only lame thing about resetting the X server is that it resets all the other things I am working on.

I will send you an email for other stuff I wanted to ask, look for it later.

---

