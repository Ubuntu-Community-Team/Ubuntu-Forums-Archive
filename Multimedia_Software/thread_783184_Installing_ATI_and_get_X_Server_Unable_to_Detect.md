---
title: "Installing ATI and get X Server: Unable to Detect"
date: 2008-05-05
forum: Multimedia Software
---

### Post by Laxton14 on 2008-05-05
Im trying to install the latest ATI drivers that support my card (8.28.8 ) but when i try to install i get....

Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
Detected configuration:
Architecture: i686 (32-bit)
X Server: unable to detect
Removing temporary directory: fglrx-install

thanks in advance

---

### Post by Laxton14 on 2008-05-05
please if you have any idea what may be wrong please help, i would really like to get my video card correctly installed

---

### Post by deadpunk on 2008-05-10
Hi there! i got the same probleme!!

Am also on an ATI Radeon 9200 (64mb) on my laptop HP nx7010!
Os:Ubuntu 8.04
______________________________________________________
deadpunk@localhost:~$ sudo bash /ati/ati-driver-installer-8.28.8.run 
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
Detected configuration:
Architecture: i686 (32-bit)
[COLOR="Red"]X Server: unable to detect[/COLOR]
Removing temporary directory: fglrx-install
deadpunk@localhost:~$ 
____________________________________________________________
deadpunk@localhost:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 4x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.0.3-rc2

deadpunk@localhost:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 01)
deadpunk@localhost:~$ lspci -n | grep 0300
01:00.0 0300: 1002:4c66 (rev 01)
____________________________________________________________________

The problems is when i enable compiz ! everything is stuck and i think that there are no 3D acceleration!
Or its just because my 64mb is not capable of the compiz 3D effect?
I install the driver " ATI fglrx " from the repos ,but the 3D didnt work !
Then  i try to install the ATi proprietary " ati-driver-installer-8.28.8.run " from ATI!

Thanx !!

---

### Post by Ninja T. Penguin on 2008-09-12
Same problem...

> sh ./ati-driver-installer-8.28.8.run 
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
Detected configuration:
Architecture: i686 (32-bit)
X Server: unable to detect
Removing temporary directory: fglrx-install



> 
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200] (Secondary) (rev 01)
03:0c.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)


---

### Post by Eisenwinter on 2008-10-22
I have a Radeon 9200, for me it's not even detected.
```
No protocol specified
Error: unable to open display (null)
```

That is the output of fglrxinfo.

---

### Post by markbuntu on 2008-10-23
You should not be using such and old driver with 8.04. The x server has been updated and I doubt if they will work. You should be using the open source radeon driver which fully supports those old cards.

Getting compiz to work with a 64mb video card is most likely impossible.

---

### Post by x_off on 2009-02-05
Same problem here, hp compaq nx7010, ati mobility radeon 9200.

Older proprietary drivers from Ati web, the last release working with such card, can't derive a .deb packages because of X server recognition problems.. 

What's the best is that the card was actually working well before on Hardy 8.04.. default opensource ati drivers ..everything include compiz, but since I had messed up with fglrx drivers can't get this depart point back anymore.

I think I have already tried almost everything, well including custom Intrepid kernel compiling + brand new Mesa 7.0.3..

I don't really want to reinstall the whole system again, it is too much of settings to do after.

My kernel image is now Intrepid: 2.6.28-direct

$> glxinfo```

OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)

```
$>lspci
```
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
```

#posting bit messy xorg.conf
```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "Default Screen" 0 0
	InputDevice    "Synaptics Touchpad"
EndSection
Section "Extensions"
Option "Composite" "Disable"
EndSection
Section "Files"
EndSection

Section "Module"
	Load  "glx"
	Load  "GLcore"
	Load  "dri"
	Load  "v4l"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizEdgeScroll" "0"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
	VendorName   "Generic LCD Display"
	ModelName    "LCD Panel 1680x1050"
	HorizSync    31.5 - 65.5
	VertRefresh  56.0 - 65.0
	Gamma        1
	ModeLine     "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
	ModeLine     "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
	ModeLine     "1280x768@60" 80.1 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
	ModeLine     "1280x720@60" 74.5 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
	ModeLine     "1280x800@60" 83.5 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
	ModeLine     "1440x900@60" 106.5 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
	ModeLine     "1600x1024@60" 136.4 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
	ModeLine     "1680x1050@60" 147.1 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
EndSection

Section "Monitor"
 # 
	Identifier   "monitor1"
	Gamma        1
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "radeon"
	VendorName  "ATI"
	BoardName   "ATI Radeon"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "on"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
 # 
	Identifier  "device1"
	Driver      "radeon"
	VendorName  "ATI"
	BoardName   "ATI Radeon"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1680x1050@60" "1600x1024@60" "1440x900@60" "1280x800@60" "1280x720@60" "1280x768@60" "800x600@60" "800x600@56"
	EndSubSection
EndSection

Section "Screen"
 # 
	Identifier "screen1"
	Device     "device1"
	Monitor    "monitor1"
	DefaultDepth     24
EndSection

```

If anyone has an idea how to get at least default settings (those were working well), please share an advice.

Thank you very much in advance,
..I am only few months on Linux (well, very intensive learning time), there are some problems sometimes.. but there is no way back to another OS!

x_off

---

### Post by Typhoeus on 2009-02-11
If you have a backup of your xorg.conf file (check /etc/X11/ you could have a backed up xorg.conf file even if you haven't manually backed it up) then all you need to do in a terminal is go to /etc/X11 and type

  sudo cp 'enter name of back up file' xorg.conf

this will over write your xorg.conf with the back up.

Hopes this helps someone.

---

### Post by x_off on 2009-02-12
Thanks for advice,

The think is that only modifying xorg.conf is not enough in my case, the system was completely messed up from my previous experiments to get fglrx working.. the best option how to get back your default driver is to uninstall all of things which has something to do with flgrx and reinstall "xserver-xorg-video-ati" whatever, then just type:
```

sudo dpkg-reconfigure xserver-xorg

```
which will bring; after few questions you can leave pretty default, your X back to original settings
..this worked for my old ati 9200 card
so,
direct rendering: yes
glxgears are now running around 2100fps (opensource ati)

good luck
x_off

---

### Post by Bablefish on 2009-02-12
If you head to where you found the driver there is a link to a pdf file that even tell you the correct way to comfigure it.

---

### Post by x_off on 2009-03-31
Thanks, yes there are tons of instructions on the web, official, semi-official, unofficial and then sort of damn hacks, but none of them is actually working for me.

The main problem is that old Ati drivers do not support newer Xorg, which is delivered by most of linux distros nowadays.. And switching to older X means lots of other incompatibility issues etc, etc. It is possibly better to buy a new card instead of messing up with this.. it seems the support is not going to be better anymore for older (just few years :-k) chipsets from AMD side, it is a sad fact.

But still, there are open source drivers and it's just fine for me, I am really not a hardcore gamer, sometimes playing chess.. even 3d, who cares about framerate :)

Anyway, if someone get any of Ati R2xx chipset on closed-source drivers and current Xorg working, please post your experience here, I am just wondering.

Thanks for your help,
best!
(happy Ubuntu user) xoff

---

### Post by jesse123 on 2009-05-05
i need help i cant get graphics card wprking ive read over forms n forms un able to detect i dont no please help email me [email]cyums@hotmail.com[/email] i am new to ubuntu and am bout to give up

---

### Post by 0guzhan on 2009-06-08
Same problem, ATI Radeon 9200 SE, couldn't find XOrg! 

But it's not possible to buy a new video card that suits with my old board agp8x slot... 

No Country for Old Ati! :)

---

