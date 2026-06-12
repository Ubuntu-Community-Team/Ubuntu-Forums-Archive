---
title: "Xlib:  extension &quot;XFree86-DRI&quot; missing on display &quot;:0.0&quot;."
date: 2007-04-19
forum: Multimedia &amp; Video
---

### Post by universalguitarist on 2007-04-19
Hi,  I just recently installed Ubuntu Feisty and I'm having some trouble with ATI's new 8.36.5 drivers working with Feisty.  I get the error Xlib:  extension "XFree86-DRI" missing on display ":0.0"..  Here's a copy of my xorg.conf:

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
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
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "glx"
	Load  "extmod"
	Load  "freetype"
	Load  "int10"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
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
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

Section "ServerFlags"
Option "AIGLX" "off"
EndSection

I've tried reinstalling the drivers and various other little things.  I was going to go back to ATI's 8.35.5 driver because they worked last time I used Feisty, but I can't find the patch to rebuild the fglrx kernel without getting an error.  Anybody know what's going on?

Oh, and my card is an ATI Radeon X700 PCI-E

---

### Post by fsando on 2007-04-19
> **universalguitarist said:**
> Hi,  I just recently installed Ubuntu Feisty and I'm having some trouble with ATI's new 8.36.5 drivers working with Feisty.  I get the error Xlib:  extension "XFree86-DRI" missing on display ":0.0"..  
<snip>
Oh, and my card is an ATI Radeon X700 PCI-E

Hi universalguitarist, did you do a search on that exact error message here in the forums?
I believe most of us with ati cards have seen it and many have posted your  question. I remember I did some months ago - I don't recall the solution right now (don't have beryl at the moment) but I believe it is related to beryl/xgl and it was solved by following some tutorial.

---

### Post by universalguitarist on 2007-04-19
Yes I did, all I got was Disable Composite and AIGLX in the xorg.conf, which as you can see I already have.  I may have overlooked one that best suites my problem though.  I don't use beryl/compiz or even have either one installed at the moment, I just want my drivers to be fully functional.  Thanks for your reply fsando.

---

### Post by fsando on 2007-04-19
This is my thread on the same issue as a new ubuntu user (just over a week of ubuntu) :)
[http://ubuntuforums.org/showthread.php?t=337539]("http://ubuntuforums.org/showthread.php?t=337539")

The first answer:
> That is all normal side effects from using XGl. You can not use 3d acceleration when using an XGL session.
Hope this helps you

---

### Post by universalguitarist on 2007-04-19
> **fsando said:**
> This is my thread on the same issue as a new ubuntu user (just over a week of ubuntu) :)
[http://ubuntuforums.org/showthread.php?t=337539]("http://ubuntuforums.org/showthread.php?t=337539")

The first answer:

Hope this helps you

I am not running an XGL session.  While I have used Ubuntu I've gotten this error several times and fixed it with no problem.  Usually all I had to do is reinstall the drivers.  I'm just missing something and I don't know what it is.  I think I've read somewhere that I need linux-restricted-modules installed and I don't.  Ubuntu's servers are so slow right now though it's not funny I'm getting an average speed of 6000 B/s.  Thanks for your help.

---

### Post by universalguitarist on 2007-04-19
Nevermind I just realized what that package is.  still no direct rendering

---

