---
title: "TwinView leads to Counter Strike/Condition Zero Problems"
date: 2008-02-04
forum: Multimedia &amp; Video
---

### Post by Kimm on 2008-02-04
Well, take a look at the picture, it speaks for itself.
I would like to point out that this is not a KDE4 issue, but a definently a TwinView issue (since I have the same problem in Gnome) and that this problem was not there when I ran two separate X-screens.

I set up TwinView using nvidia-settings, and added the following lines for the TV (screen0, to get colour):

> 
Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
[B]    Option         "TVOutFormat" "SVIDEO"
    Option         "TVStandard" "PAL-G"[/B]
    Option         "metamodes" "CRT: 1280x1024 +0+0, TV: nvidia-auto-select +1280+0"
EndSection


For now, I can run games in a fake Wine desktop, but that is just not the same as fullscreen

---

