---
title: "Minimal xorg.conf for multi head display"
date: 2007-10-29
forum: Multimedia &amp; Video
---

### Post by badrunner on 2007-10-29
I'm posting this in the hope it will be useful to others, its my xorg.conf for nvidia which relies on auto configuration for everything. Basically everything (mouse, keyboard and number of monitors) are all detected correctly at runtime and everything works brilliantly. I use nvidia-settings to toggle screens off forcibly when i want to (for instance when running fullscreen games).

I love it as it just auto detects *everything* on my system, displayconfig-gtk just generates garbage for me:

```

Section "Device"
        Identifier      "nVidia Corporation G80 [GeForce 8800 GTS]"
        Driver          "nvidia"
        Option          "TwinView"      "True"
        Option          "NoLogo"        "True"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation G80 [GeForce 8800 GTS]"
EndSection

```

Yes, it really is that simple!

Hope this helps some people.

FYI, if you want to change the xinerama order of screens so that gnome panels show up on a particular display, you can use the following in the "Device" section:

```
Option          "TwinViewXineramaInfoOrder" "DFP-1, DFP-0"
```

In this case it just swaps 2 flat panel displays, you would need to change the values to suit your particular setup.

---

