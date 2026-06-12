---
title: "Intel Dual-Head Display, Separate X Screens"
date: 2011-04-13
forum: Multimedia Software
---

### Post by leadbasedtoy on 2011-04-13
I'm having a hard time trying to figure this one out, it should be so simple. I have a PC with an Intel graphics chipset, i810 or something like that. It works fine with the Xorg Intel driver, with both screens acting as one giant desktop (extended desktop). However, I need each monitor to be it's own X desktop (similar to when you use the Nvidia settings app with an Nvidia card, you can set it to use TwinView or have separate X screens for each monitor.)

I've tried every config option I've found to disable Xinerama and MergedFB (at this point I'm certain it's Xinerama that's causing this, I don't think MergedFB is enabled.) It seems to have no effect. I've even tried starting X with the -xinerama option from the command line, it STILL gave me the extended desktop.

The reason I want to do this is because I'm designing a Kiosk that is supposed to utilize two touch screens at once. Each touch pointer needs to work on it's own display. Currently, it treats each touch screen as a normal pointer, so when you go from bottom-left to top-right of one touch screen, the pointer moves across both screens, which is not desirable. Nor can I find a way to lock the cursors to each screen or to an arbitrary limit.

Any help would be much appreciated. I feel like I'm missing something simple but I've been staring at it for far too long.

```
Section "ServerFlags"
	Option "Xinerama" "False"
EndSection

Section "ServerLayout"
	Identifier     "Layout0"
	Screen      0  "Screen0" 0 0
	Screen 	    1  "Screen1" 1380 0
	InputDevice    "Keyboard0" "CoreKeyboard"
	InputDevice    "TouchScreen0" "CorePointer"
	InputDevice    "TouchScreen1" "SendCoreEvents"
	Option         "MergedFB" "0"
	Option         "Xinerama" "0"
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
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "glx"
	Load  "dri2"
	Load  "extmod"
	Load  "record"
	Load  "dbe"
	Load  "dri"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier   "TouchScreen0"
	Driver	      "evdev"
	Option	      "Device" "/dev/input/event3"
	Option	      "DeviceName" "TouchScreen0"
	Option	      "ScreenNumber" "0"
	Option	      "Screen" "0"
	Option	      "Screenno" "0"
	Option	      "ReportingMode" "Raw"
	Option	      "AbsoluteScreen" "0"
	Option	      "Mode" "absolute"
	Option	      "width" "1280"
	Option	      "height" "1024"
	Option        "MinX" "76"
	Option        "MinY" "104"
	Option        "MaxX" "4000"
	Option        "MaxY" "4000"
	Option	      "x0" "0"
	Option	      "y0" "3"
	Option	      "x1" "7"
	Option	      "y1" "2"
	Option	      "x2" "1"
	Option	      "y2" "1"
	Option	      "x3" "-3"
	Option	      "y3" "0"
	Option	      "x4" "10"
 	Option	      "y4" "-2"
	Option	      "x5" "9"
	Option	      "y5" "0"
	Option	      "x6" "0"
	Option	      "y6" "2"
	Option	      "x7" "10"
	Option	      "y7" "3"
	Option	      "x8" "5"
	Option	      "y8" "0"
EndSection

Section "InputDevice"
	Identifier   "TouchScreen1"
	Driver	      "evdev"
	Option	      "Device" "/dev/input/event4"
	Option	      "DeviceName" "TouchScreen1"
	Option	      "ScreenNumber" "1"
	Option	      "Screen" "1"
	Option	      "Screenno" "1"
	Option	      "ReportingMode" "Raw"
	Option	      "AbsoluteScreen" "0"
	Option	      "Mode" "absolute"
	Option	      "width" "1280"
	Option	      "height" "1024"
	Option        "SendCoreEvents" "true"
	Option        "MinX" "76"
	Option        "MinY" "104"
	Option        "MaxX" "4000"
	Option        "MaxY" "4000"
	Option	      "x0" "0"
	Option	      "y0" "3"
	Option	      "x1" "7"
	Option	      "y1" "2"
	Option	      "x2" "1"
	Option	      "y2" "1"
	Option	      "x3" "-3"
	Option	      "y3" "0"
	Option	      "x4" "10"
 	Option	      "y4" "-2"
	Option	      "x5" "9"
	Option	      "y5" "0"
	Option	      "x6" "0"
	Option	      "y6" "2"
	Option	      "x7" "10"
	Option	      "y7" "3"
	Option	      "x8" "5"
	Option	      "y8" "0"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
	Option       "Enable" "true"
	Option      "DPMS"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
	Option       "Enable" "true"
	Option      "DPMS"
EndSection

Section "Device"
        Option     "DRI" "False"
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "Mobile 915GM/GMS/910GML Express Graphics Controller"
	BusID       "PCI:0:2:0"
	Option      "MergedFB" "false"
	Option      "Xinerama" "false"
	Option      "monitor-VGA1" "Monitor0"
EndSection

Section "Device"
        Option     "DRI" "False"
	Identifier  "Card1"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "Mobile 915GM/GMS/910GML Express Graphics Controller"
	BusID       "PCI:0:2:0"
	Option      "MergedFB" "false"
	Option      "Xinerama" "false"
	Option      "monitor-DVI1" "Monitor1"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes     "1280x1024"
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Card1"
	Monitor    "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes     "1280x1024"
	EndSubSection
EndSection

```

