---
title: "Help - Attaching new monitor - do I need to do anything first?"
date: 2006-08-31
forum: Multimedia &amp; Video
---

### Post by aleska on 2006-08-31
Hi, I have a 15" ViewSonic VA520 that I want to go out and replace with a larger screen monitor.  I have an integrated nvidia GeForce 6150le video and use the latest nvidia drivers.  I have the nvidia settings panel under Applcations -> System Tools

Do I need to tweak or adjust anything before I add my new monitor, or it is plug and play in the sense that linux will recognize the new monitor and adjust accordingly?  Right now, this is how my xorg.conf files reads as it relates to Monitor and Device.

> Section "Monitor"
    Identifier     "VA520"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "VA520"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

So, what do I need to do before and after attaching the new monitor?
TIA
-aleska

---

### Post by tseliot on 2006-08-31
My suggestion is the following:

Boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

Press ENTER whenever you don't know the answer to a question. When you get to the point at which it asks you about your monitor you can choose the Advanced option so as to be able to choose the right refresh rate (vertical and horizontal rate) for your monitor (if your monitor is detected you will see the name of your monitor and the suggested refresh rate).

then type:
```
reboot
```

---

