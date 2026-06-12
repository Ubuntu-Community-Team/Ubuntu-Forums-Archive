---
title: "Default ATI Video Drivers vs. xorg-fglrx-drivers"
date: 2006-06-03
forum: Multimedia &amp; Video
---

### Post by heatvent on 2006-06-03
I read the hardware guide for Ubuntu Dapper 6.06 LTS here:
[URL="http://help.ubuntu.com/6.06/ubuntu/desktopguide/C/hardware.html"]
http://help.ubuntu.com/6.06/ubuntu/desktopguide/C/hardware.html[/URL]

I have an ASUS Pundit-R with ATI 9100 IGP graphics card built in.  Following the instructions, I ran the following in terminal to see if I am getting 3D support:

glxinfo | grep rendering

I got a "yes" response.  Seems good.  However, I went to play Army Ops and noticed that I need to downgrade the detail to low in order to play smoothly.  I was wondering if there are different levels of support for 3D or different levels of performance.  Also wondering if the fglrx driver would be a better driver to use.

Now this is the first time I have ever seen a linux OS support 3D at all on my ATI graphics card.  I have played around alot with the ATI proprietary drivers and numerous forum suggestions only to end up messing something up that I could not reverse.  So before messing around with what appears to be a pretty good setup, I was wondering if anyone had any suggestions on the xorg-fglrx-driver, whether it's better, faster, easier, etc.

Thanks.

---

### Post by BaffledMollusc on 2006-06-03
[QUOTE=heatvent]I read the hardware guide for Ubuntu Dapper 6.06 LTS here:
[URL="http://help.ubuntu.com/6.06/ubuntu/desktopguide/C/hardware.html"]
http://help.ubuntu.com/6.06/ubuntu/desktopguide/C/hardware.html[/URL]

I have an ASUS Pundit-R with ATI 9100 IGP graphics card built in.  Following the instructions, I ran the following in terminal to see if I am getting 3D support:

glxinfo | grep rendering

I got a "yes" response.  Seems good.  However, I went to play Army Ops and noticed that I need to downgrade the detail to low in order to play smoothly.  I was wondering if there are different levels of support for 3D or different levels of performance.  Also wondering if the fglrx driver would be a better driver to use.

Now this is the first time I have ever seen a linux OS support 3D at all on my ATI graphics card.  I have played around alot with the ATI proprietary drivers and numerous forum suggestions only to end up messing something up that I could not reverse.  So before messing around with what appears to be a pretty good setup, I was wondering if anyone had any suggestions on the xorg-fglrx-driver, whether it's better, faster, easier, etc.

Thanks.[/QUOTE]
If you're using the build-in driver for 3D that comes with Dapper, then yes, the fglrx driver should be much better. If you follow the instructions on that page you linked to ([http://help.ubuntu.com/6.06/ubuntu/desktopguide/C/hardware.html](http://help.ubuntu.com/6.06/ubuntu/desktopguide/C/hardware.html)) under the section "3D ATI Video Card Driver" you should be able to install the driver. By all means try it, and if it causes problems you can always change back.

---

### Post by gregdwih on 2006-06-04
[QUOTE=heatvent]I read the hardware guide for Ubuntu Dapper 6.06 LTS here:
[URL="http://help.ubuntu.com/6.06/ubuntu/desktopguide/C/hardware.html"]
http://help.ubuntu.com/6.06/ubuntu/desktopguide/C/hardware.html[/URL]

I have an ASUS Pundit-R with ATI 9100 IGP graphics card built in.  Following the instructions, I ran the following in terminal to see if I am getting 3D support:

glxinfo | grep rendering

I got a "yes" response.  Seems good.  However, I went to play Army Ops and noticed that I need to downgrade the detail to low in order to play smoothly.  I was wondering if there are different levels of support for 3D or different levels of performance.  Also wondering if the fglrx driver would be a better driver to use.

Now this is the first time I have ever seen a linux OS support 3D at all on my ATI graphics card.  I have played around alot with the ATI proprietary drivers and numerous forum suggestions only to end up messing something up that I could not reverse.  So before messing around with what appears to be a pretty good setup, I was wondering if anyone had any suggestions on the xorg-fglrx-driver, whether it's better, faster, easier, etc.

Thanks.[/QUOTE]
I installed driver following instructons, when i enter glxinfo | grep rendering, comes back direct rendering no. I don't know?

---

### Post by BaffledMollusc on 2006-06-04
[QUOTE=gregdwih]I installed driver following instructons, when i enter glxinfo | grep rendering, comes back direct rendering no. I don't know?[/QUOTE]
Strange... All I can tell you is what I did. I installed the fglrx driver using Synaptic, then modified the line in my /etc/X11/xorg.conf file from

Driver    "ati"

to

Driver   "fglrx"

and that worked fine.

---

### Post by heatvent on 2006-06-04
O.K. I installed the xorg-fglrx-driver package.  Then I tried using the xorg configuration editor per the Ubuntu guide.  That messed things up.  Asked a lot of questions that I didn't know the answer to.  So I restored my xorg.conf file - back to normal.  Then I manually edited xorg.conf and changed ati to fglrx.  Now I get a no response to direct rendering when I run glxinfo | grep rendering.

What else am I missing?

Here is my xorg.conf file:

> 
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
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
	Identifier	"ATI Technologies, Inc. Radeon 9100 A5 (R200 IGP)"
	Driver		"fglrx"
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"SDM-HS95"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9100 A5 (R200 IGP)"
	Monitor		"SDM-HS95"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
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



---

### Post by mzembe on 2006-06-05
It seems like there is a problem with the fglrx and R200 chips. My 8500le doesn't work right but the 9800 & X700 do. [Not all]("http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units") 9100's are R200's. I dunno 'tho - it might help to run **sudo update-pciids** .

Is the new armyops client out yet?

---

### Post by heatvent on 2006-06-05
I tried sudo update-pciids.  Not sure what this did but now I don't get direct rendering on the ati driver either.

I don't have any idean on armyops.  I'm using 2.6 which has been out for a while.

---