---

### Post by tlroche on 2011-04-13
> **leadbasedtoy said:**
> However, I need each monitor to be it's own X desktop [...] I feel like I'm missing something simple

Well, I don't know much about xorg.conf, but I am noticing one thing: above you have

```
Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"

```

twice, but no

```
Section "Screen"
	Identifier "Screen1"
	Device     "Card0" # or "Card1", I dunno
	Monitor    "Monitor1"

```

Shouldn't there be one of each?

---

### Post by leadbasedtoy on 2011-04-13
Good catch. I made the change (changed the second section to reference Monitor1). Didn't seem to have an effect.

---

### Post by speedbird25 on 2011-05-08
Hi!

So, it seems that I found another one with the same problems. We've spent now almost a whole week to get our multi-touchscreen (not multitouch!) setup to work. We have 2 graphics cards and 9 touchscreens (3M). We tried different Ubuntu version but none had a success. Now we're trying with the lastest (11.04) and the evdev driver.

It was much effort to initially get even the touchscreens working. But now, we're stuck with the same problem, that the outputs of every touchscreen is visible only on the first X screen.

We tried [http://www.x.org/wiki/XInputCoordinateTransformationMatrixUsage](http://www.x.org/wiki/XInputCoordinateTransformationMatrixUsage) (available in 11.04) but that had only again results on the first X screen. We did a setup to have 5 screens (each 1920x1080) in a row and applied a matrix with scaling factors 0.2 for x and offsets 0, 0.2, 0.4, 0.6, 0.8. This had the result that movements on the touchscreens where all still visible on the first X screen but only scaled by the factors and offsets applied. E.g. touchscreen #1 with scaling factor 0.2 and offset 0.2 had a x-coordinate range of 1920 * 0.2 to 1920 * 0.4. We expected to be rather 0.2 * 1920 * 5 to 0.4 * 1920 * 5.

So, I just discovered the Option "AbsoluteScreen" of the evdev driver, but that option seems to be outdated and not be used. I got this info by comparing the man pages of different versions: [http://manpages.ubuntu.com/manpages/hardy/man4/evdev.4.html](http://manpages.ubuntu.com/manpages/hardy/man4/evdev.4.html). There you can see that the option dropped with Ubuntu 8.04.

So my question to anyone that has a multi-touchscreen successfully running is: How can I attach the touchscreen movements to a X screen? Is the Option "AbsoluteScreen" of the evdev driver valid or not, and if not, are there any other options that will bind the touchscreen movements to a X screen.

Thanks in advance,
Stephan

---

### Post by speedbird25 on 2011-05-09
FYI I posted my question also on Ubuntu launchpad ([https://answers.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+question/156612](https://answers.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+question/156612)) and on the xorg mailinglist ([http://lists.freedesktop.org/mailman/listinfo/xorg](http://lists.freedesktop.org/mailman/listinfo/xorg)).

---

