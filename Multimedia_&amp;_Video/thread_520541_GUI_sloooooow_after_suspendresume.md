---
title: "GUI sloooooow after suspend/resume"
date: 2007-08-08
forum: Multimedia &amp; Video
---

### Post by josh2112 on 2007-08-08
I'm with the 2 or 3 of you who are trying to get Ubuntu functional on an HP dv6500t laptop ;-)  I got the nVidia drivers installed using envy and they appear to be working great; glxgears scores of over 3000 FPS.

Suspend and resume seem to work OK too, however the drawing of GUI elements is really slow upon resume.  I mean REALLY slow - when I click on the KMenu, I can outline w/shadow being drawn, the lefthand blue bar being filled in, then the menu itself being drawn from top to bottom.  When I drag a window around, I think I'm back on my old K6 233Mhz - it lags way behind the cursor.

glxgears scores drop a bit but are still pretty decent at 2500 FPS, it's just the 2D drawing that suffers horribly.  I can restart X with Ctrl-Alt-Backspace and everything is lightning fast again :guitar:

I've tried switching the POST_VIDEO setting in /etc/default/acpi-support between true and false, it doesn't seem to have any effect.  And there's nothing weird in dmesg after the resume.

Anybody know what's going on?

Specs:
Kubuntu Feisty, kernel 2.6.20-16-generic
nVidia GeForce Go 8400M w/nVidia drivers 100.14.11

Relevant sections from xorg.conf:

```

Section "Module"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

...

Section "Monitor"
    Identifier     "dv6500t LCD"
    HorizSync       28.0 - 50.0
    VertRefresh     43.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia GeForce Go 8400M"
    Driver         "nvidia"
    Option         "NvAGP"  "1"
EndSection

....

Section "Extensions"
    Option         "Composite" "Enable"
EndSection


```

BAH!  I just noticed the Composite Enable thing, I guess envy did that.  I'll turn it off and see if it has any effect...

---

