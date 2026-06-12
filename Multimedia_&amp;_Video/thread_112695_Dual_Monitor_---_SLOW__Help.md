---
title: "Dual Monitor --- SLOW  Help"
date: 2006-01-04
forum: Multimedia &amp; Video
---

### Post by greenwom on 2006-01-04
Ok so I installed my new video card (Nvidia GX 5500) with 128Mb of ram.
It was great, was playing with compositing, It was great!!  Then I started setting up the second monitor and then if I run anything like TV or DVD it dogs down the system.....  I think I must have a config missing or messed up.  

I've played around and looked into other threads but I'm stuck.......

here's my xorg.conf
```
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
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
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier "Configured Mouse"
	Driver "mouse"
	Option "Protocol" "evdev"
	Option "Dev Name" "A4Tech USB Optical Mouse" # cat /proc/bus/input/devices
	Option "Dev Phys" "usb-0000:00:1d.1-2/input0" # cat /proc/bus/input/devices
	Option "Device" "/dev/input/input0" #event4
	Option "Buttons" "10"
	Option "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
        Identifier 	"cursor"
        Driver 		"wacom"
	Option 		"Device"		"/dev/ttyS0"         
        Option 		"Type" 			"cursor"
EndSection

Section "InputDevice"
        Identifier 	"stylus"
        Driver 		"wacom"
        Option 		"Device" 		"/dev/ttyS0
        Option 		"Type" 			"stylus"
EndSection

Section "InputDevice"
        Identifier 	"eraser"
        Driver 		"wacom"
        Option 		"Device" 		"/dev/ttyS0
       Option 		"Type" 			"eraser"
EndSection

Section "Device"
	Identifier	"NVIDIA GeForce FX5500 PCI"
	Driver		"nvidia"
	BusID		"PCI:2:11:0"
	Option          "RenderAccel"           "true"
##	Option 		"CursorShadow" 		"1"	### Added for effects not used (just in case)
	Option          "AllowGLXWithComposite" "true"
#	Option 		"Coolbits" 		"1"     ### Another effect 
	Screen		0
######################Comment this out if you want two seperate displays and not a stretched display#############
	Option "NvAGP" "3" 
	Option "Twinview" "TRUE"
	Option "TwinViewOrientation" "RightOf"
	Option "SecondMonitorHorizSync" "28-64"
	Option "SecondMonitorVertRefresh" "43-60"
	Option "MetaModes" "1280x1024 , 1280x1024" 
	Option "ConnectedMonitor" "CRT , CRT"
##################################################################################################################
EndSection

Section "Extensions"
	Option		"Composite" "Enable"
EndSection

Section "Monitor"
	Identifier	"Eview 17f"
	Option		"DPMS"
	HorizSync	30-72
	VertRefresh	50-160
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection


Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA GeForce FX5500 PCI"
	Monitor		"Eview 17f"
	DefaultDepth	24
	
	SubSection "Display"
		#Viewport 0 0
		Depth		1
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		#Viewport 0 0
		Depth		4
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		#Viewport 0 0
		Depth		8
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		#Viewport 0 0
		Depth		15
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		#Viewport 0 0
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		#Viewport 0 0
		Depth		24
		Modes		"1280x1024"  
	EndSubSection
EndSection

################################# uncomment if you want a two display device
#Section "Device"
#	Identifier	"NVIDIA Head 2"
#	Driver		"nvidia"
#	BusID		"PCI:2:0:0"
#	Option		"NoLogo"
#	Screen		1
#EndSection
#
#
#Section "Monitor"
#	Identifier	"HP Pavilion mx70"
#	Option		"DPMS"
#	HorizSync	28-64
#	VertRefresh	43-60
#	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
#EndSection
#
#Section "Screen"
#	Identifier	"Screen 2"
#	Device		"NVIDIA Head 2"
#	Monitor		"HP Pavilion mx70"
#	DefaultDepth	24
#	
#	SubSection "Display"
#		Depth		24
#		Modes		"1280x1024"  "1024x768" "800x600" "640x480"
#	EndSubSection
#	EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
#	Screen		0 "Default Screen" 0 0
#	Screen		1 "Screen 2" RightOf "Default Screen"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "cursor"  "AlwaysCore"
        InputDevice	"stylus"  "AlwaysCore"
	InputDevice	"eraser"  "AlwaysCore"
	Option 		"Xinerama" "Off"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by greenwom on 2006-01-04
I've also tried this, still get choppy video.

```

