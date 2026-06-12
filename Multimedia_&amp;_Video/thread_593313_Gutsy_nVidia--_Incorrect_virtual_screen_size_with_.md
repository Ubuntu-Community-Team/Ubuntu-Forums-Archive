---
title: "Gutsy nVidia-- Incorrect virtual screen size with Twinview!"
date: 2007-10-27
forum: Multimedia &amp; Video
---

### Post by Paradoxdruid on 2007-10-27
Since my upgrade to Gutsy, my main LCD will not go above 640x480 resolution (it's normally 1280x1024).  It gives an error about reading EDID modes for it, so I disabled EDID.  If I leave twinview resolution to nvidia-auto-select for both monitors, my secondary LCD works fine at 1280x1024, but my primary is still at 640x480.

So I set the metamode to "1280x1024+0+0,1280x1024+1280+0"

And here's the output I see in my X log:
> (II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024+0+0,1280x1024+1280+0"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024

It finds both monitors, validates the mode, but what actually happens?  The main monitor is shut off completely, and it runs on only my secondary monitor.  Gah!  **How can I specify the correct virtaul screen size, or what is going on here?**

Here's a relevant chunk of my X log:
> (**) NVIDIA(0): Option "UseEDID" "False"
(**) NVIDIA(0): Option "TwinView" "True"
(**) NVIDIA(0): Option "TwinViewOrientation" "RightOf"
(**) NVIDIA(0): Option "SecondMonitorHorizSync" "30-70"
(**) NVIDIA(0): Option "SecondMonitorVertRefresh" "50-160"
(**) NVIDIA(0): Option "MetaModes" "1280x1024+0+0, 1280x1024+1280+0"
(**) NVIDIA(0): Option "NoBandWidthTest" "True"
(**) NVIDIA(0): Option "DPI" "95 x 96"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): TwinView enabled
(**) NVIDIA(0): Ignoring EDIDs
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(GPU-0): Not probing EDID on CRT-1.
(II) NVIDIA(GPU-0): Not probing EDID on DFP-0.
(II) NVIDIA(0): NVIDIA GPU GeForce 7600 GT (G73) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.73.22.51.04
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7600 GT at PCI:1:0:0:
(--) NVIDIA(0):     CRT-1
(--) NVIDIA(0):     DFP-0
(--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
(--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
(--) NVIDIA(0): DFP-0: Internal Dual Link TMDS
(II) NVIDIA(0): Assigned Display Devices: CRT-1, DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024+0+0,1280x1024+1280+0"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(**) NVIDIA(0): DPI set to (95, 96); computed from "DPI" X config option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.

And here's the relevant chunks of my xorg.conf (the Dell is the one that doesn't work any more):
> Section "Monitor"
    Identifier     "DELL 1701FP"
    Option         "DPMS"
	Horizsync	31.0-80.0
	Vertrefresh	56.0-76.0
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
EndSection

Section "Device"
    Identifier     "nVidia Corporation G70 [GeForce 7600 GT]"
    Driver         "nvidia"
   Option "UseEDID" "False"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G70 [GeForce 7600 GT]"
    Monitor        "DELL 1701FP"
    DefaultDepth    24
    Option         "TwinView" "True"
    Option "TwinViewOrientation" "RightOf"
    Option "SecondMonitorHorizSync"   "30-70"
    Option "SecondMonitorVertRefresh" "50-160"
    Option         "MetaModes" "1280x1024+0+0, 1280x1024+1280+0"
    Option "NoBandWidthTest" "True"
    Option "DPI" "95 x 96"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Thanks in advance for any help!

---

### Post by Paradoxdruid on 2007-10-28
After days of trying different options, I found a way to "solve" my problem--

Connect my LCD using its VGA cable through a VGA-DVI adapter, instead of the DVI connection.  Then, nvidia-settings and nvidia-xconfig and all the rest work as they should, automatically setting it to 1280x1024 at 60 Hz.

Honestly, I can't tell much visual difference, except on small font text, where it seems a little less sharp.  But I shouldn't need to give up my DVI connection and use an adapter just to get the correct monitor resolution.  The real problem is still extent and needs fixing.

---

### Post by ktechman on 2008-05-07
I read something about compiz messing up screen resolutions because of a setting you should find it at System/appearanceprefs/visual effects/ custom prefs/general options display settings mine was doing the same thing and I never found a solution, but you seem to have found a partial solution can you post your xorg file here so I can copy some of the settings to my rig nobody seems to want to help on this issue I can't figure it out???? Everybody is usually very helpful but on this twinview issue ????? 


                           Regards

---

