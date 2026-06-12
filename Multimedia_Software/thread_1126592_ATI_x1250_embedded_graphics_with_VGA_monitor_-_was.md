---
title: "ATI x1250 embedded graphics with VGA monitor - washed out display"
date: 2009-04-15
forum: Multimedia Software
---

### Post by wetmonkey on 2009-04-15
System:
AMD 64 w/ x1250 ATI embedded video card
Ubuntu 8.10
```
01:05.0 VGA compatible controller: ATI Technologies Inc RS690 [Radeon X1200 Series]

```
VGA and DVI outputs, both connected to identical Dell 1908p monitors
Using open source ATI driver with minimal xorg config which mimics BigDesktop.

The VGA monitor displays completely washed out.  I have adjusted contrast/brightness/color settings on the monitor for two days, and none of it helps. 
An example of washed out is this forum.  A thread on the VGA screen will have no distinctions in color.  It's solid white with a mustard yellow stripe down the sides where the ubuntu brown background is. 
This page: [http://sedition.com/perl/rgb.html](http://sedition.com/perl/rgb.html) displays as all white for the first 2 rows, and the 4th and 5th row (minus the black and dark slate gray).  
I can psuedo fix it by dropping gamma down ($gamma -xgamma .425), but it munges the blacks and makes the DVI monitor horrible. 
Black and white display correctly (no grey). 

I have tried ddccontrol but the monitor is not found. 

This monitor was connected to a windows box and displayed fine.  I also connected two other monitors to the VGA output and they displayed the same washed out effect. When I click the 'auto-adjust' on the monitor as it goes through the cycles there is one point where it's perfect, but then it finishes as washed out. 

I feel like I need to adjust the output brightness, but can not find a way to do that. However, there may be a more appropriate fix available.  I have run out google foo.. 

I am not opposed to switching drivers but I have to have the big desktop effect which I could not accomplish previously.  (It would work through the login screen but once gnome loaded it switched to mirror)

```

$xrandr
Screen 0: minimum 320 x 200, current 2560 x 1024, maximum 3200 x 1024
VGA-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+   75.0     60.0     60.0* 
   1600x1024      60.2  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8  
   1152x864       75.0     75.0     75.0     70.0     60.0  
   1024x768       75.1     75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     75.0     60.0     59.9  
   720x400        70.1  
HDMI-0 disconnected (normal left inverted right x axis y axis)
DVI-0 connected 1280x1024+1280+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+   75.0     60.0     60.0* 
   1600x1024      60.2  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8  
   1152x864       75.0     75.0     75.0     70.0     60.0  
   1024x768       75.1     75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     75.0     60.0     59.9  
   720x400        70.1  



```

xorg.conf
```

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	3200 1024
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option "AllowDDCCI" "true"
EndSection



```


```

(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: 4025  Serial#: 843593804
(II) RADEON(0): Year: 2007  Week: 48
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max Image Size [cm]: horiz.: 38  vert.: 30
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.080   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Serial No: UW0427C12H8L
(II) RADEON(0): Monitor name: DELL 1908FP
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 83 kHz, PixClock max 140 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac25404c384832
(II) RADEON(0): 	3011010368261e782eeea5a3544c9926
(II) RADEON(0): 	145054a54b00714f8180010101010101
(II) RADEON(0): 	010101010101302a009851002a403070
(II) RADEON(0): 	1300782d1100001e000000ff00555730
(II) RADEON(0): 	34323743313248384c0a000000fc0044
(II) RADEON(0): 	454c4c203139303846500a20000000fd
(II) RADEON(0): 	00384c1f530e000a2020202020200084
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "DEL", prod id 16421
(II) RADEON(0): I2C device "HDMI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "HDMI-0:ddc2" removed.
(II) RADEON(0): Output: HDMI-0, Detected Monitor Type: 0
invalid output device for dac detection
(II) RADEON(0): EDID vendor "DEL", prod id 16422
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x60.0  108.88  1280 1360 1496 1712  1024 1025 1028 1060 -hsync +vsync (63.6 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: 4026  Serial#: 825447509
(II) RADEON(0): Year: 2007  Week: 47
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 38  vert.: 30
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.080   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Serial No: UW0427BN13TU
(II) RADEON(0): Monitor name: DELL 1908FP
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 83 kHz, PixClock max 140 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac264055543331
(II) RADEON(0): 	2f11010380261e782eeea5a3544c9926
(II) RADEON(0): 	145054a54b00714f8180010101010101
(II) RADEON(0): 	010101010101302a009851002a403070
(II) RADEON(0): 	1300782d1100001e000000ff00555730
(II) RADEON(0): 	343237424e313354550a000000fc0044
(II) RADEON(0): 	454c4c203139303846500a20000000fd
(II) RADEON(0): 	00384c1f530e000a2020202020200032
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "DEL", prod id 16422


```

---

### Post by ethan.close on 2010-06-21
I fixed a similar issue by installing the latest kernel build of 2.6.33.  Aparently, there are a lot of graphics driver fixes in that.

---

