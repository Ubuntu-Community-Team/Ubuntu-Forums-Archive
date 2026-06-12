---
title: "xrandr extension &quot;XRNADR&quot; missing on display &quot;0:0&quot;"
date: 2008-02-06
forum: Multimedia &amp; Video
---

### Post by mwiley63 on 2008-02-06
I am having a problem getting dual monitors to work on my system.  I have an ATI X800XL videocard and was able to get the drivers installed correctly on Ubuntu 7.04. 

The display is fine, however I am only getting output from the DVI, the VGA will not display anything.  I am unsure how I can enable this and I found that xrandr is an easy way to handle dual monitors.  

I have messed with the xorg.conf file so much that I had to rollback to the very first file 3 times, so this is starting to get frustrating being a newbie to Ubuntu.  

Hopefully someone with more knowledge then I can explain to me what I did wrong.  Here is some useful information:
-----------------------------------------------------------------------------------------------------------------------------
/lshw
*-pci:6
          description: PCI bridge
          product: MCP55 PCI Express bridge
          vendor: nVidia Corporation
          physical id: f
          bus info: pci@0000:00:0f.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
        *-display:0
             description: VGA compatible controller
             product: R430 [Radeon X800 XL] (PCIe)
             vendor: ATI Technologies Inc
             physical id: 0
             bus info: pci@0000:07:00.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             configuration: driver=fglrx_pci latency=0 module=fglrx
        *-display:1 UNCLAIMED
             description: Display controller
             product: R430 [Radeon X800 XL] (PCIe) (Secondary)
             vendor: ATI Technologies Inc
             physical id: 0.1
             bus info: pci@0000:07:00.1
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=0
-----------------------------------------------------------------------------------------------------------------------------
xorg.conf:

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
	Load  "GLcore"
	Load  "v4l"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "true"
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

Section "Monitor"
	Identifier   "Failsafe Monitor"
	VendorName   "Generic LCD Display"
	ModelName    "LCD Panel 1024x768"
	HorizSync    31.5 - 48.0
	VertRefresh  56.0 - 65.0
	Gamma        1
	ModeLine     "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
	ModeLine     "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
	ModeLine     "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
	ModeLine     "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
EndSection

Section "Monitor"
 # 
	Identifier   "monitor1"
	VendorName   "Generic LCD Display"
	ModelName    "LCD Panel 1024x768"
	HorizSync    31.5 - 48.0
	VertRefresh  56.0 - 65.0
	Gamma        1
	ModeLine     "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
	ModeLine     "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
	ModeLine     "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
	ModeLine     "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Failsafe Device"
	Driver      "vesa"
	BoardName   "vesa"
	BusID       "PCI:7:0:0"
EndSection

Section "Device"
 # 
	Identifier  "device1"
	Driver      "vesa"
	BoardName   "vesa"
	BusID       "PCI:7:0:0"
	Screen      1
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Failsafe Device"
	Monitor    "Failsafe Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1024x768@60" "800x600@60" "800x600@56" "640x480@60"
	EndSubSection
EndSection

Section "Screen"
 # 
	Identifier "screen1"
	Device     "device1"
	Monitor    "monitor1"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1024x768@60" "800x600@60" "800x600@56" "640x480@60"
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
-----------------------------------------------------------------------------------------------------------------------------

If anyone could help me I would greatly appreciate it.  I would like to stay with Ubuntu, but I can't do it without dual monitors!

---

