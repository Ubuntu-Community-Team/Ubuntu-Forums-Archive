---
title: "Custom Modeline for Sony Projector"
date: 2008-02-05
forum: Multimedia &amp; Video
---

### Post by dvjunk on 2008-02-05
I am trying to apply a custom modeline for my Sony VPL-HS20 projector. However it doesn't seem to be working.
I tried it with and without Option         "DPMS".
I found this modeline posted by several different users specifically for this projector, so I think it is a good modeline.

Is there something wrong with my xorg.conf?
I assume I should see this mode appear in nvidia-settings!!??

When I do sudo nvidia-settings from a terminal I get these errors (with or without the modeline) which were reported in this thread without any resolution: [http://ubuntuforums.org/showthread.php?t=672254](http://ubuntuforums.org/showthread.php?t=672254)
ERROR: Cannot open display 'dvr-desktop:0.0'.


ERROR: Unable to assign attribute DigitalVibrance specified on line 21 of
       configuration file '/home/dvr/.nvidia-settings-rc' (no Display
       connection).

the second error is repeated about 30 times for different attributes.


Here is the section of my xorg.conf:
Section "Monitor"
    Identifier     "VPL-HS20"
    ModeLine       "1368x768" 80.3 1368 1424 1568 1784 768 769 780 803 -hsync -vsync
#    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV44A [GeForce 6200]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV44A [GeForce 6200]"
    Monitor        "VPL-HS20"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1368x768" "1280x720" "720x480" "640x480"
    EndSubSection
EndSection

---

