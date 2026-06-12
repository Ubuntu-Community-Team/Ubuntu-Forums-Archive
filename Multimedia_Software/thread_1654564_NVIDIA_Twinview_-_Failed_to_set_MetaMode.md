---
title: "NVIDIA Twinview - Failed to set MetaMode"
date: 2010-12-28
forum: Multimedia Software
---

### Post by thepossiblehuman on 2010-12-28
Hi all,

I'm trying to get TwinView working with 10.10.  It's been a while since needing to mess with these NVIDIA drivers for me, and I'm having no luck.  When I try to set Twinview, I get this exact error:

```


Failed to set MetaMode (2) 'DFP-0: 1680x1050 @1680x1050 +0+0, DFP-1: 1280x1024 @1280x1024 +1680+0' (Mode 2960x1050, id: 50) on X screen 0

Would you like to remove this MetaMode?


```

This seems vaguely familiar to me from messing around with getting dual monitors and Compiz working in previous versions with other NVIDIA cards.  I think I ended up doing something manually in xorg with resolution or depth, but I just can't remember unfortunately.  Does anybody have any tips?  Below is my xorg.conf file.


```


    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "DELL 1907FP"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 135M"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 135M"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"

# Removed Option "TwinView" "0"
# Removed Option "metamodes" "DFP-0: nvidia-auto-select +0+0"
# Removed Option "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +1680+0"
# Removed Option "metamodes" "DFP-0: 1680x1050 +0+0, DFP-1: 1280x1024 +1680+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP-0: 1680x1050 +0+0, DFP-1: 1280x1024 +1680+0; DFP-0: 1680x1050 +0+0, DFP-1: nvidia-auto-select +1680+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by thepossiblehuman on 2010-12-28
I solved it 5 minutes after posting of course.

It was a permissions problem.  For whatever case, the nvidia settings app does not launch as root.  I had to go command line and launch the app using sudo, and I was able to save everything without issue.

---

### Post by realzippy on 2010-12-28
Edit.

So solved;but normally nvidia-settings should ask for password when "saving to xorg configuration file" ,no need for sudo.

---

