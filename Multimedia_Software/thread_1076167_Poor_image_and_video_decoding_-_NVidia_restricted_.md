---
title: "Poor image and video decoding - NVidia restricted drivers"
date: 2009-02-21
forum: Multimedia Software
---

### Post by GrooveTherapy on 2009-02-21
Hey all

I've been having this issue with all image and video playback.  The images are of significantly less quality in ubuntu when I compare it to vista.  Essentially, it looks like I'm on 16bit color mode.  It's only noticeable on parts of an image that have small variation in the color.  I've compared images from the same source on my ubuntu setup (using nvidias restricted 177 driver and 180 driver - both giving me similar results) with an XP system, the latter being much clearer.  

Here's the relevant sections of my xorg.conf

```



Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
	Option 		"RandRRotation" "On"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Nvidia Default Flat Panel"
    HorizSync       29.0 - 49.0
    VertRefresh     0.0 - 61.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 6150"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

I've included a screenshot, although I'm not sure if you will see what I am seeing.  See this link for comparison: [http://www.antirobotic.net/images/IronMan%201280x800%202.jpg](http://www.antirobotic.net/images/IronMan%201280x800%202.jpg)

Any ideas?

---

### Post by GrooveTherapy on 2009-02-21
I just switched back to the 180 driver and I realize it's even worse than the 177.  Why is it doing this?

Btw, I'm on 32bit intrepid

---

### Post by GrooveTherapy on 2009-02-22
Bump

I've been lurking at the NVidia linux support forum and I found this thread: [http://www.nvnews.net/vbulletin/showthread.php?t=124258&highlight=image](http://www.nvnews.net/vbulletin/showthread.php?t=124258&highlight=image)
The issue I'm having is colour banding as well.  It even happens for me on the 177.82 driver, although it isn't as bad as 180.11.  I've tried resetting colour correction defaults to no avail.  Upping the brightness slightly seems to help on some images, but colour banding is still there.  I can open the same images in vista, and they look flawless :(

Anti aliasing doesn't work either, even when I enable it from nvidia-settings.  As a result, window wobble looks gross.  

Has no one else had these issues?

---

### Post by Rackstar on 2009-03-26
I have the same problem. Did not had it with old 177 driver, but this one was buggy with compiz. 

Driver: 180.35
Nvidia geforce go 7300
Ubuntu 8.10

Did you find any answers?

Thanks!

---

