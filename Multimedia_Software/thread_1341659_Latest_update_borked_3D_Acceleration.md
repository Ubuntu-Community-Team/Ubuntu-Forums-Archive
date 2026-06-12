---
title: "Latest update borked 3D Acceleration"
date: 2009-11-29
forum: Multimedia Software
---

### Post by cKGunslinger on 2009-11-29
So, before I left for Thanksgiving holiday (last Wednesday) I noticed that my update manager wanted to grab some files, so I let it.  Instead of rebooting, I simply Powered-Off since I was leaving for the week.

I come back and boot-up this evening only to get the common "*flashing black console screen with intermittent input*" thing I encountered when I updated to Karmic last month.  I assumed I got a new nVidia driver or a new kernel or some such.

I blew away my xorg.conf and got back into Gnome with no problem.  I then rebuilt my xorg.conf with nvidia-xconfig and nvidia-settings and rebooted.  

Everything seemed good:

Dual monitors working?  Yes
nVidia proprietary driver in use?  Yes (185)
3D acceleration?  Nope.

jockey-text -l
```
xorg:nvidia-185 - NVIDIA accelerated graphics driver (Proprietary, Enabled, In use)
```

glxinfo:
```
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
```

compiz-check:
```
Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation G92 [GeForce 9800 GT] (rev a2)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size 
```

When I look at the OpenGl/GLX page in my nvidia-setting app, I get:
```
Fail to query the GLX server vendor.
```

So, I completely removed all nvidia drivers, rebooted, started up with vesa.  Used EnvyNG to get the recommended nVidia 185 drivers, rebooted.  Same thing.

Why can't my system find a "GLX extension?"  Do I have some mismatched drivers/kernel headers or something?  Is this a DKMS or whatever issue?  (I admit, I don't know much about that.)

Is there some missing link I can't find?

xorg.conf:
```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Option         "Xinerama" "0"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Compaq"
    HorizSync       31.5 - 53.7
    VertRefresh     56.0 - 85.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9800 GT"
EndSection

Section "Screen"
    Option         "NoLogo" "True"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "CRT: 1024x768 +1920+0, DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by rockdj on 2009-11-30
Pretty much the same thing here, except my gfx chip is "nVidia Corporation G84 [GeForce 8600M GT] (rev a1)" but all the output you've got there from compiz-check is exactly the same.  Hopefully someone's got idea how to fix things.

---

### Post by tripolitan on 2009-11-30
Should there be a zero in between screen and "screen0" 0 0 ? or is  it a typo?

Screen      0  "Screen0" 0 0

---

### Post by PariahVayne on 2009-11-30
x

---

