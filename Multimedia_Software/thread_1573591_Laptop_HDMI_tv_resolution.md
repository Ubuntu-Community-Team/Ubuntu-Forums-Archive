---
title: "Laptop HDMI tv resolution"
date: 2010-09-12
forum: Multimedia Software
---

### Post by primus454 on 2010-09-12
So I want to hook my laptop up to my tv for the sake of watching movies. However, my resolutions do not match up. The laptop maxes out at 1280X800, while the closest resolution for the tv is 1280x720. I have tried so many things but to no avail. Somebody please help, this is driving me mad...

---

### Post by thook07 on 2010-09-13
What have you tried exactly? I run my computer through HDMI to a 26" Vizio 720p HDTV. I had no problems.

Does the image show up on your TV?

If so, is the image to zoomed in because of the pixel difference?

Are you trying to have multiple monitors or just duplicate the display on both monitors (your laptop and TV)?

You haven't really described the problem very well....

---

### Post by primus454 on 2010-09-13
I thought it seemed pretty clear but I guess not...I have a geforce 9300m video card btw.

I want to run a cloned display to simply watch movies (at the time), nothing else, on my 26" 720p Sanyo LCD. Like I said in the original post, the closest match I can get is my laptop at 1280x800 and the tv at 1280x720. This results in the bottom part of the laptop screen being cut of when displayed on the tv.

I have tried messing with the nVidia settings as well as trying to mess with xorg.conf and using xrandr. I have yet to get any positive results.

---

### Post by Grenage on 2010-09-13
I think you're best off just configuring it as an additional display, do you need to clone? (not that it should be a problem using different resolutions on a clone).

I just use metamodes, which is what the nvidia-settings utility will use:

```
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT-0: 1440x900_75 +0+0, CRT-1: 1440x900_75 +1440+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
```

---

### Post by primus454 on 2010-09-13
Code1 is what my xorg.config reads, Code2 is what I'm guessing it should read. I can't check it atm, but will mess with it when I get back to my dorm.

```
Section "Screen"

# Removed Option "metamodes" "DFP-1: nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

```
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "DFP-0: 1280x800 +0+0, DFP-1: 1280x720_60 +1440+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

### Post by Grenage on 2010-09-13
I think you'd want Twinview to be off (0) if you were after cloning.  I can't be sure - I've never opted for a clone over an expanded desktop.

---

### Post by primus454 on 2010-09-13
So just change the 1 to a 0 and you think I would be set?

---

### Post by Grenage on 2010-09-13
It's not going to kill your computer, so I'd give it a go.  Just make sure you've backed up your existing xorg.conf.

As I said, I've not attempted to clone the display before.  Actually, I'm going to try here.

---

### Post by Grenage on 2010-09-13
I stand corrected, this worked for me:

```
Section "Screen"

    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT-0: 1440x900_75 +0+0, CRT-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

I configured that using the nvidia-settings application (running with sudo).  The cloning is likely specified in the serverlayout section.

---

