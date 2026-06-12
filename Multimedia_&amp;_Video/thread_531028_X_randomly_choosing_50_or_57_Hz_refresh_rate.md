---
title: "X randomly choosing 50 or 57 Hz refresh rate"
date: 2007-08-21
forum: Multimedia &amp; Video
---

### Post by Ben Jao Ming on 2007-08-21
Hi all,

I need to run 57 Hz on my flat panel, because the picture is all wrong in 50 Hz (nice going, LG!). But even though I've typed in my screen specs in xorg.conf, X willl always start in 50 Hz. When I log into Gnome, it will sometimes go to 57 Hz and sometimes not... it seems totally random. I may have to restart X once, twice or four times.. but suddenly Gnome goes into 57 Hz.. which I want X to do from the mere beginning - it shouldn't be Gnome that's able to tell that I can run 1680x1050@57Hz.

Here's my facts:

[LIST]
[*]Nvidia kernel module version 1.0-9631
[*]Geforce 6200
[*]Xorg 7.2.0
[*]Nvidia Xorg driver 1.0.9631
[/LIST]

The snippet from my xorg.conf. DPMS is removed, because it didn't make a difference, and I know for sure that HorizSync and VertRefresh are correct.

```
Section "Monitor"
    Identifier     "LG"
    DisplaySize     474    296
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
#    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVidia"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVidia"
    Monitor        "LG"
    DefaultDepth    24
    Option         "RenderAccel" "true"
    Option         "AllowGLXWithComposite" "true"
    Option         "DisableGLXRootClipping" "True"
    Option         "NvAGP" "1"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection
```

I'm worried about this message from X.org.log.0. Could it be that the nvidia driver is getting stuff wrong?

```
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
```


Thanks for reading,
Benjamin

---

### Post by Ben Jao Ming on 2007-08-21
Ok, I found out about nvidia-settings and used it to generate options "metamodes ...", which got me booting X into 60Hz:

```
    Option         "metamodes" "1680x1050_60 +0+0; 1680x1050 +0+0; 1280x1024 +0+0; 1280x960 +0+0; 1152x864 +0+0; 1024x768 +0+0; 800x600 +0+0; 640x480 +0+0"
```

Gnome's Screen Resolution dialog is calling it 58Hz, while both Xorg.0.log and my monitor is saying 60Hz. I'd still like to go into another refresh rate, since I'm still missing 3 mm on the right side. But I think the problem is a matter of adjusting my HorizSync and VertRefresh and then typing in the right stuff in metamodes.

---

