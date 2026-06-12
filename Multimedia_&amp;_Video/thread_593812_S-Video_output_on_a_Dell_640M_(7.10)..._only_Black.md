---
title: "S-Video output on a Dell 640M (7.10)... only Black and White!!"
date: 2007-10-27
forum: Multimedia &amp; Video
---

### Post by CanadianNorth on 2007-10-27
ok


I have a 640M running 7.10. I can get video out through my s-video port using the Fn-F8 hotkey (the LCD/CRT switch). BUT... it's only black and white!

any suggestions?

---

### Post by Mguel on 2007-11-02
I'm having the same problem with with my dell xps m1210. Using the i810 driver, and the black and white tv-out didn't changed with the i810switch which only enabled the Fn+F8 key to toggle. 

I haven't been able to find or manage to fix the lack of colour in the tv-out.

Cheers

---

### Post by Mguel on 2007-11-03
I'm using an almost unmodified xorg.conf file from a fresh install of ubuntu gutsy 7.10.

I've tried doing a **dpkg-reconfigure -phigh xserver-xorg, **with no luck to get colour in the tv-out.

My xorg.conf part for video output:

```

Section "Device"
    Identifier    "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
    Driver        "intel"
    BusID        "PCI:0:2:0"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection "Display"
        Modes        "1280x800" "0x817"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"

# Uncomment if you have a wacom tablet
#    InputDevice     "stylus"    "SendCoreEvents"
#    InputDevice     "cursor"    "SendCoreEvents"
#    InputDevice     "eraser"    "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection
```Once I got colour on the tv-out: Trying different things in one opportunity I changed the driver to i810 instead of intel (and I'm not sure if other changes also) and after log-out I had a 1024x768 display with no option to change it at the screen resolution preference nor at the screens at administration menu, not tv-out display, but when pressed Fn+F8 the tv displayed a colour image! while the notebook went black (with intel driver I always have a display in the notebook, it nevers go black, and what changes with Fn+F8 is the turning on or off of the tv-out).

I've searched the forum, the web, but I'm pretty lost about possible changes or tests I can make.

Thanks in advance,
Mguel

PS: Dell XPS m1210, with Intel Graphics Media Accelerator 950 / GMA950

---

### Post by itendo on 2008-03-06
reiteration of the above, sort of:

i have an even more generalized version of this problem and have been unable to find any resources regarding it. i am running a dell inspiron 700m: it runs a 1280x800 monitor on an Intel Extreme Graphics 2 but its on the 'intel - Experimental modesetting' default driver. 

the problem is that any video playback, on the standard monitor, is in black and white. ive had the problem in vlc, totem, and codeine, and mplayer. i have no idea where to start as far as updating/reinstalling the driver, if that is the problem. if its not the problem then i am completely lost.

---

