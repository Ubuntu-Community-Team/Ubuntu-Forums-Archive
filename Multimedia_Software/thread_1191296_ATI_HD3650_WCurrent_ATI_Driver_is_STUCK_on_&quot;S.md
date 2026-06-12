---
title: "ATI HD3650 W/Current ATI Driver is STUCK on &quot;Single Independent Display&quot;"
date: 2009-06-18
forum: Multimedia Software
---

### Post by xefialtis on 2009-06-18
I don't know what I did. Not that I am an idiot or anything, but...well...let me start at the beginning...

I have this new Lenovo T500 with the HD3650 Video Card. I have a Dock and I use the External analog display port (this is a work machine)...

This morning, I had MultiMonitor and everything was great...no real issues.
I went into a conference to run some things, and I hooked up the Projector. Hit the FN+F7 to change display ports and it only would BLINK, not display... so I tweaked the "amdcccle" configuration... It still wouldn't display.
I gave up and we finished the meeting without my stuff (embarrassing) ...

I stuck my machine back into the dock, and it wouldn't display on my monitor, so I went back into the "amdcccle" config and adjusted it, but no luck. Tried the FN+F7 thing, no luck...

SO I went into /etc/X11/xorg.conf and looked for something out of the ordinary...nothing...so I rebooted the machine.

WHen it came back, I still didn't have multi monitor, and when I went into "amdcccle" for the configuration, it says "Single Independent Display"...and I CANNOT CHANGE IT...
it only has one option for the Laptop Monitor, "SINGLE INDEPENDENT DISPLAY" and the external monitor, while listed, is disabled, and I CANNOT ENABLE IT, and even if I could, there is ONLY ONE SELECTION..."SINGLE INDEPENDENT DISPLAY"...

Does ANYONE Have ANY idea what the HECK is going on here? Or how I might fix it?

I can turn Xinerama ON or OFF, but with only one monitor, it does no good.

HELP!!??!!??

my xorg.conf:
```

Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
        Option      "Clone" "on"
        Option      "Xinerama" "on"
        Option      "AIGLX" "on"
EndSection

Section "Files"
EndSection

Section "Module"
        Load  "dbe"
        Load  "freetype"
        Load  "extmod"
        Load  "glx"
        Load  "dri"
EndSection

Section "ServerFlags"
        Option      "Xinerama" "on"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[1]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[1]-0"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]-0"
        Device     "aticonfig-Device[0]-0"
        Monitor    "aticonfig-Monitor[0]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[1]-0"
        Device     "aticonfig-Device[1]-0"
        Monitor    "aticonfig-Monitor[1]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "DRI"
        Group        "Video"
        Mode         0666
EndSection

```

---

