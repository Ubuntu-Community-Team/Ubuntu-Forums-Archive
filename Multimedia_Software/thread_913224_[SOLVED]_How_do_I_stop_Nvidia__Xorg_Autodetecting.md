---
title: "[SOLVED] How do I stop Nvidia / Xorg Autodetecting?"
date: 2008-09-07
forum: Multimedia Software
---

### Post by SiHa on 2008-09-07
Hi, I wonder if someone can help?


I'm using Mythbuntu 8.04.1, with Nvidia FX5200, using DVI-out for my LCD TV. If the TV is switched on when the box boots, the card detects and squirts everything out the DVI port.
But if the TV is not on, it all goes to the VGA and I have no option but to 'ESC, Down, Down, Enter' to tell MythTV to reboot, after turning the TV on, of course.

Can I edit my Xorg (or do something in nVidia-Setings) to force the box to use the DVI port even if it thinks nothing is there? Or should I try a different route and enable Twinview, so that it sends it all out of both? I've steered away from the twinview option so far, because last time I attemped that (on the backend box) I broke my Xorg.conf and being a very new Linux user at the time it took a while to restore.

TIA

SiHa

---

### Post by Thanh-BKK on 2008-09-08
Hi :)

I've got a similar problem and am seeking for the same solution, i.e. "how to tell xorg once and for all that i am using *such and such* graphic card and *such and such* monitor.

Reason: I gave up on getting TV-out to work (Nvidia) in the correct resolutions - either the image is too large for the TV or crappy resolution on the LCD monitor (twin view/"clone", as nothing else works).

So i got me a little hardware gadget - hook that to the PC and it sends the same signal to the monitor and to the TV, with some auto-corrections for the TV to make it compliant (can set resolution, width, height etc manually on that device extra for the TV, but even all by itself it does a perfect job). 

However when i BOOT my Ubuntu, monitor ON, i get only 640x480 on the monitor because Ubuntu "can't find the graphics card and monitor". 

Now i've gotten me a SECOND hardware gadget to solve that problem - a 1-to-2 VGA splitter, of which  i connect one of the outputs to the monitor and the other to that TV thingy. THIS works - almost perfect, only "almost" because the thingy has an amplifier that can't be turned off or regulated and as a result i get a little "ghosting" on the LCD (the thing is made for cable lengths up to 60 meters while i have only 1.5 meters, adding a 15 meters extension was a waste of money as it still "ghosts" AND, AGAIN, won't detect the monitor upon boot). 

Plus, having the two of them sucking electricity all the time is a waste, too, as i rarely use the TV but am too lazy to re-wire the whol;e shabang every time i DO use it!

So please, if anyone knows how to stop this "auto detecting" upon boot, i would be very happy to know it, too :)

Best regards.....

Thanh

---

### Post by cbstryker on 2008-09-08
I'm having a similar problem here. I can install the nvidia drivers fine, and everything works great until I reboot at which time my system loads upto the cannot detect video card box at 800x600 res. I then have to reinstall the nvidia drivers again.

Anyone know a solution?

---

### Post by SiHa on 2008-09-10
Well, I'm going to try a hardware fix. The DVI spec calls for a pin called 'Hot Plug Detect' on pin 16. A connected monitor must drive this pin to a voltage greater than 2.4V to indicate it is present.

So, I'm going to solder a 10K resistor between 16 & 14 (+5V) on the card, this will generate a logic 'high' and hopefully fool the card into thinking the TV is on - even if it isn't. 

Watch this space - I'll report back in a couple of days.

---

### Post by SiHa on 2008-09-28
Oh well, hardwiring 'Hotplug Detect' to +5V doesn't work. If the TV is off, the system still boots to VGA, instead of DVI.

Anyone have any ideas?

---

