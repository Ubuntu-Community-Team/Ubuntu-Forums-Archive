---
title: "NVIDIA: How I fixed my display resolution problem with DVI-D connection!"
date: 2006-06-11
forum: Multimedia &amp; Video
---

### Post by blastus on 2006-06-11
I have a SyncMaster 740b LCD that supports 1280x1024 75Hz and a GeForce FX-5600 card. The problem I had was that I could not run my monitor at its native resolution 1280x1024 with a DVI-D connection. At 1280x1024, the display would become unstable and blank out for a few seconds everytime I moved a window, opened a menu, really anything that would cause an update to the display. I should point out that using a D-Sub (analog) cable does NOT have this issue, the problem is only when using a DVI-D cable.

I am thoroughly convinced that the majority of resolution problems with DVI-D connections has to do with a mismatch between the timing cycle of the video card and the timing mode of the monitor. Either the monitor reports incorrect EDID modes or somehow X can't validate them or doesn't know how to use them. After spending literally countless hours trying to get a DVI-D connection to work at 1280x1024 75Hz, I finally got it to work! The trick has to do with finding out the preset timing modes for your monitor and finding the magic "ModeLine" that corresponds to the timing mode you need.

For example, the maximum supported resolution on my LCD is:
Display Mode = 1280x1024
Horizontal Frequency(kHz) = 79.976
Vertical Frequency(Hz) = 75.025
Pixel Clock(MHz) = 135.00
Sync Polarity(H/V) = +/+

Unfortunately, my monitor does NOT report this mode via EDID. I read tseliot's awesome [NVIDIA Dapper Guide](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper) which helped point me in the right direction. Unfortunately none of the tools for generating ModeLines could create one that matched the timing mode I needed. However, by accident I stumbled upon the following ModeLine from [this website](http://lists.debian.org/debian-user/2006/02/msg00415.html):

# 1280x1024, 75.0Hz; hfreq=79.98, vfreq=75.03
ModeLine "1280x1024" 135.00 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync

So I edited my xorg.conf file and added the ModeLine but it still wouldn't work. The problem is that according this [NVIDIA documentation page](http://download.nvidia.com/XFree86/Linux-x86/1.0-8762/README/appendix-d.html), you may have to specify the AllowNon60HzDFPModes option to run a resolution with a refresh rate other than 60Hz. So here's the magic xorg.conf file that I found worked...

```
Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
    # 1280x1024, 75.0Hz; hfreq=79.98, vfreq=75.03
    ModeLine "1280x1024_7" 135.00 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV31 [GeForce FX 5600]"
    Driver         "nvidia"
    BusID	   "PCI:1:0:0"
    Option         "ConnectedMonitor" "DFP-0"
    Option         "UseEDID" "False"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV31 [GeForce FX 5600]"
    Monitor        "Generic Monitor"
    DefaultDepth    16
    Option         "ExactModeTimingsDVI" "TRUE" 
    Option         "ModeValidation" "DFP-0: AllowNon60HzDFPModes, NoEdidModes, NoVesaModes, NoXServerModes"    
    SubSection     "Display"
        Depth       16
        Modes       "1280x1024_7"
    EndSubSection
EndSection
```

In the Monitor section I have a ModeLine corresponding to the timing mode I want. The 1280x1024_7 is a just a label for the mode, I could have called it anything I think.

In the Device section, because I am using a Digital Flat Panel, the ConnectedMonitor option specifies DFP-0. I also have set the UseEDID option to false because I don't want to X to use the EDID modes my monitor reports (because it doesn't report 1280x1024 75Hz anyway.)

In the Screen section, the ExactModeTimingsDVI tells X to use the timing information in my ModeLine precisely. The magic is in the ModeValidation option where I tell X to allow my non-60Hz mode and not to consider any timing modes that may be derived from EDID, VESA or X Server.

I still don't understand a lot of this, but I'm sure glad I can now use a DVI-D connection with my LCD! The picture is amazing and crystal clear. BTW: I have the same problem in Windows XP with my LCD and a DVI-D connection; I can't run my LCD at 1280x1024. I haven't been able to fix this in Windows but I don't care anyways, as long as it works in Linux I'm a happy camper!

---

