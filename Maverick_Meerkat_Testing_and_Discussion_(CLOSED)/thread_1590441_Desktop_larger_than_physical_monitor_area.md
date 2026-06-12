---
title: "Desktop larger than physical monitor area"
date: 2010-10-07
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Yumi on 2010-10-07
Thursdays update brought back an older problem. My monitor (viewsonic 1080p) and the graphics card (nvidia Gforce 6100) support a resolution of 1920x1080. This worked fine until Thursday.

Now the desktop is larger then the monitor area, some icons and menus are to the left and can not be seen or accessed. 

The xorg.conf seems ok, nothing has changes since.
> Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ViewSonic VX2250 SERIES"
    HorizSync       24.0 - 82.0
    VertRefresh     50.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6100"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1920x1080_60_0 +0+0; nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


System - Administration - Additional drivers shows the nvidia 260 beeing activated but it says it is not in use.

Deactivating the nvidia driver and removing the xorg.conf results in a boot at very low resolution and the monitor is not detected.

Michael

---

### Post by ronacc on 2010-10-07
what does nvidia-settings say about the driver ?

---

### Post by Yumi on 2010-10-08
Says:
NVIDIA Driver Version: 260.19.06

---

### Post by Yumi on 2010-10-08
It is back to normal. Had to set the resolution in nvidia x-server settings to "auto" instead of the wanted resolution of 1920x1989. Wonder why.

Michael

---

### Post by spegru on 2010-10-08
hi I have a related problem

I just got a new monitor with resolution 1920x1080, 60Hz but the highest resolution I can find for it under the nvidia settings is only 1024x768.
How can I create new resolution for that?
My driver appears to be 195.36.24. Is that the reason? (How did you get a newer one?)

---

### Post by auxbuss on 2010-10-08
> I just got a new monitor with resolution 1920x1080, 60Hz but the highest 
> resolution I can find for it under the nvidia settings is only 1024x768.
> How can I create new resolution for that?

Check contents of /etc/X11/xorg.conf

Attaching its contents here would help.

> My driver appears to be 195.36.24. Is that the reason? (How did you get 
> a newer one?)

It's the current Nvidia driver for 10.10 Maverick. You are on Lucid. It's a beta driver anyway, and it doesn't work on my machine, so I wouldn't wish for it :-/

---

### Post by spegru on 2010-10-08
here is my xorg.conf. As you can see is is very sparse, but as I mentioned, I am a little surprised there is an xorg.conf at all


Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

What version of the driver does maverick have and does it work at 1920x1080 resolution?

---

### Post by cariboo on 2010-10-08
You may need to run **nvidia-xconfig** to get the correct resolution, if your monitor is not detected properly. Nvidia-xconfig creates a new /etc/X11/xorg.conf file.

I run an older KVM switch, the crt is never detected properly, so i have to run the command, then manually adjust the horizontal and vertical frequencies.

---

### Post by spegru on 2010-10-08
Unfort I tried that and it made no difference.
 Realy the only problem I have is a missing set of resoutions for the nvidia settings - 1920x1080
I could do it manually I guess, but I've had problems with that in the past, and now I cant even remember how....

---

### Post by Yumi on 2010-10-08
Here is my working xorg.conf file. Maybe it is of use.

> Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ViewSonic VX2250 SERIES"
    HorizSync       24.0 - 82.0
    VertRefresh     50.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6100"
EndSection

Section "Screen"

# Removed Option "metamodes" "1920x1080_60_0 +0+0; nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "nvidia-auto-select +0+0; 1920x1080_60_0 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


---

### Post by solitaire on 2010-10-09
This happens on my 1080p screen when I use HDMI
there's a slider in the nVidia control panel (somewhere on the last option) that you can use to change the zoom

I have to start and then stop the Nvidia control panel for the zoom to be corrected so I can see the whole screen...

(i'll have to boot my Nvidia box to find the exact settings but not close to it at the moment...)
NOTE this never happens when I use VGA just HDMI

---

