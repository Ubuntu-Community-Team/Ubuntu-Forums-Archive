---
title: "nVidia dual monitors on 8.10"
date: 2008-11-02
forum: Multimedia Software
---

### Post by gaz514 on 2008-11-02
Hey people,

Just upgraded to 8.10. My dual monitor setup worked perfectly on 7.10 and 8.04, not to mention Gentoo (which is what I used before Ubuntu), but I can't get it to work on Intrepid.

The relevant parts of my setup are:

AMD64 chip, running 64 bit Ubuntu
nVidia GeForce 6200 TurboCache graphics card
NEC flat panel (LCD1770NX) plugged into DVI port of graphics card
VideoSeven flat panel plugged into VGA port of graphics card

Both flat panels are 17", max resolution 1280x1024. Fairly standard setup really.

My xorg.conf:

```

Section "Module"
	Load           "glx"
EndSection

Section "Monitor"
	Identifier     "Monitor0"
EndSection

Section "Device"
	Identifier     "Device0"
	VendorName     "NVIDIA Corporation"
	BoardName      "GeForce 6200 TurboCache(TM)"
	Driver         "nvidia"
	Option         "NoLogo"	"1"
	Option         "TwinView" "1"
	Option         "MetaModes" "DFP-0: 1280x1024, CRT-0: 1280x1024; DFP-0: 1280x1024, CRT-0: NULL;"
	Option         "TwinViewOrientation" "DFP-0 LeftOf CRT-0"
	Option         "TwinViewXineramaInfoOrder" "DFP-0"
	Option         "HorizSync" "DFP-0: 31.5-69; CRT-0: 31.5-79"
	Option         "VertRefresh" "DFP-0: 50-76; CRT-0: 55-75"
	Option         "RenderAccel" "true"
EndSection

Section "Screen"
	Identifier     "Screen0"
	Device         "Device0"
	Monitor        "Monitor0"
	DefaultDepth	24
EndSection

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "Screen0" 0 0
EndSection

```

I looked for warnings in the Xorg startup log:

```

root@mullen:~# grep "^(W" /var/log/Xorg.0.log
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) NVIDIA(0): Unable to parse range in HorizSync string "DFP-0:31.5-69";
(WW) NVIDIA(0):     ignoring
(WW) NVIDIA(0): Unable to parse range in HorizSync string "CRT-0:31.5-79";
(WW) NVIDIA(0):     ignoring
(WW) NVIDIA(0): Unable to parse range in VertRefresh string "DFP-0:50-76";
(WW) NVIDIA(0):     ignoring
(WW) NVIDIA(0): Unable to parse range in VertRefresh string "CRT-0:55-75";
(WW) NVIDIA(0):     ignoring
(WW) NVIDIA(GPU-0): The EDID read for display device CRT-0 is invalid:
(WW) NVIDIA(GPU-0):     unrecognized EDID Header.
(WW) NVIDIA(0): Unable to find all display devices requested in TwinView
(WW) NVIDIA(0):     Orientation string "DFP-0 LeftOf CRT-0".
(WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from CRT-0's EDID.

```

Firstly it's having trouble with the HorizSync and VertRefresh strings, although according to the [nVidia documentation](ftp://download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/appendix-g.html) these strings are perfectly valid.

Secondly, there's a problem with the EDID header (this is the same thing as DDC right?), and that seems to be preventing CRT-0 from being used. At least that's my interpretation of Xorg's messages.

I even got desperate and tried to sort it out using the graphical tool, nvidia-settings. Using that, I was able to get both monitors working, but was unable to select the 1280x1024 resolution for CRT-0; it wouldn't let me choose anything higher than 1360x768.

I'm pretty much stumped. Seems like an issue with the latest version of the nVidia drivers. Any ideas?

---

### Post by gaz514 on 2008-11-05
Fixed it...

I recently enabled the intrepid-proposed repository in order to fix another ridiculous 8.10 bug - joysticks not working.

From this repository I just installed nvidia-glx-96, and it works perfectly (the other versions available, 173 and 177, don't work).

In the few days I've been running Intrepid, I've already had this problem, the joystick issue I mentioned, and all sorts of trouble with the new NetworkManager. I also use Ubuntu Studio, and I'm told that the rt kernel for it doesn't support SMP, which is insane since I'd imagine that most modern multimedia production computers have some sort of multi-core processor. Overall I wouldn't recommend this upgrade to anybody; stick with 8.04 until all the problems are ironed out.

---

### Post by yusufk on 2008-11-06
Hi, 

what is the difference between nvidia-177 and nvidia-96 etc.?

Regards,
Yusuf

---

