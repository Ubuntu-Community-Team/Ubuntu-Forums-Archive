---
title: "Can't set resolution of one of my two screens."
date: 2014-05-28
forum: Multimedia Software
---

### Post by Jacajack on 2014-05-28
Hello everyone! :)

My problem is i have 2 screens connected with my computer. My ubuntu detected one of them correctly and resolution is ok, but second one
can't be detected and it sets it to 1024x768 ( native is 1280x1024 ). I tried xrandr from terminal, but I'm getting errors.
I've also tried "gksu nvidia-settings", but it also sets ViewPortOut "1024x768+0+0".
It's very annoying because if I move windows between screens they rescale about 2 times. ;(

Also, "xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync" works well.
 It gives error "xrandr: cannot find mode "1280x1024_60.60"" when I'm trying this: "xrandr --addmode DVI-I-0 1280x1024_60.60"

Hardware:

LG FLATRON L1919S ( 1280x1024 ) ( DVI-I-0 ) <--This one is bad one
LG FLATRON E2240 ( 1920x1080 ) ( VGA-0 ) <--This one is working correctly

---

### Post by Bucky Ball on 2014-05-28
Welcome. Have you tried tweaking with arandr? That is a graphical front-end for xrandr and has worked for me (I'm also using two screens, different sizes). Try it and see if that offers you the correct resolution for your monitor.

---

### Post by Jacajack on 2014-05-28
Yes. I have it installed, and I have played with it for few minutes.
When I rightclick on my monitor maximum resolution i can choose is 1024x768 :(

---

### Post by Jacajack on 2014-05-28
Also when I restart my PC there is an error window with this:

[I]```
none of the selected modes were compatible with the possible modes:
Trying modes for CRTC 635
CRTC 635: trying mode 1024x768@60Hz with output at 1280x1024@60Hz (pass 0)
CRTC 635: trying mode 1360x768@60Hz with output at 1280x1024@60Hz (pass 0)
CRTC 635: trying mode 1360x768@60Hz with output at 1280x1024@60Hz (pass 0)
CRTC 635: trying mode 1152x864@60Hz with output at 1280x1024@60Hz (pass 0)
CRTC 635: trying mode 800x600@72Hz with output at 1280x1024@60Hz (pass 0)
CRTC 635: trying mode 800x600@60Hz with output at 1280x1024@60Hz (pass 0)
CRTC 635: trying mode 800x600@56Hz with output at 1280x1024@60Hz (pass 0)
CRTC 635: trying mode 680x384@120Hz with output at 1280x1024@60Hz (pass 0)
CRTC 635: trying mode 680x384@120Hz with output at 1280x1024@60Hz (pass 0)
CRTC 635: trying mode 640x480@60Hz with output at 1280x1024@60Hz (pass 0)
CRTC 635: trying mode 512x384@120Hz with output at 1280x1024@60Hz (pass 0)
CRTC 635: trying mode 400x300@144Hz with output at 1280x1024@60Hz (pass 0)
CRTC 635: trying mode 320x240@120Hz with output at 1280x1024@60Hz (pass 0)
CRTC 635: trying mode 1024x768@60Hz with output at 1280x1024@60Hz (pass 1)
CRTC 635: trying mode 1360x768@60Hz with output at 1280x1024@60Hz (pass 1)
CRTC 635: trying mode 1360x768@60Hz with output at 1280x1024@60Hz (pass 1)
CRTC 635: trying mode 1152x864@60Hz with output at 1280x1024@60Hz (pass 1)
CRTC 635: trying mode 800x600@72Hz with output at 1280x1024@60Hz (pass 1)
CRTC 635: trying mode 800x600@60Hz with output at 1280x1024@60Hz (pass 1)
CRTC 635: trying mode 800x600@56Hz with output at 1280x1024@60Hz (pass 1)
CRTC 635: trying mode 680x384@120Hz with output at 1280x1024@60Hz (pass 1)
CRTC 635: trying mode 680x384@120Hz with output at 1280x1024@60Hz (pass 1)
CRTC 635: trying mode 640x480@60Hz with output at 1280x1024@60Hz (pass 1)
CRTC 635: trying mode 512x384@120Hz with output at 1280x1024@60Hz (pass 1)
CRTC 635: trying mode 400x300@144Hz with output at 1280x1024@60Hz (pass 1)
CRTC 635: trying mode 320x240@120Hz with output at 1280x1024@60Hz (pass 1)
Trying modes for CRTC 634
CRTC 634: trying mode 1024x768@60Hz with output at 1280x1024@60Hz (pass 0)
CRTC 634: trying mode 1360x768@60Hz with output at 1280x1024@60Hz (pass 0)
CRTC 634: trying mode 1360x768@60Hz with output at 1280x1024@60Hz (pass 0)
CRTC 634: trying mode 1152x864@60Hz with output at 1280x1024@60Hz (pass 0)
CRTC 634: trying mode 800x600@72Hz with output at 1280x1024@60Hz (pass 0)
CRTC 634: trying mode 800x600@60Hz with output at 1280x1024@60Hz (pass 0)
CRTC 634: trying mode 800x600@56Hz with output at 1280x1024@60Hz (pass 0)
CRTC 634: trying mode 680x384@120Hz with output at 1280x1024@60Hz (pass 0)
CRTC 634: trying mode 680x384@120Hz with output at 1280x1024@60Hz (pass 0)
CRTC 634: trying mode 640x480@60Hz with output at 1280x1024@60Hz (pass 0)
CRTC 634: trying mode 512x384@120Hz with output at 1280x1024@60Hz (pass 0)
CRTC 634: trying mode 400x300@144Hz with output at 1280x1024@60Hz (pass 0)
CRTC 634: trying mode 320x240@120Hz with output at 1280x1024@60Hz (pass 0)
CRTC 634: trying mode 1024x768@60Hz with output at 1280x1024@60Hz (pass 1)
CRTC 634: trying mode 1360x768@60Hz with output at 1280x1024@60Hz (pass 1)
CRTC 634: trying mode 1360x768@60Hz with output at 1280x1024@60Hz (pass 1)
CRTC 634: trying mode 1152x864@60Hz with output at 1280x1024@60Hz (pass 1)
CRTC 634: trying mode 800x600@72Hz with output at 1280x1024@60Hz (pass 1)
CRTC 634: trying mode 800x600@60Hz with output at 1280x1024@60Hz (pass 1)
CRTC 634: trying mode 800x600@56Hz with output at 1280x1024@60Hz (pass 1)
CRTC 634: trying mode 680x384@120Hz with output at 1280x1024@60Hz (pass 1)
CRTC 634: trying mode 680x384@120Hz with output at 1280x1024@60Hz (pass 1)
CRTC 634: trying mode 640x480@60Hz with output at 1280x1024@60Hz (pass 1)
CRTC 634: trying mode 512x384@120Hz with output at 1280x1024@60Hz (pass 1)
CRTC 634: trying mode 400x300@144Hz with output at 1280x1024@60Hz (pass 1)
CRTC 634: trying mode 320x240@120Hz with output at 1280x1024@60Hz (pass 1)
```[/I]

And later it restores to default screen modes ( smaller one is prime ) and I have to restore it from nvidia-settings.
Have I messed bit too much? ;_;

Eventually I can reinstall my Ubuntu until I don't have much apps and I have it for 1 day.

---

### Post by Bucky Ball on 2014-05-28
Perhaps get rid of the modelines you have created (which should kill those boot errors) and see what arandr then offers you natively rather than have it read them.

---

### Post by Jacajack on 2014-05-29
Well, I tried with "xrandr --rmmode "1280x1024_60.00"", but it throws error "xrandr: cannot find mode "1280x1024_60.00"".
Am I doing right thing? Should I try something else?

---

### Post by Jacajack on 2014-05-29
And...
Perhaps I should tell You I've been messing around in "~/.config/monitors.xml" and things I wrote into it are still there.
Should I try to remove it as they tell here [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) ?

---

### Post by Jacajack on 2014-05-29
Yes. I backuped it and removed. Error window after startup disappeared. :)
But Arandr still isn't offering me correct resolution. :(

Also, here's my "/etc/X11/xorg.conf", heard it's worth something:
```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 331.20  (buildd@komainu)  Mon Feb  3 15:11:14 UTC 2014

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: xconfig, VertRefresh source: xconfig
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 520"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "nvidiaXineramaInfoOrder" "CRT-1"
    Option         "metamodes" "DVI-I-0: nvidia-auto-select +0+0, VGA-0: nvidia-auto-select +1024+0"
    Option         "SLI" "Off"
    Option         "MultiGPU" "Off"
    Option         "BaseMosaic" "off"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by Jacajack on 2014-06-02
Well, and there's another sad thing.
When I set something by xrandr it restores to defaults when I restart my computer.
It's the same with nvidia-settings. :(

---

### Post by Jacajack on 2014-09-05
I found a solution for that. :p Finally! 
First thing I've done was installing Ubuntu instead of GNOME, but that doesn't matter. 
Important thing was that I had bad DVI-VGA connector, it seems that couldn't transfer display data.
When I changed it to Gigabyte connector Ubuntu detected it correctly immediately. 
I hope that will help other people with same problem. c:
Thanks for your help!

---

