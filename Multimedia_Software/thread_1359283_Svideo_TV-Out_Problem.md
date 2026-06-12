---
title: "Svideo TV-Out Problem"
date: 2009-12-19
forum: Multimedia Software
---

### Post by yousillygoose on 2009-12-19
Hey all.  I have had all sorts of problems properly configuring svideo to TV since Gutsy (gutsy worked perfectly!).  Simply using nvidia-settings fails to setup SVIDEO out properly.  I have to play a lot with my xorg to make anything at all appear on the tv.  I will post my xorg and then tell you my problem!

```

Section "Module"
	Load	"glx"
EndSection

Section "ServerLayout"
	Identifier	"Layout0"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen0"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Seiko"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600"
    #Option         "OnDemandVBlankInterrupts" "true"
    #Option         "RegistryDwords" "PowerMizerLevel=0x1"
    Option         "NoLogo" "True"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600"
    Option         "TVOutFormat" "SVIDEO"
    Option         "TVStandard" "NTSC-M"
    Option         "NoLogo" "True"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Coolbits" "1"
    Option         "AddARGBGLXVisuals" "True"
    #Option         "TwinView" "1"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "TV: nvidia-auto-select +0+0"
    #SubSection     "Display"
    #    Depth       24
    #EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "1"
EndSection

```


It is displaying on the tv screen with a separate X session (which is fine since I could never configure twinview since Gutsy).  There are two problems.

1) If I drag my mouse to the right (where the tv monitor is configured to show) the mouse pointer shows nicely on the tv screen.  The problem is that I cannot drag the mouse back to my laptop's screen.  Once I go to control the screen on the tv there is no turning back.  Does anyone know how I could possible fix this?

2)  The resolution on my tv is a bit weird.  It cuts off the borders of my screen on all sides.  This causes a problem while watching movies and having the left and right sides of the picture cut off (the movie is still watchable but it bother me nonetheless).  I was wondering if there is a way to fix this.


Thanks all and I appreciate any help you can provide.

ysG

---

### Post by yousillygoose on 2009-12-20
bump

---

