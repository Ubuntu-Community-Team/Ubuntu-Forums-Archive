---
title: "[SOLVED] No Video on External Monitor on VGA"
date: 2008-11-27
forum: Multimedia Software
---

### Post by r6dude on 2008-11-27
Hello

I have installed 8.10 on my Acer Laptop AS5102WLMi which has an internal ATI Radeon® Xpress 1100 integrated 3D graphics card.  **Everything works great however when I play video, it play fine on my laptop screen but I don't see the video on my external monitor attached to the VGA port**.  I can play a flash video and see it on the external VGA monitor but not anything else.

This is what I have in my xorg.conf
```
Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

Some out from my xorg.log file
```
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "DMI", prod id 0
(II) RADEON(0): DDCModeFromDetailedTiming: Ignoring tiny 0x1100 mode
(II) RADEON(0): DDCModeFromDetailedTiming: Ignoring tiny 0x617 mode
(II) RADEON(0): DDCModeFromDetailedTiming: Ignoring tiny 0x522 mode
(II) RADEON(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
(II) RADEON(0): EDID vendor "AUO", prod id 8564
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: AUO  Model: 2174  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 1
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.590 redY: 0.345   greenX: 0.315 greenY: 0.555
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  AUO
(II) RADEON(0):  B154EW02 V1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006af742100000000
(II) RADEON(0): 	010f0103802115780a1cf59758508e27
(II) RADEON(0): 	27505400000001010101010101010101
(II) RADEON(0): 	010101010101c71b00a0502017303020
(II) RADEON(0): 	36004bcf100000180000000f00000000
(II) RADEON(0): 	00000000000000000020000000fe0041
(II) RADEON(0): 	554f0a202020202020202020000000fe
(II) RADEON(0): 	004231353445573032205631200a00aa
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "AUO", prod id 8564
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) Quirked EDID physical size to 0x0 cm
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: DMI  Model: 0  Serial#: 66
(II) RADEON(0): Year: 2004  Week: 17
(II) RADEON(0): EDID Version: 1.0
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Signal levels configurable
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Indeterminate output size
(II) RADEON(0): Gamma: 2.56
(II) RADEON(0): DPMS capabilities: StandBy; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.000 redY: 0.000   greenX: 0.000 greenY: 0.000
(II) RADEON(0): blueX: 0.000 blueY: 0.000   whiteX: 0.000 whiteY: 0.000
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 720x400@88Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@87Hz (interlaced)
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 78
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): #1: hsize: 1280  vsize 720  refresh: 60  vid: 49281
(II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  4 x 3 mm
(II) RADEON(0): h_active: 1280  h_sync: 1528  h_sync_end 1640 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1062  v_sync_end 1065 v_blanking: 1066 v_border: 0
(II) RADEON(0): Stereo: left channel on sync
side-by-side interleaved(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0011a9000042000000
(II) RADEON(0): 	110e01001804039c8e00000000000000
(II) RADEON(0): 	000000fffff881c081c0818000000000
(II) RADEON(0): 	000000000000000000fc004c4344204d
(II) RADEON(0): 	756c74692d4d6564000000fc00696120
(II) RADEON(0): 	446973706c6179202020000000fc000a
(II) RADEON(0): 	202020202020202020202020302a0098
(II) RADEON(0): 	51002a40f8706308040300000078004a
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "DMI", prod id 0
(II) RADEON(0): DDCModeFromDetailedTiming: Ignoring tiny 0x1100 mode
(II) RADEON(0): DDCModeFromDetailedTiming: Ignoring tiny 0x617 mode
(II) RADEON(0): DDCModeFromDetailedTiming: Ignoring tiny 0x522 mode
(II) RADEON(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
(II) RADEON(0): EDID vendor "AUO", prod id 8564
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: AUO  Model: 2174  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 1
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.590 redY: 0.345   greenX: 0.315 greenY: 0.555
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  AUO
(II) RADEON(0):  B154EW02 V1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0006af742100000000
(II) RADEON(0): 	010f0103802115780a1cf59758508e27
(II) RADEON(0): 	27505400000001010101010101010101
(II) RADEON(0): 	010101010101c71b00a0502017303020
(II) RADEON(0): 	36004bcf100000180000000f00000000
(II) RADEON(0): 	00000000000000000020000000fe0041
(II) RADEON(0): 	554f0a202020202020202020000000fe
(II) RADEON(0): 	004231353445573032205631200a00aa
in RADEONProbeOutputModes
```


Any Help Please?

---

### Post by r6dude on 2008-11-27
When I said "Not Anything Else" I mean no other video.  The external display is fine for normal desktop, browsing etc.  Just the videos I don't see.  I see a black screen when the video supposed to be.

Thanks

---

### Post by Coreigh on 2008-11-27
I was too slow and didn't see your update before I wrote the below:


On many laptops you have to enable the external video device with a function key on the keyboard. Have to covered that yet? Do you get output to external but not your movie, or no output at all?

I don't have it in front of me but my Dell D510 the keys are something like:
Fn+F6

The Fn key is the blue one on the bottom row near the "Windows" or Super key, and the F button has a picture of a screen on it. It works like a toggle. Internal display, External display or Both.

---

### Post by r6dude on 2008-11-27
This is solved folks.  I installed the recommended ATI driver by ubuntu and changed the right resolution to what my monitor can support and it rocks.

Ubutu rocks..

---

