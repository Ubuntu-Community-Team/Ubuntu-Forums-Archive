---
title: "Problem with tri-head driver conflict"
date: 2007-07-02
forum: Multimedia &amp; Video
---

### Post by oceanplexian on 2007-07-02
Hi, I'm having some trouble getting both the fglrx and nv drivers installed together. I'm guessing that there is some kind of conflict? If I use apt it tries to autoremove the nvidia package if I install fglrx and vice versa. Forcing it also doesn't work. 

Everything else is great, I have at least the nv prop driver running now. Xinerama disables xrandr, so beryl doesn't work. I'm guessing that's something that is an x.org issue and not something I could fix. Quite a few websites are pretty slow because I think transparent png's that rely on opengl. Also, I'm not sure if ajax relies on 3d accel, but it is pretty slow.


Also I'm now running Kubuntu Gusty Gibbon, but that shouldn't be important because I've had the issue on previous versions. My system is a 2.4ghz p4 with 768mb ram. If anyone has any experience with multi-head displays and has any advice on how I could get both drivers working or at least speed things up a bit would be great.

Here's some info and some of my xorg if it helps anyone. I do at least have a working tri-monitor setup so it might be a good resource.

> 02:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:05.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]


> Section "Device"
  identifier "ATI Technologies, Inc. RV350 AP [Radeon 9600]"
  boardname "atiradeon"
  busid "PCI:1:0:0"
  driver "radeon"
  screen 0
  option "MergedFB" "off"
  Option      "AGPFastWrite" "yes"

#Optimized values (changed from driver default)
	Option		"AGPMode" "4"
	Option		"AGPFastWrite" "on" #Faster than default (off)
	Option		"SWcursor" "off" #Faster than default (on)
	Option		"EnablePageFlip" "on" #Faster than default (off)
	Option		"AccelMethod" "XAA" # or XAA, EXA, XAA more stable, XAA is deafult
	Option		"DynamicClocks" "on"
	Option		"BIOSHotkeys"   "on"

#Left to driver default
#	Option		"RenderAccel" "on" #Default is "on"
#	Option		"DMAForXv" "on" #Default is on, use default value
#	Option		"SubPixelOrder" "RGB" #Force subpixel order to specified order. The default is NONE for CRT, RGB for digital panels, use default value
#	Option		"ColorTiling" "on" # Frame buffer can be addressed either in linear or tiled mode.The default value is on. Use default value.
#	Option		"DDCMode" "off" #Force to use the modes queried from the connected monitor. The default is off, use default value

#These are not mentioned in man page for driver
	Option		"AGPSize" "32" # default: 8
	Option		"EnableDepthMoves" "true"
EndSection

Section "Monitor"
  identifier "Generic Monitor"
  vendorname "Plug 'n' Play"
  modelname "Plug 'n' Play"
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  gamma 1.0
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "ATI Technologies, Inc. RV350 AP [Radeon 9600]"
  Monitor "Generic Monitor"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    modes "1280x1024@75" "1280x1024@60" "1152x864@75" "1280x960@75" "1024x768@60" "1600x1200@60" "1024x768@70" "1024x768@75" "832x624@75" "800x600@60" "800x600@75" "800x600@72" "640x480@75" "640x480@72" "640x480@60"
  EndSubSection
Option "UseEvents" "True"
EndSection

Section "ServerLayout"
  Identifier "Default Layout"
  screen 0 "Default Screen" 0 0
  screen 1 "Screen1" rightof "Default Screen"
  screen 2 "Screen2" leftof "Default Screen"
  screen 3 "Screen3" rightof "Default Screen"

  
  InputDevice "Generic Keyboard"
  InputDevice "Configured Mouse"
  Option "Xinerama" "true"
EndSection

Section "DRI"
  Mode 0660
EndSection


Section "device" #      
  identifier "device1"
  boardname "Radeon9200Pro"
  busid "PCI:02:05:1"
  driver "radeon"
  screen 1
  option "MergedFB" "off"
  Option      "AGPFastWrite" "yes"
        Option          "UseFBDev" "false"


EndSection


Section "screen" #      
  Identifier "Screen1"
  Device "Device1"
  Monitor "Monitor1"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    modes "1280x1024@75" "1280x1024@60" "1152x864@75" "1280x960@75" "1024x768@60" "1600x1200@60" "1024x768@70" "1024x768@75" "832x624@75" "800x600@60" "800x600@75" "800x600@72" "640x480@75" "640x480@72" "640x480@60"
  EndSubSection
