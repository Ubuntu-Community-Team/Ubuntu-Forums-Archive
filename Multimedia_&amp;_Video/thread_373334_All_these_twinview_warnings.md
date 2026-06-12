---
title: "All these twinview warnings"
date: 2007-03-01
forum: Multimedia &amp; Video
---

### Post by addisor on 2007-03-01
Hi guys, twinview is up and running in a fashion, but with all these Xorg.0.log warnings. Any ideas?

(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "UseEdidFreqs" "False"
(**) NVIDIA(0): Option "TwinView" "True"
(**) NVIDIA(0): Option "TwinViewOrientation" "RightOf"
(**) NVIDIA(0): Option "SecondMonitorHorizSync" "31.5-60.0"
(**) NVIDIA(0): Option "SecondMonitorVertRefresh" "50.0-60.0"
(**) NVIDIA(0): Option "MetaModes" "1280x768,1024x768;NULL,1280x768;1280x768,NULL"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
(**) NVIDIA(0):     disabled on all display devices.
(**) NVIDIA(0): TwinView enabled
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 6150 at PCI:0:5:0
(--) NVIDIA(0): VideoRAM: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.51.28.45.79
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6150 at PCI:0:5:0:
(--) NVIDIA(0):     @@@ LCD-15EX (CRT-0)
(--) NVIDIA(0):     YMH DPX-830 (DFP-0)
(--) NVIDIA(0): @@@ LCD-15EX (CRT-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(0): YMH DPX-830 (DFP-0): 310.0 MHz maximum pixel clock
(--) NVIDIA(0): YMH DPX-830 (DFP-0): Internal Dual Link TMDS
(WW) NVIDIA(0): Mode "1024x768" is too large for YMH DPX-830 (DFP-0);
(WW) NVIDIA(0):     discarding.
(WW) NVIDIA(0): Mode "1280x960" is too large for YMH DPX-830 (DFP-0);
(WW) NVIDIA(0):     discarding.
(WW) NVIDIA(0): Mode "1280x768" is too large for YMH DPX-830 (DFP-0);
(WW) NVIDIA(0):     discarding.
(WW) NVIDIA(0): Mode "1280x800" is too large for YMH DPX-830 (DFP-0);
(WW) NVIDIA(0):     discarding.
(WW) NVIDIA(0): Mode "1152x768" is too large for YMH DPX-830 (DFP-0);
(WW) NVIDIA(0):     discarding.
(WW) NVIDIA(0): Mode "1440x900" is too large for YMH DPX-830 (DFP-0);
(WW) NVIDIA(0):     discarding.
(WW) NVIDIA(0): Mode "1024x768" is too large for YMH DPX-830 (DFP-0);
(WW) NVIDIA(0):     discarding.
(WW) NVIDIA(0): Mode "1280x960" is too large for YMH DPX-830 (DFP-0);
(WW) NVIDIA(0):     discarding.
(II) NVIDIA(0): Assigned Display Devices: CRT-0, DFP-0
(WW) NVIDIA(0): No valid modes for "1280x768,1024x768"; removing.
(WW) NVIDIA(0): No valid modes for "NULL,1280x768"; removing.
(WW) NVIDIA(0): No valid modes for "1280x768,NULL"; removing.
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 2304 x 768
(WW) NVIDIA(0): No size information available in CRT-0's EDID; cannot compute
(WW) NVIDIA(0):     DPI from EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfb0

---

### Post by booe on 2007-03-02
Are you using the YAMAHA DPX-830 projector seen [here](http://www.yamaha.com/yec/products/productdetail.html?CNTID=200520&CTID=5001300&ATRID=1020&DETYP=ATTRIBUTE)?

The reason I ask is that it lists a maximum resolution of 1280x768 pixels with the other following specs:
Horizontal sync range: 15-80kHz
Vertical sync range: 50-85Hz (analog) | 60Hz/50Hz (digital)

So you *should* be able to get the full 1280x768 resolution, but you need to fix your xorg.conf file (located in /etc/X11/) first.

Please post the contents of your xorg.conf here, and confirm what graphics card and screen/monitor/projector/display you have connected to your computer. Then you can fix the config so that it has the correct resolutions, sync rates, bit depth, etc specified.

---

### Post by kerry_s on 2007-03-02
It's saying your display size is no good so it falls back to auto-select. It looks like it's falling to "1152x768, 1152x768".
What is the max resolution for both monitors?
You can try using panning to get the size since its a projector. Try->
"1152x768, 1152x768 @1280x768 " Panning allows you to pretend to be a different size.

---

### Post by addisor on 2007-03-02
Tried the panning metamode, same result. new post below with latest info

---

### Post by addisor on 2007-03-02
Here's my X11 that I generated after lots of playing by using nvidia config--twinview.

Section "Monitor"
    Identifier     "LCD-15EX"
    HorizSync       31.5 - 60.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA GeForce 6150"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA GeForce 6150"
    Monitor        "LCD-15EX"
    DefaultDepth    24
    Option         "UseFBDev" "true"
    Option         "TwinView" "True"
    Option         "TwinViewOrientation" "RightOf"
    Option         "UseEdidFreqs" "True"
    Option         "MetaModes" "1024x768, 1280x720; 1024x768, NULL"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768"
    EndSubSection
EndSection



My mobo is Abit M2-NF with onboard graphics using GeForce 6150 with a VGA and DVI out.

LCD (recognised as CRT) is 15" 1024x768 @60 or 75hz, horiz 31,5-60, vert 56-75 called LCD-15EX

Projector Ymaha DPX-830 can recognise 1280x768 but is programmed to recognise 1280x720 or 1024x768


Added a metamode and have found that I can swap between CRT and CRT/DFP combi by changing resolution in system,preferences,screen resolution. That's because ctrl alt + or - doesn't work. Heres my latest log

(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "UseEdidFreqs" "True"
(**) NVIDIA(0): Option "TwinView" "True"
(**) NVIDIA(0): Option "TwinViewOrientation" "RightOf"
(**) NVIDIA(0): Option "MetaModes" "1024x768, 1280x720; 1024x768, NULL"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
(**) NVIDIA(0):     enabled on all display devices.
(**) NVIDIA(0): TwinView enabled
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 6150 at PCI:0:5:0
(--) NVIDIA(0): VideoRAM: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.51.28.45.79
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6150 at PCI:0:5:0:
(--) NVIDIA(0):     @@@ LCD-15EX (CRT-0)
(--) NVIDIA(0):     YMH DPX-830 (DFP-0)
(--) NVIDIA(0): @@@ LCD-15EX (CRT-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(0): YMH DPX-830 (DFP-0): 310.0 MHz maximum pixel clock
(--) NVIDIA(0): YMH DPX-830 (DFP-0): Internal Dual Link TMDS
(WW) NVIDIA(0): Mode "1024x768" is too large for YMH DPX-830 (DFP-0);
(WW) NVIDIA(0):     discarding.
(WW) NVIDIA(0): Mode "1280x960" is too large for YMH DPX-830 (DFP-0);
(WW) NVIDIA(0):     discarding.
(WW) NVIDIA(0): Mode "1280x1024" is too large for YMH DPX-830 (DFP-0);
(WW) NVIDIA(0):     discarding.
(WW) NVIDIA(0): Mode "1280x768" is too large for YMH DPX-830 (DFP-0);
(WW) NVIDIA(0):     discarding.
(WW) NVIDIA(0): Mode "1280x800" is too large for YMH DPX-830 (DFP-0);
(WW) NVIDIA(0):     discarding.
(WW) NVIDIA(0): Mode "1152x768" is too large for YMH DPX-830 (DFP-0);
(WW) NVIDIA(0):     discarding.
(WW) NVIDIA(0): Mode "1440x900" is too large for YMH DPX-830 (DFP-0);
(WW) NVIDIA(0):     discarding.
(WW) NVIDIA(0): Mode "1600x1024" is too large for YMH DPX-830 (DFP-0);
(WW) NVIDIA(0):     discarding.
(WW) NVIDIA(0): Mode "1024x768" is too large for YMH DPX-830 (DFP-0);
(WW) NVIDIA(0):     discarding.
(WW) NVIDIA(0): Mode "1280x960" is too large for YMH DPX-830 (DFP-0);
(WW) NVIDIA(0):     discarding.
(WW) NVIDIA(0): Mode "1280x1024" is too large for YMH DPX-830 (DFP-0);
(WW) NVIDIA(0):     discarding.
(II) NVIDIA(0): Assigned Display Devices: CRT-0, DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1024x768,1280x720"
(II) NVIDIA(0):     "1024x768,NULL"
(II) NVIDIA(0): Virtual screen size determined to be 2304 x 768
(WW) NVIDIA(0): No size information available in CRT-0's EDID; cannot compute
(WW) NVIDIA(0):     DPI from EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:

Would just like to ensure projector is getting full 1280x720

---

