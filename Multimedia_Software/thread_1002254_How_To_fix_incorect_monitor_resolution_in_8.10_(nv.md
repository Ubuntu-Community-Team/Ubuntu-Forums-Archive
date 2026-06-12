---
title: "How To fix incorect monitor resolution in 8.10 (nvidia-settings)"
date: 2008-12-04
forum: Multimedia Software
---

### Post by Jive Turkey on 2008-12-04
In Ubuntu 8.10 and probably the other *buntus the restricted nvidia v177 & 173 driver fails to correctly detect and configure the appropriate resolution for many monitors.  Neither Ubuntu or Nvidia softwares do a very good job of exposing these settings to the user to get it working correctly.  Yes, you must edit the xorg.conf
In searching for a solution I found many unanswered threads on the same problem so I wanted to post my solution.

After installing the restricted driver for my nvidia card, my secondary monitor could only be set to 1024x768 with some inapropriate widescreen options above that and only 60Hz refresh which causes serious problems on this old beast of a CRT I have.  I've never had any luck with ubuntu's screen resolution manager under "System>Preferences>Screen Resolution" when using multiple monitors. I suggest avoiding that even though it doesn't seem to hose X like it used to.

[SIZE="6"][COLOR="DarkOrange"]Solution[/COLOR][/SIZE]

1.Lookup in you manual, or google your monitor's correct settings.        
   Specifically these:
   Horizontal Refresh (# in Hz)
   Vertical Refresh  (# in Hz)
   Max refresh @ your desired resolution
    *For most LCDs I believe this is almost always 60Hz but look it 
     up  anyway.

2. In a terminal type:```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.suck
```*This is in case things go wrong you can revert back to your old settings using:```
sudo cp /etc/X11/xorg.conf.suck /etc/X11/xorg.conf
```

3. Use gedit or nano or whatever to open your xorg.conf file like this:```
sudo gedit /etc/X11/xorg.conf
```
Mine looked like this after getting mangled several times by me trying to use GUI tools to get the settings right:```
[COLOR="Silver"]

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection
[/COLOR]
[COLOR="Red"]Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
EndSection[/COLOR]

[COLOR="Silver"]Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GT"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection[/COLOR]

[COLOR="Red"]Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-1"
    Option         "metamodes" "CRT-0: 1024x768 +1600+0, CRT-1: 1600x1200_70 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection[/COLOR]

```
"Monitor" was working fine while my second monitor "Monitor0" was stuck at low-res and low-refresh.

After changing the refresh values in my "Monitor0" section to the correct range for my specific model, and editing the "metamodes" line (both shown in red) to the following and restarting X (ctrl+alt+backspace)```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    [COLOR="Red"]HorizSync       31.0 - 96.0
    VertRefresh     55.0 - 160.0[/COLOR]
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-1"
    [COLOR="Red"]Option         "metamodes" "CRT-0: 1600x1200_70 +1600+0, CRT-1: 1600x1200_70 +0+0"[/COLOR]
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```
All of the sudden everything was groovy, the monitor was at the resolution I wanted and the Nvidia settings GUI has more appropriate refresh options to choose.  Good luck yith your settings.

---

### Post by BCtom on 2009-02-01
Well Jive Turkey, It was your post that seems to have given me the desired screen resolution that I have fought for for so long since moving to 8.10. I have the Nvidia GeForce 6200 A-LE card and a 19" TFT LCD Monitor that I wanted to have at 1440x900 resolution--it took me exactly eight tries before I got it!

This was too much BS. If it wasn't for my strong convictions towards LINUX and open source, I would have gone back Fedora-Core, or worse yet..... no, I can't say it.

Anyway, my settings are:

HorizSync       55.9 - 55.9
    VertRefresh     60.0

...and

 Option         "metamodes" "1440x900 +0+0"

So, there is way to force the screen resolution in 8.10! I am a happy camper once again. Unfortunately it was by trial and error writing the xorg.conf, so you have to know your monitor's specifications. Nvidia's auto settings will not work in with some hardware settings. I hope Ubuntu will listen to the masses in its next incarnation.

---

### Post by Jive Turkey on 2009-05-08
Glad I helped someone, that took a while for me to figure out and then write.

---

