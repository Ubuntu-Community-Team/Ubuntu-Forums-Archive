---
title: "Cannot enable 24p video output (nvidia)"
date: 2011-11-01
forum: Multimedia Software
---

### Post by MasterZ on 2011-11-01
Hi,

I'm using an Nvidia GTX 560 on my HTPC to watch movies. 
When watching Hi-def movies in 24p, some frames get dropped and it is really visible in some scenes. 

I think I should switch my output to 24Hz when watching those movie. 

My HTPC is connected to a Yamaha video amplifier and it reports an HDMI source of 1080p@60hz. 
I also have a PS3 hooked up to the amp and when watching Blu-rays, the output switches to 24hz. (I can verify this on the TV source info and on the amplifier as well). 

From the HTPC however, I cannot change the output refresh rate at all. 

In the nvidia-settings utility, I can change the resolution options to select a refresh rate of 60hz, 50hz or 24hz, but when I click 'Apply', nothing changes and the amplifier still reports a 60hz source. 

In the Xorg.0.log, I can see that: 
```

(II) NVIDIA(0): Setting mode "1920x1080_24+0+0"

```

BUT
Checking on the command line, I can confirm that it's still 60Hz: 
```

sudo nvidia-settings -q Refreshrate
  Attribute 'RefreshRate' (HTPC:0.0; display device: DFP-1): 60.00 Hz.

```

I tried to play with the xorg.conf, but either it doesn't change anything, or it breaks the X server. 

Why does the Nvidia utility report a 24Hz setting that does nothing when selected ? 
And how could I change my refresh rate to 24Hz ? 


Thanks for any help.

---

### Post by BicyclerBoy on 2011-11-01
Does the amp & TV show 24p or 60p when playing fullscreen video with VDPAU ?

I doubt the video card is dropping frames if it is using VDPAU decode.

If the video card outputs at 60p, it has to create frames by either: pulldown or interpolation.

Most new TVs take 24p & then interpolate to 48 or 96 (frame create) because people don't like 24p temporal resolution but "cartoon" playback is equally sad.

I hope the card can perform some interpolation (like shader de-interlacing) but I don't know yet..
I have little doubt a new HTPC video card can out-perform the TV engine.


Does your /var/log/Xorg.0.log show validated video modes for 24p on the TV ?

---

### Post by MasterZ on 2011-11-02
Hi, 

The amp still shows that the refresh rate is 60hz even during full screen playback (using vlc or xbmc). 

Maybe the card isn't dropping frames, but it feels like it. 
Especially during camera travelling on landscapes, there are some small 'hangups', still very noticeable. 

The CPUs are not used close to 100%, I got free RAM, so I do not think about a performance issue. 
This is why I'm looking into the refresh rate, to test the 24p and see if it helps. 

I looked deeply into the Xorg.0.log, as you proposed and I see these lines that could maybe describe the issue with 24P: 
```

[  6135.596] (--) NVIDIA(0): Connected display device(s) on GeForce GTX 560 Ti at
[  6135.596] (--) NVIDIA(0):     PCI:1:0:0
[  6135.596] (--) NVIDIA(0):     SONY TV (DFP-1)
[  6135.596] (--) NVIDIA(0): SONY TV (DFP-1): 165.0 MHz maximum pixel clock
[  6135.596] (--) NVIDIA(0): SONY TV (DFP-1): Internal Single Link TMDS
[  6135.601] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
[  6135.601] (**) NVIDIA(0):     enabled on all display devices.[B]
[  6135.601] (WW) NVIDIA(0): The EDID for SONY TV (DFP-1) contradicts itself: mode
[  6135.601] (WW) NVIDIA(0):     "1920x1080" is specified in the EDID; however, the EDID's
[  6135.601] (WW) NVIDIA(0):     valid VertRefresh range (48.000-62.000 Hz) would exclude
[  6135.601] (WW) NVIDIA(0):     this mode's VertRefresh (24.0 Hz); ignoring VertRefresh
[  6135.601] (WW) NVIDIA(0):     check for mode "1920x1080".
[  6135.605] (WW) NVIDIA(0): The EDID for SONY TV (DFP-1) contradicts itself: mode
[  6135.605] (WW) NVIDIA(0):     "1920x1080" is specified in the EDID; however, the EDID's
[  6135.605] (WW) NVIDIA(0):     valid VertRefresh range (48.000-62.000 Hz) would exclude
[  6135.605] (WW) NVIDIA(0):     this mode's VertRefresh (24.0 Hz); ignoring VertRefresh[/B]
[  6135.605] (WW) NVIDIA(0):     check for mode "1920x1080".
[  6135.636] (II) NVIDIA(0): Assigned Display Device: DFP-1
[  6135.636] (==) NVIDIA(0): 
[  6135.636] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[  6135.636] (==) NVIDIA(0):     will be used as the requested mode.
[  6135.636] (==) NVIDIA(0): 
[  6135.636] (II) NVIDIA(0): Validated modes:
[  6135.636] (II) NVIDIA(0):     "nvidia-auto-select"
[  6135.636] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[  6135.666] (--) NVIDIA(0): DPI set to (30, 30); computed from "UseEdidDpi" X config
[  6135.666] (--) NVIDIA(0):     option
[  6135.666] (--) Depth 24 pixmap format is 32 bpp
[  6135.666] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[  6135.666] (II) NVIDIA:     access.
[  6135.669] (II) NVIDIA(0): Setting mode "nvidia-auto-select"

```

The EDID information from the TV could cause the problem. 
How could I work around that ? 

Do I need to change the VertRefresh Range in the xorg.conf ? Or will it be overriden by the EDID info anyway ?

---

### Post by BicyclerBoy on 2011-11-02
You can make the mode validation selectively ignore certain EDID parts:

Option "ModeValidation" "string"

For your case, "string" can be "NoVertRefreshCheck" etc
see the driver readme appendix B 

The actual monitor EDID contains monitor frequencies clocks & video modes..

If you use a xorg.conf monitor section with vert freq data, you then need to use the above Option or Option "UseEDID" "False".


I still think the video card should be able to do a better job 24p -->60p than the display can do..but it depends on the post-decode shader program.
I don't know if this exists (yet)...

Stuttering:
It is possible that you are getting powermixer problems ..
Trying setting the powermixer to max performance as an expt..

---

