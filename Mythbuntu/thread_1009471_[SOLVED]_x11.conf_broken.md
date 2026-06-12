---
title: "[SOLVED] x11.conf broken"
date: 2008-12-12
forum: Mythbuntu
---

### Post by Eric Boring on 2008-12-12
Hi,

I had mythbuntu running nicely using a modifed x11.conf which sent entire desktop to the Hauppauge 350 tv out. That conf file is pasted below. 

I could not leave well enough alone and tried running that installation on a different mother board. This seemed to work ok, but the video resolution did not work, and rather than mess around with it, I switched everything back to the way it was. However, now my video out to the 350's TV out is not working. It there, either black screen or with a flashing curser in the corner. 

Near as I can tell, the x11.conf file has not changed from when it worked. Is there a way to tell ubuntu to use the proper x11.conf file? Or did something subtle get changed when I tried to use the other motherboard? 

Everything else on the machine seems to work. I can still use Mythweb and can watch from my windows machine. Just no TV out display.

```
Section "Files"
	Fontpath	"/usr/share/X11/fonts/misc"
	Fontpath	"/usr/share/X11/fonts/cyrillic"
	Fontpath	"/usr/share/X11/fonts/100dpi/:unscaled"
	Fontpath	"/usr/share/X11/fonts/75dpi/:unscaled"
	Fontpath	"/usr/share/X11/fonts/Type1"
	Fontpath	"/usr/share/X11/fonts/100dpi"
	Fontpath	"/usr/share/X11/fonts/75dpi"
	Fontpath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

# Specific modules needed *this is important.*
Section "Module"
	Load		"dbe"
	Load		"v4l"
	Load		"extmod"
	Load		"type1"
	Load		"freetype"
EndSection

# Almost standard keyboard 
# Note: This setup doesn't require the keyboard to be present

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

# Almost standard mouse pointer
# Note: This setup doesn't require the mouse to be present

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Hauppauge PVR 350 iTVC15 Framebuffer"
	
	# the driver we installed - in Gutsy, this is NOT "ivtvdev".
	Driver		"ivtv"
	
	# frame buffer we found above
	Option		"fbdev"	"/dev/fb0"
	Option		"TVStandard"	"NTSC-M"
	Option		"VideoOverlay"	"on"
	Option		"XVideo"	"1"
	
	# below settings are optional I've seen lots of people with them commented out.
	# I believe that pal users should just comment below line out.
	
	# Not optional setting
	# BusID we found with lspci converted as shown above
	Busid		"PCI:01:09:0"
	
	Screen	0
	
EndSection

# these settings are generic (for TVs) but are specifically for TV

Section "Monitor"
	Identifier	"TV"
	Horizsync	30-68
	Vertrefresh	50-120
	Displaysize	183	122
  Mode "720x480"
		Dotclock	34.564
		Htimings	720	752	840	928
		Vtimings	480	484	488	504
		Flags		"-HSync"	"-VSync"
  EndMode
	
	
	# for pal users:
	#Section "Monitor"
	#       Identifier  "TV"
	#       HorizSync  30-68
	#       VertRefresh 50-120
	#       Mode "720x576"
	#       D: 41.475 MHz, H: 44.693 kHz, V: 74.488 Hz
	#       DotClock 41.476
	#       HTimings 720 752 840 928
	#       VTimings 576 580 584 600
	#       Flags    "-HSync" "-VSync"
	#       EndMode
	#EndSection
	#for pal users more settings: http://www.mythtv.org/wiki/index.php/XV_on_PVR-350#PAL 
	
	# Sorry SECAM users I don't have the codes for that but I did see them on the web
	# So seek and you will find.  There are some resources at the bottom of this 
	# webpage to help out.
	
EndSection


# Our PVR-350 Driver entry
Section "Screen"
	Identifier	"TV Screen"
	Device		"Hauppauge PVR 350 iTVC15 Framebuffer"
	Monitor		"TV"
	Defaultdepth	24
	Defaultfbbpp	32
	SubSection "Display"
		Depth	24
		Fbbpp	32
		Modes		"720x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "TV Screen"
	
	# There is other ways to get rid of keyboard and mouse, but you can these settings as is.
	# This setup is designed to run without keyboard and mouse plugged in.
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666#	Not	specifically	needed	as	far	as	I	know.
	# I think it's specific to my computer's hardware
	# That said all my ubuntu boxes have this line.
	
EndSection
```

Thanks for your help!

---

### Post by Eric Boring on 2008-12-13
Hey, I just wanted to report that I found the solution: When I put hte PVR 350 card back into the old box, I put it in a different PCI slot. What do you know, but that changed the BusID! After running:
```

lspci | grep "Internext Compression" 
``` and converting the BusID from hexadecimal to decimal, changing that line in xorg.conf and rebooting the computer, X-out  through the PVR350 works again. 

Hope my bonheaded mistake can help someone else out in the future.
-Josh

---

