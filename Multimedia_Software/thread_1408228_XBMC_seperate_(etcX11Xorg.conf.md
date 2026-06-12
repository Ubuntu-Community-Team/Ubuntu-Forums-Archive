---
title: "XBMC seperate (/etc/X11/Xorg.conf"
date: 2010-02-16
forum: Multimedia Software
---

### Post by pacecal on 2010-02-16
When i login to ubuntu i can use 'XBMC' or 'GNOME' in the bottommenu.
 
When i login to XBMC i want to load an other xorg.conf. Is dit possible?
 
Normaly i use 2 monitors. For XBMC i just want to use the right monitor, the left should be disabled.

---

### Post by aeiah on 2010-02-16
my setup is a little different so i cant help directly but here goes:

my pc has a normal 19" monitor and a 32"HDTV. to enable refresh sync for videos to avoid tearing, and generally because i never need them both on at the same time, i have a seperate xorg entry for my tv and launch a seperate x session through some scripts when i hit a button on my remote.

i use two different server layouts within xorg and then call the hdtv one when i need it. i assume you could specify your single-monitor-only layout within your login config somehow.

so, aside from my normal monitor xorg.conf entries i also have a default server layout:
```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Screen0" 0 0
EndSection

```

and a hdtv layout + xorg entries for Screen1, my hdtv:

```

Section "ServerLayout"
    Identifier     "hdtv"
    Screen         "Screen1" 0 0
EndSection

Section "Monitor"

    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "AOC L32W451"
    DisplaySize     1600    900
    HorizSync       31.0 - 50.0
    VertRefresh     56.0 - 75.0
    Option         "ExactModeTimingsDVI" "TRUE"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7800 GT"
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-0: 1280x720 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

to activate the x session (which should be possible to configure during your different login thing) i run a script that does, amongst other things:
```

X :1 -layout hdtv &
export DISPLAY=:1.0
nvidia-settings -a :1.0/SyncToVBlank=1 &
nvidia-settings -a :1.0/AllowFlipping=1 &
nvidia-settings -a :1.0/XVideoTextureSyncToVBlank=1 &
nvidia-settings -a :1.0/XVideoBlitterSyncToVBlank=0 &
xbmc;

```

the nvidia things are just to make sure i have it synced up nicely for videos so i dont get tearing. the important bit i guess is the top two lines, where i export my layout called 'hdtv' to display 1. the bottom line activates xbmc. perhaps you can fit some of that code into your login

---

### Post by pacecal on 2010-02-16
tnx a lot!  i will try this @ home

---

