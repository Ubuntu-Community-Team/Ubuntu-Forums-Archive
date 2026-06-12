---
title: "Screen resolution..."
date: 2006-12-20
forum: Multimedia &amp; Video
---

### Post by infinotize on 2006-12-20
Well, I've hit the screen resolution bug everyone seems to get. I'm running a 2001FP (1600x1200 @ 60 is what I would like) and have nvidia drivers installed.  I upped the default HorizSync value to 60 initially in xorg.conf and everything worked great.

However, my desktop crashed yesterday and I had to do a hard reset on the machine.  When I logged back on, back to 1024x768 again.  Reseting/rechanging my .conf has not helped.  I've went and tried adding 

# V-freq: 60.00 Hz  // h-freq: 74.69 KHz
Modeline "1600x1200" 170.89  1600 1688 1896 2288  1200 1200 1203 1244

and it did not help.  I'm using monitor specs from here: [http://support.dell.com/support/edocs/monitors/2001fp/EN/specs.htm](http://support.dell.com/support/edocs/monitors/2001fp/EN/specs.htm)

I've been playing with the .conf a LOT in hopes that something would work, but nothing yet. Here's the current monitor sections:

```

Section "Device"
	Identifier	"NVIDIA Corporation NV18GL [Quadro4 NVS AGP 8x]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	31-80
	VertRefresh	56-76
	# V-freq: 60.00 Hz  // h-freq: 74.69 KHz
	Modeline "1600x1200_60.00" 170.89  1600 1688 1896 2288  1200 1200 1203 1244
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV18GL [Quadro4 NVS AGP 8x]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```

Yes, I've also tried adding "1600x1200" in all of those, "1600x1200_60", etc. Nothing has worked. 1024x768 on this monitor blows. Help :neutral:

Also: here is output from my log, grep'ed for EE and WW:
```

(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(II) Loading extension MIT-SCREEN-SAVER
(WW) NV(0): config file hsync range 28-51kHz not within DDC hsync ranges.
(WW) NV(0): config file vrefresh range 43-60Hz not within DDC vrefresh ranges.
(WW) (1600x1200,Generic Monitor) mode clock 162MHz exceeds DDC maximum 160MHz
(WW) (1600x1200,Generic Monitor) mode clock 175.5MHz exceeds DDC maximum 160MHz
(WW) (1600x1200,Generic Monitor) mode clock 189MHz exceeds DDC maximum 160MHz
(WW) (1600x1200,Generic Monitor) mode clock 202.5MHz exceeds DDC maximum 160MHz
(WW) (1600x1200,Generic Monitor) mode clock 229.5MHz exceeds DDC maximum 160MHz
(WW) (1792x1344,Generic Monitor) mode clock 204.8MHz exceeds DDC maximum 160MHz
(WW) (1792x1344,Generic Monitor) mode clock 261MHz exceeds DDC maximum 160MHz
(WW) (1856x1392,Generic Monitor) mode clock 218.3MHz exceeds DDC maximum 160MHz
(WW) (1856x1392,Generic Monitor) mode clock 288MHz exceeds DDC maximum 160MHz
(WW) (1920x1440,Generic Monitor) mode clock 234MHz exceeds DDC maximum 160MHz
(WW) (1920x1440,Generic Monitor) mode clock 297MHz exceeds DDC maximum 160MHz
(WW) (1400x1050,Generic Monitor) mode clock 184MHz exceeds DDC maximum 160MHz
(WW) (1680x1050,Generic Monitor) mode clock 214.51MHz exceeds DDC maximum 160MHz(WW) (1920x1200,Generic Monitor) mode clock 193.16MHz exceeds DDC maximum 160MHz(WW) (1920x1200,Generic Monitor) mode clock 230MHz exceeds DDC maximum 160MHz
(WW) (1920x1440,Generic Monitor) mode clock 341.35MHz exceeds DDC maximum 160MHz(WW) (960x720,Generic Monitor) mode clock 170.675MHz exceeds DDC maximum 160MHz
(WW) (2048x1536,Generic Monitor) mode clock 266.95MHz exceeds DDC maximum 160MHz(WW) (2048x1536,Generic Monitor) mode clock 340.48MHz exceeds DDC maximum 160MHz(WW) (1024x768,Generic Monitor) mode clock 170.24MHz exceeds DDC maximum 160MHz
(WW) (1024x768,Generic Monitor) mode clock 194.02MHz exceeds DDC maximum 160MHz
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom

Other interesting things from this file:

(II) NV(0): Supported VESA Video Modes:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported Future Video Modes:
(II) NV(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #1: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) NV(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 162.0 MHz   Image Size:  367 x 275 mm
(II) NV(0): h_active: 1600  h_sync: 1664  h_sync_end 1856 h_blank_end 2160 h_border: 0
(II) NV(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1250 v_border: 0
(II) NV(0): Serial No: C064654E4Y6L
(II) NV(0): Monitor name: DELL 2001FP
(II) NV(0): Ranges: V min: 56  V max: 76 Hz, H min: 31  H max: 80 kHz, PixClock max 160 MHz

```

I don't really know what that rubbish means...

---

### Post by infinotize on 2006-12-20
Well, after another reboot, it works!  I also changed my fonts to something smaller than default, which my coworker insists is the solution, since she had the same problem and changing that worked for her without touching any config files.  Who knows!  At least this thread can be a reference for anyone else with problems.

---

### Post by subject117 on 2007-01-12
I have the same monitor as the guy above but making my xorg.conf file like his didn't work for me.  Eventually I found this:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

And installed the nvidia drivers, then magically everything worked.  Now I am doing a dance because my monitor resolution if finally correct!

---

