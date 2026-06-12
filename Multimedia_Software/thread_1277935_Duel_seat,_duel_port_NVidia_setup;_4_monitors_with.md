---
title: "Duel seat, duel port NVidia setup; 4 monitors with Xinerama"
date: 2009-09-28
forum: Multimedia Software
---

### Post by djSeverin on 2009-09-28
It would appear that Ubuntu 9.04 doesn't handle multiple video cards running as a Xinerama?

I have 2x NVidia cards, a FX-5200 PCI and a 7600-GS AGP (Model nr's may not be perfect, but you get the gist of it).

I can quite easily get both cards running, and I can get 4x X-sessions running over the 4 monitors. I can't however get them to run as a Xinerama!

Everything is fine until I enable Xinerama in the xorg.conf file.

I had been using 8.04 and it was fantastic, I will post my xorg.conf file for that below so anyone interested can see how I achieved this; but in 9.04, it comes down to Xinerama.

For those who have a similar problem, I found [this forum post earlier]("http://ubuntuforums.org/showthread.php?t=884161&highlight=xinerama+nvidia&page=6") that may contain the key to fixing this, though I won't get a chance to try it till later this evening...

So whats the go with Xinerama not working under 9.04 when you have a multi-seat, multi-monitor NVidia setup?

And my xorg.conf file that works perfectly in 8.04 and not in 9.04:
```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    Screen      2  "Screen2" RightOf "Screen3"
    Screen      3  "Screen3" RightOf "Screen1"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    # RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"[B]
    [COLOR="Red"]Option         "Xinerama" "1"[/COLOR][/B]
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
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor2"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor3"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
    BusID          "PCI:2:1:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
    BusID          "PCI:2:1:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Videocard2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard3"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Rotate" "CCW"
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "Rotate" "CCW"
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
EndSection

Section "Screen"
    Identifier     "Screen2"
    Device         "Videocard2"
    Monitor        "Monitor2"
    DefaultDepth    24
    Option         "Rotate" "CCW"
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
EndSection

Section "Screen"
    Identifier     "Screen3"
    Device         "Videocard3"
    Monitor        "Monitor3"
    DefaultDepth    24
    Option         "Rotate" "CCW"
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
EndSection

```

This works in 9.04 IF you disable Xinerama... So whats the go? :confused:

---

### Post by djSeverin on 2009-09-29
Seems xserver-glx doesn't exist in the Jaunty 9.04 repo's... So back to square 1.

Further to the earlier problem; Although I can get all 4 heads to init and display a gnome desktop, I can not start applications on any but the first head.

If I attempt to start an app on head 2, 3 or 4; the gnome desktop dies and restarts...

Not having much luck thus far.

Any idea's?

---

### Post by djSeverin on 2009-10-01
Well, I've been at this Linux thing since Redhat 5.2, but this one has me stumped.

From what I can see, Xinerama and the version of X in Ubuntu 9.04 Jaunty simply don't play together over multiple video cards.

Can anyone else confirm? :confused:

---

### Post by markbuntu on 2009-10-01
That is most likely something to do with the nvidia driver and how it is using RandR1.2 which is the version in Jaunty. I have multiple ati gpus and the ati driver disables RandR and uses xinerama for multiple gpus since RandR1.2 does not have multi-gpu capabilities. The latest ati drivers do this automatically but in earlier versions I had to add this line in the device section of xorg.conf.

Option "EnableRandR12" "false"

I think randr and xinerama may be mutually exclusive. Bigdesktop, which is the ati version of twinview is also not available when xinerama is enabled because it uses RandR.

So, maybe you need to not use twinview and disable randr to get xinerama working properly.

But like I said, that was with ati, the nvidia solution is probably a little different but similar in what it accomplishes.

---

### Post by judas3000gold on 2009-10-02
similiar problem

had to disable glx

replace "Load 'glx'" with "Disable 'glx'"
now i have xinerama working, but i can't switch to to virtual terminal, just blinking curser and sometimes the switching crashes the gnome-session

also a problem with starting a second Xserver for gaming purpose as it sometimes crashes the old gnome-session

i'll try this option know
Option "EnableRandR12" "false"
for what i have read, randr1.2 can't handle multiple gpus, i guess it gets automatically loaded when glx is enabled and then crashes

---

