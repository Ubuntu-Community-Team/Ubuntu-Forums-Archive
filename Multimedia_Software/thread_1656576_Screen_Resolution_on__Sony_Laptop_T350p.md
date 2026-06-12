---
title: "Screen Resolution on  Sony Laptop T350p"
date: 2010-12-31
forum: Multimedia Software
---

### Post by ebiz98 on 2010-12-31
A couple of days ago I installed UBUNTU 10.04 LTS on a Sony VGN-T350P laptop.   Worked out of the box very nicely, except that I can not get it to use the full 1280x768 screen resolution.   
Te maximum resolution it gives is 1024x768 which leaves 1-inch black borders to each side of the screen...  

I have tried to follow threads from back in 2005 (broken links etc)  where pointers are give, but unfortunately I've had no luck resolving the issue.

any help would be most appreciated!
Thanks!
J

hwinfo --framebuffer command  reports: 

2: None 00.0: 11001 VESA Framebuffer                      	 
  [Created at bios.464]
  Unique ID: rdCR.xnRagj3_2BF
  Hardware Class: framebuffer
  Model: "Intel(r)852GM/852GME/855GM/855GME Graphics Controller"
  Vendor: "Intel Corporation"
  Device: "Intel(r)852GM/852GME/855GM/855GME Graphics Controller"
  SubVendor: "Intel(r)852GM/852GME/855GM/855GME Graphics Chip Accelerated VGA BIOS"
  SubDevice:
  Revision: "Hardware Version 0.0"
  Memory Size: 7 MB + 832 kB
  Memory Range: 0xe8000000-0xe87cffff (rw)
  Mode 0x037c: 1024x600 (+1024), 8 bits
  Mode 0x037d: 1024x600 (+2048), 16 bits
  Mode 0x037e: 1024x600 (+4096), 24 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown

I have also modifed the xorg.conf  to include  a Modeline 1280x768...  line  

Section "Device"
    Identifier    "Configured Video Device"
    Driver   	 "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    	HorizSync	20 - 90
    	VertRefresh  50 - 100
    	DisplaySize 230 138
    	Modeline "1280x768" 80.14 1280 1344 1480 1680 768 769 772 795
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor   	 "Configured Monitor"
    Device   	 "Configured Video Device"
EndSection

---

### Post by cyb3r_sn4k3 on 2010-12-31
Are the drivers installed?

---

### Post by realzippy on 2010-12-31
Where did you get your xorg.conf from ?!

Can you post your /var/log/Xorg.0.log file ?

And welcome to Ubuntuforums!

---

### Post by ebiz98 on 2010-12-31
@cyb3r_sn4k3:  I believe so... How do I check the drives are installed?

@realzippy:  /etc/X11/xorg.conf 
    and the requested file is attached. xorg.0.log (saved as zip file)

Thank you both for prompt responses and help!

---

### Post by ebiz98 on 2011-01-10
anything - anyone? 
Thanks!

---

### Post by realzippy on 2011-01-10
Where did you get your xorg.conf from ?!
(..and why the "vesa" driver ?!)

...what is the output from:
```
xrandr
```

---

### Post by TG12 on 2011-01-11
[http://ubuntuforums.org/showthread.php?t=1664919](http://ubuntuforums.org/showthread.php?t=1664919)

Try that I posted there!

---

### Post by BicyclerBoy on 2011-01-11
But his hardware shows intel 855 graphis controller.

In the /etc/X11/xorg.conf..

try changing vesa to intel.

You don't need a modeline entry, the built in EDID & driver video modes should be fine.

This will then use intel driver for X server & not the free vesa one.

The intel driver will allow 2d & 3d ? acceleration & should allow the intel chipset to work better.

---