Option "UseEvents" "True"
EndSection


Section "monitor" #      
  identifier "Monitor1"
  vendorname "Plug 'n' Play"
  modelname "Plug 'n' Play"
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  gamma 1.0
EndSection


Section "device" #      
  identifier "device2"
  boardname "NVIDIA GeForce FX (generic)"
  busid "PCI:2:0:0"
  driver "nvidia"
  screen 0
  vendorname "NVIDIA"

#Optimized values (changed from driver default)
	Option		"AGPMode" "4"
	Option		"AGPFastWrite" "on" #Faster than default (off)
	Option		"SWcursor" "off" #Faster than default (on)
	Option		"EnablePageFlip" "on" #Faster than default (off)
	Option		"AccelMethod" "XAA" # or XAA, EXA, XAA more stable, XAA is deafult
	Option		"DynamicClocks" "on"
	Option		"BIOSHotkeys"   "on"

#Left to driver default
#	Option		"RenderAccel" "on" #Default is "on"
#	Option		"DMAForXv" "on" #Default is on, use default value
#	Option		"SubPixelOrder" "RGB" #Force subpixel order to specified order. The default is NONE for CRT, RGB for digital panels, use default value
#	Option		"ColorTiling" "on" # Frame buffer can be addressed either in linear or tiled mode.The default value is on. Use default value.
#	Option		"DDCMode" "off" #Force to use the modes queried from the connected monitor. The default is off, use default value

#These are not mentioned in man page for driver
	Option		"AGPSize" "32" # default: 8
	Option		"EnableDepthMoves" "true"
        Option          "UseFBDev" "false"


EndSection


Section "screen" #      
  Identifier "Screen2"
  Device "Device2"
  Monitor "Monitor2"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    modes "1280x1024@75" "1280x1024@60" "1152x864@75" "1280x960@75" "1024x768@60" "1600x1200@60" "1024x768@70" "1024x768@75" "832x624@75" "800x600@60" "800x600@75" "800x600@72" "640x480@75" "640x480@72" "640x480@60"
  EndSubSection
Option "UseEvents" "True"
EndSection


Section "monitor" #      
  identifier "Monitor2"
  vendorname "Plug 'n' Play"
  modelname "Plug 'n' Play"
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  gamma 1.0
EndSection


Section "device" #      
  identifier "device3"
  boardname "ATI Radeon (9200)"
  busid "PCI:2:5:0"
  driver "ati"
  screen 0
  vendorname "ATI"
  option "MergedFB" "off"
  Option      "AGPFastWrite" "yes"


#Optimized values (changed from driver default)
	Option		"AGPMode" "4"
	Option		"AGPFastWrite" "on" #Faster than default (off)
	Option		"SWcursor" "off" #Faster than default (on)
	Option		"EnablePageFlip" "on" #Faster than default (off)
	Option		"AccelMethod" "XAA" # or XAA, EXA, XAA more stable, XAA is deafult
	Option		"DynamicClocks" "on"
	Option		"BIOSHotkeys"   "on"

#Left to driver default
#	Option		"RenderAccel" "on" #Default is "on"
#	Option		"DMAForXv" "on" #Default is on, use default value
#	Option		"SubPixelOrder" "RGB" #Force subpixel order to specified order. The default is NONE for CRT, RGB for digital panels, use default value
#	Option		"ColorTiling" "on" # Frame buffer can be addressed either in linear or tiled mode.The default value is on. Use default value.
#	Option		"DDCMode" "off" #Force to use the modes queried from the connected monitor. The default is off, use default value

#These are not mentioned in man page for driver
	Option		"AGPSize" "32" # default: 8
	Option		"EnableDepthMoves" "true"
        Option          "UseFBDev" "false"

EndSection


Section "screen" #      
  Identifier "Screen3"
  Device "Device3"
  Monitor "Monitor3"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    modes "1280x1024@75" "1280x1024@60" "1152x864@75" "1280x960@75" "1024x768@60" "1600x1200@60" "1024x768@70" "1024x768@75" "832x624@75" "800x600@60" "800x600@75" "800x600@72" "640x480@75" "640x480@72" "640x480@60"
  EndSubSection
Option "UseEvents" "True"
EndSection


Section "monitor" #      
  identifier "Monitor3"
  vendorname "Plug 'n' Play"
  modelname "Plug 'n' Play"
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync

  gamma 1.0
EndSection

Section "Extensions"
 Option "composite" "false"
EndSection


---

