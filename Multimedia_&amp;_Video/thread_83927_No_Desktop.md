---
title: "No Desktop"
date: 2005-10-29
forum: Multimedia &amp; Video
---

### Post by sentaku on 2005-10-29
After the boot screen there is a small white underscrore line that blinks a few times and then stops.  I can switch to promps usining crtl+alt+f2 

my xorg.conf file for the monitor section:
Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Driver Section:

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 7000 VE (RV100 QY)"
	Driver		"ati"
	BusID		"PCI:0:11:0"
EndSection

My monitor specs:
Resolutions supported
1024 x 768 ? 1280 x 1024 ? 640 x 480 ? 800 x 600 ? 1152 x 864
Synchronization Range - Vertical 
50 - 160 Hz
Synchronization Range - Horizontal 
30 - 70 kHz
Native (Recommended) Resolution
1024 x 768

my X.0.log file contains these errors repeaded for any aray of screen sizes.
RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)

---

### Post by sentaku on 2005-10-30
well I figured the problem was that I X is using my other video card and not my main one.

---

