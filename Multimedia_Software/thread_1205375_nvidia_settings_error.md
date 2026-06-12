---
title: "nvidia settings error"
date: 2009-07-05
forum: Multimedia Software
---

### Post by bluedalek on 2009-07-05
Hey all

I launch the nvidia settings manager like so:

```
sudo nvidia-settings
``` 

Then, when I try and save the settings, I get the following error:

> PARSE ERROR:  Parse error on line 34 of section Module in file /etc/X11/xorg.conf.
"Disable" is not a valid keyword in this section.

Segmentation fault


Any thoughts or suggestions?

Many thanks in advance!

---

### Post by x33a on 2009-07-06
post the output of
```
cat /etc/X11/xorg.conf
```

---

### Post by bluedalek on 2009-07-06
Your wish is my command...

> Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
	Disable	"dri2"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
EndSection


the settings manager detects my display correctly (LG TV) and the correct refresh rates and resolutions, but defaults to 800x600.  It's only when attempting to save the settings as 1360x768 (or anything else) I get the error.

Thanks again in advance!

---

### Post by merlinus on 2009-07-06
Edit xorg.conf and delete the line in red:

Section "Module"
    Load    "glx"
    [COLOR=Red]Disable    "dri2"[/COLOR]
EndSection

Then try gksudo nvidia-settings.

---

### Post by bluedalek on 2009-07-06
Awesome!  Problem solved, many thanks once again..  my xorg actually looks like a configuration file now.. 

Now, all I need to do is get my sound to work.  What a pain!

Thanks again!


> 
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LG TV"
    HorizSync       31.0 - 60.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1360x768 +0+0; nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


---