### Post by SiHa on 2008-09-29
OK, I've managed to force the box to output to the DVI regardless, by adding```
Option "ConnectedMonitor" "DFP" 
``` line to the screen section of xorg.conf I've removed all other modes as well, otherwise the system would incorrectly set the resolution to 1920x1080 if it booted while the TV was on.

But if it boots when the TV is off, I get an error "No valid modes for "1280x720"; removing" in my Xorg.0.log and it falls back to nvidia-auto-select, and sets the screen to 640x480.

Here's the relevant bit from my xorg.conf:
```
Section "Monitor"
    Identifier     "Generic Monitor"
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Panasonic-TV"
    HorizSync       15.0 - 68.0
    VertRefresh     23.0 - 61.0
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
    Option         "DPI" "100x100"
    Option         "UseEvents" "1"
    Option         "AddARGBVisuals" "1"
    Option         "AddARGBGLXVisuals" "1"
    Option         "NoLogo" "1"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
EndSection

[COLOR="Red"]Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "ConnectedMonitor" "DFP"
    SubSection     "Display"
        Depth       24
        Modes      "1280x720"
    EndSubSection
#    Option         "metamodes" "DFP: 1280x720 +0+0; DFP: 720x480 +0+0; DFP: 800x600 +0+0; DFP: 640x480 +0+0"
 
EndSection[/COLOR]
```

and from /var/log/Xorg.0.log:```
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "ConnectedMonitor" "DFP"
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): ConnectedMonitor string: "DFP"
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(WW) NVIDIA(GPU-0): Unable to read EDID for display device DFP-0
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5200 (NV34) at PCI:2:10:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 04.34.20.56.00
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5200 at PCI:2:10:0:
(--) NVIDIA(0):     DFP-0
(--) NVIDIA(0): DFP-0: 135.0 MHz maximum pixel clock
(--) NVIDIA(0): DFP-0: Internal Single Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
[COLOR="Red"](WW) NVIDIA(0): No valid modes for "1280x720"; removing.
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 640 x 480[/COLOR]
(++) NVIDIA(0): DPI set to (100, 100); computed from -dpi X commandline option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:

```

The "No valid modes defined" I guess is the clue, but what to do about it? I'm guessing I need to add a custom modeline, but not sure what values to use.

Any help appreciated, this is the last nittle niggle in a 2-3 month struggle to get a working mythtv setup with multiple machines. It's not the end of the world, I can just use suspend now I have that working OK, but I like things neat & tidy.

---

### Post by SiHa on 2008-10-01
Finally it is solved.
For anyone who wants to know:

Option "ConnectedMonitor" "DFP" in the screen section of xorg.conf forces the card to use the DVI output regardless of which output it has detected (if any) is connected.

Now you need to tell it what timings to use when it can't get them via EDID.

Boot with the TV on, so that the timings are correctly detected, run:```
xvidtune
``` and press the 'Show' button. Exit if it deosn't do so automatically. The first line displayed after slecting 'Show' should be a modeline like this:
**modeline        "1280x720@60" 74.25 1280 1390 1430 1650 720 725 730 750 +hsync +vsync**
Copy the above line into the 'monitor' section of xorg.conf thus:
```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Panasonic-TV"
    HorizSync       15.0 - 68.0
    VertRefresh     23.0 - 61.0
    modeline        "1280x720@60" 74.25 1280 1390 1430 1650 720 725 730 750 +hsync +vsync
EndSection
```

**NOTE** I had to do it this way, because the modelines generated by the online generators were different from the one detected and gave me a whacky interlaced effect

In the 'display' subsection of 'screen' I deleted all the listed modes and replaced with "1280x720@60" to match the one declared above.

Option "ExactModeTimingsDVI" "True" in the screen section tells it to ignore the fact that it can't get any EDID info because the TV is turned off, and just do what it's damn well told!

Now 'screen' looks like:
```
Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth   24 
    Option         "TwinView" "0"
    Option         "ConnectedMonitor" "DFP"
    Option         "ExactModeTimingsDVI" "TRUE"
    SubSection     "Display"
        Depth      24
        Modes      "1280x720@60"
    EndSubSection
 EndSection
```

I also commented out the "Default Screen" section, but I'm not sure that has any effect as the ConnectedMonitor statement should override this anyway.

So now the system boots to the correct resolution regardless of the power-on state of the TV!

Hope this helps someone else!

---

### Post by aymerickl on 2010-05-13
Thanks SiHa, it works!

But it seems that, when I boot with the TV off, the sound doesn't work.

Did anyone have any similar experience?

Aymerick

---

