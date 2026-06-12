---
title: "ATI Radeon 9600PRO reverts to Mesa"
date: 2008-02-20
forum: Multimedia &amp; Video
---

### Post by lhardyl on 2008-02-20
I've been looking around the boards for people with a similar problem and there seems to be oodles of others with this problem. Is it just ATI cards that have this problem? (I'm yet to find any Nvidia cards that have been having this problem)

I've tried some of the fixes but none have worked. I've also ```
sudo dpkg-reconfigure -phigh xserver-xorg
```to revert my xorg.conf to default and reinstall ATI drivers (using either Envy or the guide from [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")

It only happens if I turn off my PC and boot up again. The reset button on my case doesn't revert to Mesa and neither does Ctrl+Alt+Bksp.

So my Q. Has anyone been able to get a permanent fix to this problem? (with 9600Pro)

My xorg.conf:

```
Section "Files"
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
	Identifier	"ATI Technologies Inc RV350 AP [Radeon 9600]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Monitor"
	Identifier	"HP w1907"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 AP [Radeon 9600]"
	Monitor		"HP w1907"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1440x1440"	"1440x900"	"1280x1024"	"1280x960"	"1152x1152"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
```

My fglrx output:
```
lhardyl@lhardyl-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
```

---

### Post by lhardyl on 2008-02-20
?bump?

---

### Post by lhardyl on 2008-02-21
any input?

Has anyone had a similar issue and since resolved it?

---

### Post by Giannis68 on 2008-02-21
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

**Verifying**

 Run the following command to check its output to ensure the fglrx driver is installed properly: 
 $ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.7281 Release
The OpenGL vendor string should read **ATI** and not **Mesa**. 
**If it still says *Mesa* and not *ATI*, even after re-enabling the driver from the Restricted-manager:** You can try the following: 
 [LIST]
[*]$ less /var/log/Xorg.0.log |grep EE if this command returns (EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work then remove the kernel module and reinstall it.[/LIST]  $ sudo dkms remove -m fglrx -v 8.452.1 --all   [LIST]
[*]Remove all the packages provided by the xserver-xorg-video-all meta-package (search for it using Synaptic or Adept), then restart the machine. The X Server should now use the new fglrx driver by force (provided the driver is being used in *xorg.conf*).[/LIST] If you can't log in after this, you'll have to log in to a terminal in the login screen, and reinstall the xserver-xorg-video-all package. Your problem is probably somewhere else. (taken from [[1]]("http://ubuntuforums.org/showpost.php?p=3655658&postcount=139")).   **If it says * libGL.so.1: cannot open shared object file: No such file or directory*...** Check if you have a */usr/lib/libGL.so.1.2*, if so do this: 
  $ ls -l /usr/lib/libGL*
[LIST]
[*] The file permission should be "-rw-rw-r--".  If the permission reads "-rw-rw----", do command[/LIST]  $ sudo chmod o+r /usr/lib/libGL.so.1.2
[LIST]
[*] If the permission is correct, fixed with command:[/LIST] $ sudo ln -s /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1

---

### Post by lhardyl on 2008-02-21
i can verify that the drivers install, however upon restart the drivers revert.

Any fix i do is temporary and will change back after restart, it's mind bogglingly annoying

---

### Post by myheadisfed on 2008-03-09
I have the same exact problem. I install the drivers with Envy, everything seems to go smoothly, then upon reboot my screen flashes on and off then it tells me that it will run in low graphics mode. When I check the graphics card setting under manual configuration it says it is a MESA driver...

have you since found a solution?

---

### Post by bsegovia on 2008-04-01
I'm having the exact same issue but with the Radeon 9800Pro...

Everytime I enable the restricted device for ati and reboot, it reverts me (after a lot of flashing) to low-graphics mode. Then i get stuck in 800x600 resolution. What kills me is that it was all working great until one day when i turned on the system, the resolution was strangely at a superhigh number. So I changed it. When i turned it back to a normal setting it flipped out on me, rebooted (i heard some voices speaking in a different language [wtf?]) and now i'm stuck with this video problem.

I've tried reverting to the opensource ati driver with limited success. I am able to change resolutions but anything higher than 1024x768 pushes the active window into a corner at the top left and the rest appear blocked by the ubuntu brown desktop. *see screenshot) (strange, the screenshot captured soemthing a bit different than what i'm seeing.

[IMG]http://i26.tinypic.com/v4qcmq.jpg[/IMG]

I've added the text of my xorg.conf below. I hope the problem is apparent.

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
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
	Identifier	"ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
	Boardname	"ati"
	Busid		"PCI:1:0:0"
	Driver		"fglrx"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"DELL P992"
	Vendorname	"Dell"
	Modelname	"Dell P992"
	Horizsync	30.0-107.0
	Vertrefresh	48.0-170.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x960@85" 148.5 1280 1344 1504 1728 960 961 964 1011 +hsync +vsync
  modeline  "1280x1024@85" 157.5 1280 1344 1504 1728 1024 1025 1028 1072 +hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@75" 202.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@70" 189.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@85" 229.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@75" 261.0 1792 1888 2104 2456 1344 1345 1348 1417 -hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
  modeline  "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
  modeline  "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
  modeline  "2048x1536@60" 266.95 2048 2200 2424 2800 1536 1537 1540 1589 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
	Monitor		"DELL P992"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	2048	1536
		Modes		"1280x1024@85"	"1280x1024@60"	"1280x960@85"	"1280x960@75"	"1280x960@60"	"1400x1050@60"	"1280x1024@75"	"1400x1050@75"	"1152x864@75"	"1600x1200@65"	"1024x768@43"	"1600x1200@60"	"1024x768@60"	"1600x1200@75"	"1024x768@70"	"1600x1200@70"	"1024x768@75"	"1600x1200@85"	"1024x768@85"	"1792x1344@75"	"832x624@75"	"1792x1344@60"	"800x600@60"	"1856x1392@60"	"800x600@85"	"1920x1440@60"	"800x600@75"	"2048x1536@60"	"800x600@72"	"800x600@56"	"640x480@85"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
	Load		"dbe"
	Load		"v4l"
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"ati"
	Busid		"PCI:1:0:0"
	Driver		"fglrx"
	Screen	1
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
```

---

### Post by wallsensus on 2008-05-22
Hello,

While I'm not specifically adding anything to the solution, I experience the same issue with an ATI Radeon HD 2600 Pro.  So it is not limited to your model.  I have installed the ATI driver 8.476 and I used the guide located here with method 2 (manual install): [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide")

Note: the guide currently shows the use of driver version 8.5.

It is exactly the same, restarting my machine causes the settings to revert, but simply restarting X or hitting the reset button doesn't do it.

Strange indeed.

---

### Post by wallsensus on 2008-05-22
I've recently tried the following line after I had got the drivers working properly and I am running fglrx:

```
sudo depmod -ae
```

And everything seems to be working after restart.

Can someone else try this to confirm I'm not entirely mad?

---

### Post by defe007 on 2008-05-28
I think I have solved this problem, at least for myself.

My problem was that I still had the xserver-xgl installed, which caused my computer to revert back to Mesa.  If you follow the instructions here [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Removing_Mesa_drivers]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Removing_Mesa_drivers") it should fix your problem!

My new fglrxinfo output:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON 9600/9700 Series
OpenGL version string: 2.1.7412 Release

```

---

### Post by pksings on 2008-05-30
I just fixed mine, driver was blacklisted.
/etc/modprobe.d/blacklist-local, put a "#" in front of fglrx, reboot, works fine.

---

