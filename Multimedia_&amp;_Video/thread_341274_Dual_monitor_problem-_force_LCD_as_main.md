---
title: "Dual monitor problem- force LCD as main"
date: 2007-01-18
forum: Multimedia &amp; Video
---

### Post by razialx on 2007-01-18
Hello, I am having a problem with my dual monitor setup. It isn't a huge problem, but I was hoping someone could help.

I am running Ubuntu Edgy on my Dell laptop(Inspiron 8500, GeForce 4 4200) . I have dual monitors working, that was simple enough. However I am having a problem forcing my laptop screen to be the primary monitor and the CRT that I connect externally to be the secondary. 

I do not want this to be a spanning desktop. I want a maximized window to maximize to one monitor. And they need to be different resolution surfaces on each screen. I have this working with my current setup. The only problem is that the CRT is being set as the main screen, and therefore getting the main toolbars on it, when I need them on the LCD.

I can live with it whle I am working, but to pickup and take my laptop away I must change the resolution so the main toolbars are moved to the LCD screen. 


Here are my configuration scripts (I tried many things, but I am sure it is something simple)

Section "ServerLayout"
    Identifier     "TwinView Configuration"
    Screen         0 "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
    Option "Xinerama" "Off"
EndSection
...[cut]...
Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
	#Load	"dri"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection
...[cut]...
Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV28 [GeForce4 Ti 4200 Go AGP 8x]"
    Driver         "nvidia"
Option "NvAGP" "2"
Option "RenderAccel" "1"
Option "CursorShadow" "1"
Option "Coolbits" "0"
#Option "ConnectedMonitor" "dfp, crt"
Option "UseDisplayDevice" "DFP,CRT"
#Option "ConnectedMonitor" "DFP,CRT"
Option "NoPowerConnectorCheck"
Option "TwinView" "1"
Option "TwinViewOrientation" "CRT RightOf DFP"
Option "Metamodes" "DPF: 1280x800, CRT: 1024x768;   DFP: 1280x800, CRT: NULL"
Option "HorizSync" "CRT: 31-82; DFP: 40-70"
Option "VertRefresh" "CRT: 50-75; DFP:60"
#Option "NoTwinViewXineramaInfo"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV28 [GeForce4 Ti 4200 Go AGP 8x]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "RenderAccel" "true"
    
    SubSection     "Display"
    	Viewport 0 0
	Depth       24
        Modes      "1280x800" "1024x768" "800x600"
    EndSubSection
EndSection


Thank you ahead of time for any help anyone can give.

---

