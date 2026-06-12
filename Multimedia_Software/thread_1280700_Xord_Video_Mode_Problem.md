---
title: "Xord Video Mode Problem"
date: 2009-10-02
forum: Multimedia Software
---

### Post by bsntech on 2009-10-02
Hi Folks,

I am not able to get the video display to show correctly.  I have a custom-created xorg.conf file that I made by running "Xorg --configure" and then made a few changes.

The HDTV I have will do 1366x768 for resolution.  The Xabre 330 card I have supports the 1360x768 mode.

I just made the change to the "Modes" line yesterday night.  Upon reboot, the "Display" applet under System - Preferences - Display showed the 1360x768 and it WAS active.

However, I rebooted afterwards and now it is stuck in 1024x768 mode - even though it isn't specified in the xorg.conf file.  The Display applet also shows this is the highest resolution possible.

Is there anywhere else in the system that would prevent the mode from displaying now - or another setting somewhere that is telling the X Server to use 1024x768 and not 1360x768 like what is set in the xorg.conf file?

Here is the file I have:

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "extmod"
	Load  "record"
	Load  "dri"
	Load  "glx"
	Load  "dri2"
	Load  "dbe"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
	Identifier  "Card0"
	Driver      "sis"
	VendorName  "Silicon Integrated Systems [SiS]"
	BoardName   "330 [Xabre] PCI/AGP VGA Display Adapter"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	DefaultDepth	24
        SubSection      "Display"
                Depth   24
                Modes "1360x768"
        EndSubSection
EndSection


```

---

### Post by bsntech on 2009-10-02
I did some more research and have changed my xorg.conf file to include ModeLine lines under the Monitor heading as such:

```
       ModeLine "1360x768"   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync
        ModeLine "1280x768"   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync
        ModeLine "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
        ModeLine "640x480"   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
        ModeLine "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
        ModeLine "640x480"   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
        ModeLine "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
        ModeLine "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync

```

Still, it sticks in 1024x768 mode as the best mode.  When checking the Xorg.0.log file, I see this:

```
(II) SIS(0): "Unknown reason" in the following list means that the mode
(II) SIS(0): is not supported on the chipset/bridge/current output device.
...
(II) SIS(0): Not using default mode "1360x768" (unknown reason)
...
(II) SIS(0): Not using mode "1360x768" (no mode of this name)
(--) SIS(0): Virtual size is 1024x768 (pitch 1024)

```

What I don't understand is that the 1360x768 mode DID work at least once after I changed the xorg.conf to the first post posted in this thread - without the ModeLine lines.  Then after a few reboots - poof! Back to 1024x768.

The EDID on the HDTV does show that it supports 1360x768 - hence where I originally was able to get the information to setup the ModeLine lines.

So why all of a sudden does the card say that it isn't supported by the chipset/bridge/output device?

---

