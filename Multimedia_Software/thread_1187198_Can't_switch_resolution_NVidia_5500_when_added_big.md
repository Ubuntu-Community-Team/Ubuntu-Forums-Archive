---
title: "Can't switch resolution NVidia 5500 when added bigger monitor"
date: 2009-06-14
forum: Multimedia Software
---

### Post by cojoco on 2009-06-14
I recently installed Jaunty and the proprietary NVidia drivers, and it worked fine.

When I switched to a bigger monitor, nvidia-settings would refuse to see the higher resolution.  It gets the monitor name OK, but does not show a larger maximum resolution.

The original monitor was 1440x1050; my new one is 1920x1080.  The highest resolution shown is stuck at 1440x1050.

I tried changing my xorg.conf, but it didn't do much at all: here are some relevant lines:

Section "Monitor"
        Identifier     "Monitor0"
        VendorName     "Unknown"
        ModelName      "Acer V233H"
        Modeline "1920x1080_60"  172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync
        # HorizSync       30.0 - 94.0
        # VertRefresh     49.0 - 75.0
EndSection

...

Section "Screen"
        Identifier     "Screen0"
        Device         "Device0"
        Monitor        "Monitor0"
        Option         "TwinView" "0"
        # Option                "UseEdid" "False"
        DefaultDepth    24
        SubSection "Display"
                Modes "1920x1080_60"
                Depth       24
        EndSubSection
EndSection

Please help!

---

### Post by gradinaruvasile on 2009-06-14
Try typing 
sudo nvidia-settings

in a terminal

Press "detect displays"
If successful, press apply then "save to x configuration file"
Tick "
merge

If this is not working, delete the xorg.conf, and run
sudo nvidia-xconfig
reboot

---

