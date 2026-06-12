---
title: "Issue with dual video cards, dual monitor setup"
date: 2005-12-26
forum: Multimedia &amp; Video
---

### Post by timczer on 2005-12-26
I have read a ton of posts on the forums, and tried most of the solutions, but nothing seems to work.  I have tried a dozen or so xorg.conf setups that ZI have found here on the forums, but none seem to work for me.

First here is the xorg.conf:

Section "Module"
#	Load	"GLcore"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "ServerFlags"
   Option      "Xinerama"      "false"
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
	Option		"Buttons"	"9"
	Option		"ZAxisMapping"		"4 5		"
	Option		"Resolution"		"1000"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU]"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
	Screen		0
EndSection


Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
	Driver		"nvidia"
	BusID		"PCI:2:0:0" [COLOR="Red"](Actually ran this as PCI:1:7:0, but it crashed X)[/COLOR]
	Screen		1
EndSection

Section "Monitor"
	Identifier	"VA912b"
	Option		"DPMS"
	HorizSync	30-82
	VertRefresh	50-85
EndSection

Section "Monitor"
	Identifier	"G771"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"LeftScreen"
	Device		"NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU]"
	Monitor		"VA912b"
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

Section "Screen"
	Identifier	"RightScreen"
	Device		"NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
	Monitor		"G771"
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
	Identifier	"Layout"
	Screen	0	 "LeftScreen" 0 0
	Screen	1	"RightScreen" RightOf "LeftScreen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection


Note: On the second "device" setting, this is the new pci video card I added for the second monitor.  When Ubuntu boots, the boot sequence shows on the second monitor on this pci card.  When it goes to graphical sign in it goes to the monitor on the onboard video card.  I used a hoary live cd  and it loaded and ran on this card and monitor fine (but nothing from the onboard card).

I then went back to breezy and set up the xorg.conf exactly as it appeared from the live cd.    
The problem I have is is that the Busid is actually PCI:1:7:0, but X crashes with this entered, saying there is no configuration for this.  If I run lspci -X, it shows this is the busid for that card:
lspci -X
PCI:0:0:0 Host bridge: nVidia Corporation nForce2 AGP (different version?)
PCI:0:0:1 RAM memory: nVidia Corporation nForce2 Memory Controller 1
PCI:0:0:2 RAM memory: nVidia Corporation nForce2 Memory Controller 4
PCI:0:0:3 RAM memory: nVidia Corporation nForce2 Memory Controller 3
PCI:0:0:4 RAM memory: nVidia Corporation nForce2 Memory Controller 2
PCI:0:0:5 RAM memory: nVidia Corporation nForce2 Memory Controller 5
PCI:0:1:0 ISA bridge: nVidia Corporation nForce2 ISA Bridge
PCI:0:1:1 SMBus: nVidia Corporation nForce2 SMBus (MCP)
PCI:0:2:0 USB Controller: nVidia Corporation nForce2 USB Controller
PCI:0:2:1 USB Controller: nVidia Corporation nForce2 USB Controller
PCI:0:2:2 USB Controller: nVidia Corporation nForce2 USB Controller
PCI:0:4:0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller
PCI:0:5:0 Multimedia audio controller: nVidia Corporation nForce MultiMedia audio [Via VT82C686B]
PCI:0:6:0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP)
PCI:0:8:0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge
PCI:0:9:0 IDE interface: nVidia Corporation nForce2 IDE
PCI:0:30:0 PCI bridge: nVidia Corporation nForce2 AGP
[COLOR="Red"]PCI:1:7:0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000 AGP 8x][/COLOR]
PCI:1:8:0 Communication controller: Conexant: Unknown device 2f20
PCI:2:0:0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX - nForce GPU]

It seems to be at least the pci:1:7:0 that is the issue.
How do I get this monitor to work i a dual monitor setup?  Any help would be greatly appreciated.

---

### Post by timczer on 2005-12-27
anyone have any ideas on this?  Some further info, if it helps.  Under device manager, it lists the pci card under an "nForce External PCI Bridge".  Then it lists the new pci card.  Would this affect the BusID I should be using?

---

### Post by timczer on 2005-12-27
Never mind.  Found one more post that showed how to set up the xorg.conf and this one finally worked.  Now I have two working monitors! Yeah!!

---

### Post by crouton on 2005-12-28
(edit) Since I found something that appears to work correctly, I will post it.

Step 1: Do a 'lspci' and find the other video card's string.  For instance, my ATI Rage128 was "0000:02:09.0 VGA compatible controller: ATI Technologies Inc Rage 128 PP/PRO TMDS [Xpert 128]"

Step 2: Backup your current /etc/X11/xorg.conf just in case.  I made /etc/X11/xorg.conf.bak.

Step 3: 'sudo gedit /etc/X11/xorg.conf'.  Find the 'Device' Section and copy/paste it.  In the second 'Device', change your Identifier to a short identifier string, change the driver as necessary, and change the BusID to what you got from Step 1.  I've attached my xorg.conf file so you can take a look and see what I'm talking about.

Step 4: Still in gedit, copy the entire 'Screen' Section and paste it.  Change the Identifier to a short recognizable string and change the Device to match what you entered in the second Device section in Step 3.

Step 5: Go to the 'ServerLayout' Section.  Copy the existing Screen line, make the second version use the Identifier from Step 4, and then add 'RightOf' followed by the original Screen.  

Step 6: If necessary, you will need to make another 'Monitor' Section and feed the appropriate values.  I am using the default monitor setting and have two of the same monitor anyways.

Step 7: Save, exit, and restart X.  If it doesn't work, make sure that you have been consistent with your naming.  If you change the Identifier in one spot but not another, it will complain.

Here's my xorg.conf, for those who are interested (I've bolded the important parts):

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
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
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
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"Radeon 9600"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

[b]Section "Device"
	Identifier	"Rage128"
	Driver		"ati"
	BusID		"PCI:2:9:0"
EndSection[/b]

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device		"Radeon 9600"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
EndSection

[b]Section "Screen"
	Identifier	"Screen2"
	Device		"Rage128"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
EndSection


Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Screen1"
	Screen		"Screen2" RightOf "Screen1"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection
[/b]
Section "DRI"
	Mode	0666
EndSection


---

### Post by boxarocks on 2006-11-18
After more reconfigures than I care to count, I finally came upon this thread. What a lifesaver! I have 2 x nVidia GeForce 6300 cards and two 17" LCD monitors that I could not get to work with Ximerama or TwinView. Your example did the trick!:KS

---