Section "Device"
	Identifier	"NVIDIA GeForce FX5500 PCI"
	Driver		"nvidia"
	BusID		"PCI:2:11:0"
	 Option 	"NvAGP" 		"2"
	Option          "RenderAccel"           "0"
	Option 		"CursorShadow" 		"1"
	Option 		"Coolbits" 		"1"     ### Another cursor 3d effect (leave it off) 
	Option          "AllowGLXWithComposite" "true"
	
	Screen		0
######################Comment this out if you want two seperate displays and not a stretched display#############
##	Option "NvAGP" "3" 
	Option "Twinview" "1"
	Option "TwinViewOrientation" "RightOf"
	Option "SecondMonitorHorizSync" "28-64"
	Option "SecondMonitorVertRefresh" "43-60"
	Option "MetaModes" "1280x1024 , 1280x1024" 
	Option "ConnectedMonitor" "CRT , CRT"
##################################################################################################################
	Option "NoPowerConnectorCheck"
EndSection

Section "Extensions"
	Option		"Composite" "Enable"
EndSection

Section "Monitor"
	Identifier	"Eview 17f"
	Option		"DPMS"
	HorizSync	30-72
	VertRefresh	50-160
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection


Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA GeForce FX5500 PCI"
	Monitor		"Eview 17f"
	DefaultDepth	24
	
	SubSection "Display"
		Viewport 0 0
		Depth		1
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		4
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		8
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		15
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		24
		Modes		"1280x1024"  
	EndSubSection
EndSection

################################# uncomment if you want a two display device
#Section "Device"
#	Identifier	"NVIDIA Head 2"
#	Driver		"nvidia"
#	BusID		"PCI:2:0:0"
#	Option		"NoLogo"
#	Screen		1
#EndSection
#
#
#Section "Monitor"
#	Identifier	"HP Pavilion mx70"
#	Option		"DPMS"
#	HorizSync	28-64
#	VertRefresh	43-60
#	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
#EndSection
#
#Section "Screen"
#	Identifier	"Screen 2"
#	Device		"NVIDIA Head 2"
#	Monitor		"HP Pavilion mx70"
#	DefaultDepth	24
#	
#	SubSection "Display"
#		Depth		24
#		Modes		"1280x1024"  "1024x768" "800x600" "640x480"
#	EndSubSection
#	EndSection

Section "ServerLayout"
	Identifier	"TwinView Configuration"
#	Identifier	"Default Layout"
#	Screen		0 "Default Screen" 0 0
#	Screen		1 "Screen 2" RightOf "Default Screen"
#	Screen		"Default Screen"
	Screen 	0 "Default Screen" 0 0 
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "cursor"  "AlwaysCore"
        InputDevice	"stylus"  "AlwaysCore"
	InputDevice	"eraser"  "AlwaysCore"
	Option 		"Xinerama" "Off"
EndSection

