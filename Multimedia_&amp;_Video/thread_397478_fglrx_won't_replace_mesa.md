---
title: "fglrx won't replace mesa"
date: 2007-03-30
forum: Multimedia &amp; Video
---

### Post by Sponger on 2007-03-30
I need help!
I have spent the last couple days reading everything I can about getting the fglrx driver to work and this just seems beyond my realm of comprehension. I even went back today and tried the newest driver straight from the ATI website (released march 28) but that did not work either.
I'm new to linux but I'm definitely not new to computers... trying the make they transition from Windows but just a couple things seem to stand in my way.

I know the problem lies here:

fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

I have composite disabled and my xorg.conf says "fglrx" instead of ati or anything else.

any suggestions? I'm truly at a loss... :confused:

---

### Post by crispy_420 on 2007-03-31
Post your xorg here mine works fine and I may be able to help you edit yours.

---

### Post by Sponger on 2007-03-31
here is my xorg.conf:


Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. RV370 5B62 [Radeon X600 (PCIE)]"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"DELL E196FP"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. RV370 5B62 [Radeon X600 (PCIE)]"
	Monitor		"DELL E196FP"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
Option "Composite" "false"
EndSection



Hope you find something I missed!

---

### Post by Pugwash on 2007-04-01
How did you install the ati drivers? Also have you updated your kernel lately?

---

### Post by Sponger on 2007-04-01
I have recently updated my kernel, and for the ATI driver I downloaded it to my desktop (ver 8.35.5) and ran these commands:

 chmod +x ati-driver-installer-8.28.8.run
 ./ati-driver-installer-8.28.8.run 
aticonfig --initial

then I went back and added the lines to the end of my xorg.conf that disable composite.

I tried using the previous driver from the repos before this but it didn't work either, I was hoping the new one would make a difference.

thanks for helping, I have always been able to answer my questions from past threads but this one I just can't get.

---

### Post by Pugwash on 2007-04-01
> **Sponger said:**
> I have recently updated my kernel, and for the ATI driver I downloaded it to my desktop (ver 8.35.5) and ran these commands:

 chmod +x ati-driver-installer-8.28.8.run
 ./ati-driver-installer-8.28.8.run 
aticonfig --initial

then I went back and added the lines to the end of my xorg.conf that disable composite.

I tried using the previous driver from the repos before this but it didn't work either, I was hoping the new one would make a difference.

thanks for helping, I have always been able to answer my questions from past threads but this one I just can't get.

Have you tried this installing the drivers via this method - [https://help.ubuntu.com/community/BinaryDriverHowto/ATI?highlight=(Driver)%7C(ATI)#head-d8c6fd05bce340dfc3ad483abf0e18997868540b-2](https://help.ubuntu.com/community/BinaryDriverHowto/ATI?highlight=(Driver)%7C(ATI)#head-d8c6fd05bce340dfc3ad483abf0e18997868540b-2) 

You'll have to build the kernel module each time you update the kernel as mentioned in the link. I was having the same niggling troubles witht the mesa drivers but following the instructions  in the link solved it for me.

---

### Post by jcronkhite on 2007-04-01
Hey Sponger, I have an ATI x600 in my HP Pavilion zd8000.  I was beating my head against the wall for a couple of days when I found this:

[http://koti.mbnet.fi/waappu/edgy_ati_aiglx_beryl.html](http://koti.mbnet.fi/waappu/edgy_ati_aiglx_beryl.html)

Now I'm running Beryl with no problems.  I should also let you know that I'm a total Linux noob with no experience and it worked for me.  Let us know if it works out for you.  Good luck!

---

### Post by crispy_420 on 2007-04-02
I personally have used [this guide]("http://www.ubuntuforums.org/showthread.php?t=204910&highlight=fglrx") and was very happy with the results. You just have to change the file names to match your downloads.

By the way here is the part of my xorg concerning video:
> 
Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Driver      "fglrx"
	VideoRam    128
	Option	    "UseFBDev" "true"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Monitor    "SyncMaster"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666

---

### Post by Sponger on 2007-04-02
thanks for the advice everyone, sorry I took so long to post again, spent the better part of yesterday fixing a friends computer. (windows)

So... I followed the guide on [http://koti.mbnet.fi/waappu/edgy_ati_aiglx_beryl.html](http://koti.mbnet.fi/waappu/edgy_ati_aiglx_beryl.html) from jcronkhite and my computer flipped out. Restarted it at the end of the script and x wouldn't load. I restored my xorg.conf from a backup I made before I followed the guide, but no x.

I just don't know enough about linux yet to figure out every change that was made with that script so I guess I'm starting over tommorrow from scratch with a fresh install. What a pain. 

I'm not giving up, I'll post my results tommorow afternoon, thanks again :)

---

### Post by sdowney717 on 2007-04-02
if your running edgy use the ENVY installer

If your running feisty, try the system-admin-restricted drivers menu.

I had a terrible time getting mine to work, but I think they fixed the restricted drivers install as it is now working for me in feisty.

---

### Post by Sponger on 2007-04-03
WOW!

Thank you everyone for trying to help me, I finally got my Beryl up and running beautifully!

I had to reinstall my Edgy from the problem last night :( Then I started cleanly from scratch with the ATI driver by following the guide from Pugwash (thanks!) It took a little while to get everything going, but I then installed Beryl and Xgl according to the infamous hansen blog and presto! :)

This is so much more rewarding than Windows, and I love learning something new everyday!

---

### Post by skylark on 2007-04-04
I encountered exactly the same problem as sponger when I tried installing the fglrx drivers under a recent 64-bit feisty daily snapshot (I followed [this guide]("http://http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide")). My card is a lowly X300.

I eventually managed to find a solution. I simply added this section at the bottom of my /etc/X11/xorg.conf:

```
Section "Extensions"
        Option "Composite" "false"
EndSection
```

Now I have full 3D acceleration.

Disclaimer: I'm not sure what the side-effects are of a false Composite option.

Edit: just discovered that no Composite means no desktop effects like Beryl. I should be able to live without them :D

---

