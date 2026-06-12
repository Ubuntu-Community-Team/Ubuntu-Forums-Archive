---
title: "ATI fglrx driver only allows secondary monitor to display at 1280x800"
date: 2009-06-09
forum: Multimedia Software
---

### Post by itfische on 2009-06-09
I am trying to set up external displays on my new ThinkPad W500, which has an ATI Mobility FireGL 5700W (which reports to Ubuntu as a Mobility Radeon HD 3650).  I can get it to properly use the external monitor in non-mirrored mode, but no matter what I do, the external monitor can only display at 1280x800.  My internal LCD displays correctly at 1920x1200.  I would like my external monitor to display at that resolution at least.  The external monitor that I am using is a Dell 3007WFP, which is a 30" monitor capable of resolutions up to 2560x1600.  I am wondering if anyone else has been succesfull in getting the proprietary (or even the open source) drivers to use an external monitor at a reasonable resolution.  

Here's my lspci output:
```

$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650

```Here's my current xorg.conf file:
```

Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
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

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "VideoOverlay" "on"
    Option        "OpenGLOverlay" "off"
    Option        "DesktopSetup" "vertical,reverse"
    Option        "Capabilities" "0x00000800"
#  Option        "PairModes" "1920x1200+1920x1200"
    Option        "EnableRandR12" "false"
#  Option        "Mode2" "1920x1200"
    Option      "UseFastTLS" "2"
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

Section "DRI"
    Group        "Video"
    Mode         0666
EndSection

```As you can see in the xorg.conf file, I have tried setting the Mode2 option (which is supposed to set the resolution of the secondary display, I believe), but that had no effect.  Likewise, setting PairModes has no effect on the resolution sent to the secondary monitor.  Actually, I believe that both of those put the secondary monitor into an odd state where it displayed a bit more than two copies of the desktop arranged vertically down the screen.

When I run amdcccle, it reports the second monitor correctly as the Dell, but it says its maximum resolution is 1280x800.

Incidentally, I have also tried a different monitor connected to the VGA port, and I get similar results -- the monitor is a native 1920x1200 resolution monitor, but the display only lets it go to 1280x800.

Does anyone know a way to fix this?

---

### Post by itfische on 2009-06-10
Alternatively, does anyone know how to query a given monitor for its modes?  Or a given output for its modes?  It seems like somehow the video card limits its maximum output resolution for the combined two monitors.

On my old T61p with an Nvidia card I was able to drive the 1920x1200 lcd and a 1920x1200 external monitor without any issues.  I'm rather disappointed that my new setup is giving me significantly less screen real-estate.

---

### Post by markbuntu on 2009-06-11
I seem to remember some aticonfig option to force a monitor. You could also try adding a Virtual 3840x1200 line in the Screen section but my memory is a little vague about that too. I have no proble with setting two 1920x1200 monitors with my HD3650 but I understand that the mobility HD3650 is very diferent and you may be running up against hardware constraints.

---