```

---

### Post by reet on 2006-01-04
Stick with what you have in your first post, but in the "Modules" section comment out the following lines:

Load "GLCore"
Load "dri"

Then try. If there is still problems, look in /var/log/Xorg.0.log at the lines that start with (WW) or (EE) to see if there is any problems loading something. (WW) = warning, (EE) = Error.

---

### Post by greenwom on 2006-01-05
Thanks, can't wait to get back to the house and try it out...

This is my first Dual Monitor setup and man even with choppy video I don't think I would go back!

---

### Post by greenwom on 2006-01-05
Thanks, can't wait to get back to the house and try it out...

This is my first Dual Monitor setup and man even with choppy video I don't think I would go back!

---

### Post by greenwom on 2006-01-05
I returned to the first xorg.conf and commented out the GLcore and dri...

I'm still getting a hanging in the video picture and some sound latency now (that wasn't there before)

These are ther xorg.log problems
```
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(WW) NVIDIA(0): Not using mode "840x525" (height 1050 is larger than
(WW) NVIDIA(0):      EDID-specified maximum 1024)
(WW) NVIDIA(0): Not using mode "700x525" (height 1050 is larger than
(WW) NVIDIA(0):      EDID-specified maximum 1024)
(WW) NVIDIA(0): Not using mode "1152x768":
(WW) NVIDIA(0):   horizontal sync start (1178) not a multiple of 8
(WW) NVIDIA(0): Not using mode "576x384":
(WW) NVIDIA(0):   horizontal sync start (589) not a multiple of 8
(WW) NVIDIA(0): Not using mode "360x200":
(WW) NVIDIA(0):   horizontal sync start (378) not a multiple of 8
(WW) NVIDIA(0): The user specified HorizSync "28.000-64.000" has been adjusted
(WW) (1680x1050,Eview 17f) mode clock 147.14MHz exceeds DDC maximum 110MHz
(WW) NVIDIA(0):      to "30.000-64.000" (the intersection with EDID-specified
(WW) NVIDIA(0):      HorizSync "30.000-70.000")
(WW) NVIDIA(0): The user specified VertRefresh "43.000-60.000" has been
(WW) NVIDIA(0):      adjusted to "47.000-60.000" (the intersection with
(WW) NVIDIA(0):      EDID-specified VertRefresh "47.000-120.000"
(WW) NVIDIA(0): Not using mode "1152x768":
(WW) NVIDIA(0):   horizontal sync start (1178) not a multiple of 8
(WW) NVIDIA(0): Not using mode "576x384":
(WW) NVIDIA(0):   horizontal sync start (589) not a multiple of 8
```

I think  I may try to comment out the ```
Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
```
EDIT: that didn't help.

I'm not running anything but it seems to be maxing out the system and that doesn't seem right.. I have nothing running but a browser and a tvtime....  So I think the system can handle it.  What else should I look at....

EDIT #2 I'm also getting 95% sytstem CPU ussage... This card should be handling more..

---

### Post by reet on 2006-01-05
As long as RenderAccel is set to "true", I don't see any problem. Perhaps the problem lies with your movie player? What program are you using? It sounds like the video is being rendered in software (no hardware acceleration). Look for the video output option and make sure it is set to "xv". Perhaps try a different program. I recommend mplayer or VLC.

You can run gnome-system-monitor to see the CPU usage for each individual program, if that helps.

[Edit: Another thing I though of was you could try disabling composite extensions.]

---

### Post by greenwom on 2006-01-06
I killed the composite lines but and I've continued to experiment with different configs I've found online.  They all seem to make sense but I'm also think it may be the software. 

I'm seeing the problem with Tvtime & Totem.  I haven't played much with Mplayer.  I was using it for DVD's but was having some full screen issues that I didn't have time to stamp out.  So I'll poke around foor harware settings and see what I come up with.

---

### Post by greenwom on 2006-01-06
Ok RenderAcel is on
Glcore and dpi are commented out
I'm using Mplayer, totem, tvtime, gxine.

Even with Mplayer and gxine set to xv driver I'm still getting the 100% swamp on the CPU.  
This is a little frustrating.  My old baseline 500Mhz Dell with 128Mb of RAM can run dual head with a DVD no problem (with XP).....  This is a 1.7Ghz desktop w/ 640Mb ram and a 128Mb Nvidia FX 5500 videocard.  I souldn't get this swamped....

I'm so open to suggestions.  The dual head system minus media is great....  but I want my TV.....

---

### Post by reet on 2006-01-06
Just noticed something else. You have set up currently in "Device":

	BusID		"PCI:2:11:0"

But in the commented section for using dual display without twinview, you have:

	BusID		"PCI:2:0:0"

The BusID is the address of where your video card is in the system. As far as I know it either is right or wrong, and if it's wrong xorg won't start. Would you run the command "lspci" and look for your video card in the list. For example, my BusID is "PCI:3:0:0" and what I see in the lspci command for my video card is:

0000:03:00.0 VGA compatible controller: nVidia Corporation: Unknown device 00f1 (rev a2)

So what I am wondering is if you video card is 2:11:0 or 2:0:0. Just a thought.

---

### Post by greenwom on 2006-01-06
2:11:0 is it.
If you run the command ```
 sudo X :1 -scanpci 
```
you get a good output.

This twinview system seems to be hogging CPU power....
I tried a few other apps like VLC and xawtv and they run with lower CPU but there's still really high: 62% for system.

Is there a mod that I need to run at startup?  HELP!!!!

---

