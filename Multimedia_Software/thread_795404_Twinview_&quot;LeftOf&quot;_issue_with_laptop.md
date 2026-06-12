---
title: "Twinview &quot;LeftOf&quot; issue with laptop"
date: 2008-05-15
forum: Multimedia Software
---

### Post by T0N3 on 2008-05-15
Alright here's a very weird issue I'm having.

When I'm at work I have my laptop connected to a secondary monitor (on my left) with Twinview and this works perfectly but my problem is when I'm at home with that same laptop. 
Every thing is fine until X starts up and I need to login and then half of the "login box" is off the screen to the left. If its possible for me to take a screenshot and attach it I will. 
Now I haven't tried it with the secondary screen set to "RightOf" to see if the same thing happens but even if it doesn't its still a problem for me.

Here's my xorg.conf:
```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "PHILIPS 107S"
    HorizSync       30.0 - 71.0
    VertRefresh     50.0 - 160.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 7400"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +1280+0"
EndSection
```

---

### Post by AcidHawk on 2008-05-21
Hmmm... My laptop is on the left of my desktop monitor.  When I remove the external monitor and power up my laptop I see 1 single screen just fine (as though there was only 1 monitor in the first place).

I have noticed that my NVIDIA settings there is a position field.  For my laptop screen the position is Absolute +0 +0 however for my desktop monitor it is Absolute +1920 +0.  I am guessing here but as the res on my laptop is 1920x1200 these settings look like they make my desktop screen start where my laptop screen stops.

I bet that your "login box" appears on the left of your laptop screen.

---

### Post by T0N3 on 2008-05-21
I just setup my desktop screen to be "RightOff" my laptop, then I powered down and unplugged it. Now everything is fine so that definitely is my problem.

I wonder why this doesn't work when it's the other way around.

---

