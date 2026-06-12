---
title: "Big Desktop Too Wide - ATI Catalyst Control Center"
date: 2008-10-31
forum: Multimedia Software
---

### Post by ppatalano on 2008-10-31
I have two monitors that I have setup for "big desktop" via ati catalyst control center. One of the monitors is 1280x1024 and the other is 1680x1050, for some reason when I setup big desktop with this tool it only gives me one resolution choice of 5120x1050. This is much too big, the extra pixels are off to the right of my wide screen monitor. So its as if there is an extra 2160 pixels off to the right. I have an ATI hd2600pro graphics card and am using the restricted drivers with 8.10.

---

### Post by ppatalano on 2008-10-31
Anyone else having this problem?

---

### Post by drdan14 on 2008-11-03
I'm having the same problem with the same config (Intrepid 8.10) and same video card (ATI HD 2600 Pro). My two monitors are both 19" Viewsonic VA912b's, each with a max resolution of 1280x1024. Everything was working fine in 8.04 with my desktop spread across both monitors to be effectively 2560x1024 (and, in fact, that's what the resolution appears to be in my xorg.conf). The catalyst control center only allows me to choose 5120x1024 as my resolution.

Here's my current xorg.conf:
```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
		Virtual	2560 1024
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection
```

And here's my old xorg.conf:
```

# Xorg configuration created by system-config-display

Section "ServerLayout"
	Identifier	"single head configuration"
  screen 0 "aticonfig-Screen[0]" 0 0
	Inputdevice	"Mouse0"	"CorePointer"
	Inputdevice	"Keyboard0"	"CoreKeyboard"
EndSection

Section "Files"
	
	# RgbPath is the location of the RGB database.  Note, this is the name of the 
	# file minus the extension (like ".txt" or ".db").  There is normally
	# no need to change the default.
	# Multiple FontPath entries are allowed (they are concatenated together)
	# By default, Red Hat 6.0 and later now use a font server independent of
	# the X server to render fonts.
	Rgbpath		"/usr/X11R6/lib/X11/rgb"
	Fontpath	"unix/:7100"
EndSection

Section "Module"
	Load		"dbe"
	Load		"extmod"
	Load		"fbdevhw"
	Load		"glx"
	Load		"record"
	Load		"freetype"
	Load		"type1"
	Load		"dri"
	Load		"ddc"
EndSection

Section "InputDevice"
	
	# Specify which keyboard LEDs can be user-controlled (eg, with xset(1))
	#	Option	"Xleds"		"1 2 3"
	# To disable the XKEYBOARD extension, uncomment XkbDisable.
	#	Option	"XkbDisable"
	# To customise the XKB settings to suit your keyboard, modify the
	# lines below (which are the defaults).  For example, for a non-U.S.
	# keyboard, you will probably want to use:
	#	Option	"XkbModel"	"pc102"
	# If you have a US Microsoft Natural keyboard, you can use:
	#	Option	"XkbModel"	"microsoft"
	#
	# Then to change the language, change the Layout setting.
	# For example, a german layout can be obtained with:
	#	Option	"XkbLayout"	"de"
	# or:
	#	Option	"XkbLayout"	"de"
	#	Option	"XkbVariant"	"nodeadkeys"
	#
	# If you'd like to switch the positions of your capslock and
	# control keys, use:
	#	Option	"XkbOptions"	"ctrl:swapcaps"
	# Or if you just want both to be control, use:
	#	Option	"XkbOptions"	"ctrl:nocaps"
	#
	Identifier	"Keyboard0"
	Driver		"kbd"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Mouse0"
	Driver		"mouse"
	Option		"Protocol"	"IMPS/2"
	Option		"Device"	"/dev/input/mice"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"yes"
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	Vendorname	"Monitor Vendor"
	Modelname	"Unknown monitor"
	Horizsync	31.5	-	37.9
	Vertrefresh	50.0	-	70.0
	Option		"dpms"
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	#	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[1]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Device"
	Identifier	"Videocard0"
	Driver		"fglrx"
	Vendorname	"Videocard vendor"
	Boardname	"ATI Radeon X300"
	Option		"MonitorLayout"	"LVDS,AUTO"
	Option		"MergedXinerama"	"false"
	Option		"MergedFB"	"false"
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"fglrx"
	Option		"DesktopSetup"	"horizontal"
	Busid		"PCI:5:0:0"
EndSection

Section "Device"
	Identifier	"aticonfig-Device[1]"
	Driver		"fglrx"
	Busid		"PCI:5:0:0"
	Screen	1
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"Videocard0"
	Monitor		"Monitor0"
	Defaultdepth	16
	SubSection "Display"
		Viewport	0	0
		Depth	16
		Modes		"800x600"	"640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Viewport	0	0
		Depth	24
	EndSubSection
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen[1]"
	Device		"aticonfig-Device[1]"
	Monitor		"aticonfig-Monitor[1]"
	Defaultdepth	24
	SubSection "Display"
		Viewport	0	0
		Depth	24
	EndSubSection
EndSection

Section "DRI"
	Group	0
	Mode	0666
EndSection

Section "Extensions"
	Option		"Composite"	"1"
EndSection
```

---

### Post by ppatalano on 2008-11-03
Well I guess its reassuring to see that I'm not the only one that is having this problem. Let's see if we can figure out what is going on. This happens to you only when you activate the ATI driver correct?

---

### Post by drdan14 on 2008-11-03
> This happens to you only when you activate the ATI driver correct?

Right, which I did through Ubuntu in order to enable Compiz effects. Everything was working properly in Ubuntu 8.04.

---

### Post by clownschoolphd on 2008-11-03
Same problem over here.  6400x1200 when it should be 3200x1200.  xorg.conf reads 3200x1200.

I'm on a 64bit 8.10 desktop with a HD2400 pro graphics card.

---

### Post by ppatalano on 2008-11-05
Hah, I strange thing happened to me. I realized that I should have installed the 64 bit version, so I did. And the problem changed slightly so instead of it being so ridiculously wide it is now only 3360, but it still should be 2760.

Hmmmm :confused:

---

### Post by markayler on 2008-11-06
when you guys initially configured your dual monitor setup...did you have any problems? 

I have a similar configuration and I'm using the ATI Catalyst Control Center to configure my ATI Radeon HD 2400 XT, Multi Display to Big Desktop right of display 1...which works!, until I Reboot. After reboot..it just goes back to CLONE to Display 1.  

I used EnvyNG to install the ATI 8.543-Oubuntu4 driver. Maybe that's my mistake?

---

### Post by ppatalano on 2008-11-06
This is the only problem that I am having with dual monitors

---

### Post by ppatalano on 2008-11-08
Did either of you ever figure out a solution to this?

---

### Post by svamppi on 2008-11-27
Having the exact same problem. I have one widescreen (1680 wide) and a normal screen (1280 wide) I set up "big desktop" in ATI catalyst control center. With the standard screen on the right of the widescreen. I can only select 5920x1050 for the desktop area though. Also whenever I reboot my system, I am back to a cloned screen setup. I have not done a fresh install of 8.10, I first had some kind of home made attempt at a dualscreen setup with some ati command line xorg.conf modifying tool. Then I changed to the open source ati driver to get it to work as I wanted. Then I upgraded to 8.10, and tried enabling the proprietary driver again to see if something was going to be different. So I'm getting better results now with the proprietary driver than in 8.04 but it's not quite right yet. The overly big desktop as well as the resetting to a cloned setup are annoying.

---

### Post by Wintervenom on 2008-12-14
It has to do with the "Virtual" line in your xorg.conf.  Try commenting it out.  If you don't like the resolution it gives you, then change it to the resolution you want your monitors set to instead of the combined resolutions.

---

### Post by scrib71 on 2009-03-11
> **Wintervenom said:**
> It has to do with the "Virtual" line in your xorg.conf.  Try commenting it out.  If you don't like the resolution it gives you, then change it to the resolution you want your monitors set to instead of the combined resolutions.
This set me on the right track, thanks!

I have two 1400x1050 LCDs and a dual-DVI ATI card.  I wanted a desktop 2800x1050, but the ATI driver insisted on doubling that to 5600x1050.

I changed my *xorg.conf* from "[FONT="Courier New"]Virtual 2800 1050[/FONT]" to "[FONT="Courier New"]Virtual 1400 1050[/FONT]"

I have a nice, big desktop that properly fills both monitors.  My guess is that ATI is recognizing the dual monitor setup and making a "Virtual" screen for **each one**, effectively doubling their width.

---

### Post by markbuntu on 2009-03-11
Did any of you people ever file a bug report?
Someone should or it will never get fixed.

---

### Post by Willleung on 2009-03-29
had the same problem before.  Fixed by reinstalling both ubuntu and ati driver with both monitor connected.  It was mention in the ATi big desktop tread, so i gave it a shot and it worked, you might want to give it a try.

---

