---
title: "No widescreen with nvidia board"
date: 2011-03-15
forum: Multimedia Software
---

### Post by dinobottm2 on 2011-03-15
I just got an LG widescreen monitor, but i just cant set it to use a widescreen definition. It still has my old CRT monitor as the default and it does not recognize the new one Im using the nvidia card and its own settings driver.

---

### Post by BicyclerBoy on 2011-03-15
Try editing/deleting the 
/etc/X11/xorg.conf file
make a backup copy first..

Reboot/restart X server..

This file is no longer a necessity & the existing contents may be the cause of your problem. The contents may be setting a fixed resolution & ignoring the new EDID.

You can use the nvidia-settings GUI tool to generate a new one..

Are you using HDMI/DVI-D connection ?

---

### Post by dinobottm2 on 2011-03-16
No, im still using a VGA cable, but my windows system is configured for widescreen without any issue.  I tried to delete the file as you reccomended, but now my ubuntu isnt even turning on anymore.

---

### Post by johntaylor1887 on 2011-03-16
Did you back up your xorg.conf file?

---

### Post by dinobottm2 on 2011-03-16
> **johntaylor1887 said:**
> Did you back up your xorg.conf file?

Yes, i did.  In fact, i managed to sudo cp the backup file to its original spot already. But i still cant set it to widescreen.  P.S.: sorry for my bad spelling, english is not my first language.

---

### Post by BicyclerBoy on 2011-03-16
If you want..attach your 
/etc/X11/xorg.conf
&
/var/log/Xorg.0.log
files..

The attachments have to have windows file name (n.3) extensions.
(Don't tell anyone but the Ubuntu Forums run on a windows server)

---

### Post by dinobottm2 on 2011-03-16
Uploaded both as text files, thanks for the help.

---

### Post by johntaylor1887 on 2011-03-16
Run:
```
sudo nvidia-xconfig
```
reboot, then run:
```
sudo nvidia-settings
```

---

### Post by dinobottm2 on 2011-03-16
> **johntaylor1887 said:**
> Run:
```
sudo nvidia-xconfig
```reboot, then run:
```
sudo nvidia-settings
```

Didnt help. Same problem still. When i rebooted, it went straight to 640 and no better configuration shower up.

---

### Post by BicyclerBoy on 2011-03-17
> 
(WW) Mar 16 13:58:54 NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
(II) Mar 16 13:58:55 NVIDIA(0): Validated modes:
(II) Mar 16 13:58:55 NVIDIA(0):     "nvidia-auto-select"
(II) Mar 16 13:58:55 NVIDIA(0): Virtual screen size determined to be 1024 x 768
(WW) Mar 16 13:58:55 NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) Mar 16 13:58:55 NVIDIA(0):     from CRT-0's EDID.


This is problem (not the root cause).
You need to put some info into the xorg.conf file to allow mode validation of display against a chosen mode from the internal modes..

What is the model of display ?
What resolution do you what to use ?

---

### Post by dinobottm2 on 2011-03-17
> **BicyclerBoy said:**
> This is problem (not the root cause).
You need to put some info into the xorg.conf file to allow mode validation of display against a chosen mode from the internal modes..

What is the model of display ?
What resolution do you what to use ?

My screen is an 22" 22lg30r, and im looking for the 1280X720 HDTV definition. Thanks.

---

### Post by BicyclerBoy on 2011-03-17
I would recommend the native resolution only.. let the video card do all scaling.
The LG engine is not very good..

PC-VGA cable your display only supports 60Hz modes (good for US)

native is  1680x1050
All possible modes covered by
hortz freq range 31 - 67 KHz
vertical freq range 59 - 61 Hz
GTF timing supported.
# 1680x1050 59.95 Hz (CVT 1.76MA) hsync: 65.29 kHz; pclk: 146.25 MHz
Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync

add/edit to xorg.conf
[PHP]Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "LG"
    ModelName      "22LG30R"
    HorizSync       30.0 - 70.0
    VertRefresh     58.0 - 62.0
    Option         "DPMS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "ModeValidation" "AllowInterlacedModes"
    Option         "UseEDID" "FALSE"
    Option         "UseDisplayDevice" "CRT-0"
    SubSection     "Display"
        Depth       24
#        Option     "PreferredMode" "1920x1080i60"
    EndSubSection
EndSection
[/PHP]You need figure out the screen & device number [0, 1] that correspond to the wired port CRT-0.
The driver will generate an allowed list of modes from all the internal modes that can be validated against the monitor section.

---

### Post by dinobottm2 on 2011-03-17
> **BicyclerBoy said:**
> I would recommend the native resolution only.. let the video card do all scaling.
The LG engine is not very good..

PC-VGA cable your display only supports 60Hz modes (good for US)

native is  1680x1050
All possible modes covered by
hortz freq range 31 - 67 KHz
vertical freq range 59 - 61 Hz
GTF timing supported.
# 1680x1050 59.95 Hz (CVT 1.76MA) hsync: 65.29 kHz; pclk: 146.25 MHz
Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync

add/edit to xorg.conf
[PHP]Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "LG"
    ModelName      "22LG30R"
    HorizSync       30.0 - 70.0
    VertRefresh     58.0 - 62.0
    Option         "DPMS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "ModeValidation" "AllowInterlacedModes"
    Option         "UseEDID" "FALSE"
    Option         "UseDisplayDevice" "CRT-0"
    SubSection     "Display"
        Depth       24
#        Option     "PreferredMode" "1920x1080i60"
    EndSubSection
EndSection
[/PHP]You need figure out the screen & device number [0, 1] that correspond to the wired port CRT-0.
The driver will generate an allowed list of modes from all the internal modes that can be validated against the monitor section.

That worked. Thanks.

---

### Post by BicyclerBoy on 2011-03-19
That's good to hear..

---

