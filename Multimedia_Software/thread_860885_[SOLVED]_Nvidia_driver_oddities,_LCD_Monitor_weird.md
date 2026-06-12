---
title: "[SOLVED] Nvidia driver oddities, LCD Monitor weirdness, and HDTV frustration"
date: 2008-07-16
forum: Multimedia Software
---

### Post by brokenLockpick on 2008-07-16
I'm really stumped here, been trying nearly everything I can think of.
Using an Nvidia 7800gt attempting to connect a Rosewill R913J and an Akai 37inch HDTV.

For a few days I was held up due to resolution issues on the Rosewill, as it appears, although the XP version of the driver had no problems with a DVI hookup, the linux driver only seems to allow proper resolutions with a vga cable which I can live with.

The hdtv is where it gets bad. Attempting the use the vga input on the back with the motherboard's built in 6150 GPU simply didn't work (which was how I'd set it up in XP). Connecting the vga to my 7800 resulted in complete garbage for output, but only when X server started, through boot it was fine until that point. I decided to try the VIVO dongle and RGB component cables (once again worked fine in XP) but although I could finally get a picture on the screen it was as if there was no signal on the red component cable everything was a washed out blue/green color.

Using the nvidia drivers and x control panel that are suggested/available by/from ubuntu's add/remove menu. Any ideas as to how to fix this? Searching the forums for this particular problem seems to turn up unrelated problems. :confused:

---

### Post by NT4usB on 2008-07-16
(install and) run```
sudo nvidia-settings
``` Configure the monitors from there.
fwiw, I found the blue tint on mine was caused by xorg.conf not outputting a TVStandard my TV could use. In my case, the only 'HD' format it supported (via component output) was HD480i. rtfm on your TV to see what HD format(s) it will use.```
Section "Screen"
    Identifier     "Screen[1]"
    Device         "Device[1]"
    Monitor        "Monitor[1]"
    DefaultDepth    24
    Option         "TVOutFormat" "Component" #or SVIDEO Composite etc
    Option         "TVStandard" "HD480i" # "NTSC"
    Option         "ConnectedMonitor" "Monitor[1]"
    SubSection     "Display"
        Depth       24
        Modes      "1024x768_60" "720x576_60" "720x480_60" "640x480_60" "480x320_60"
    EndSubSection
EndSection
```

---

### Post by brokenLockpick on 2008-07-17
Awesome that worked almost perfectly. Now I just have to fix the auto overscanning problem that seems to be happening, but I feel worlds closer to getting this sorted.

---

