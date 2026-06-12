---
title: "Force screen resolution to 1920x1080_60i"
date: 2008-01-07
forum: Multimedia &amp; Video
---

### Post by Kjella on 2008-01-07
What is required to FORCE xorg into using a graphics mode? I'm trying to go crazy getting a 42" LCD TV to work under Linux, it works in both 1080i60 and 720p60 under Windows. Under Linux, no matter what I try, it either doesn't recognize the signal OR displays in 640x480/50Hz. Apparently it returns those refresh rates if you try to autodetect the monitor.

Now, my problem is that I've tried every configuration option I can possibly find to disable EDID and any other way it's trying to be "smart", I've tried manually adding modelines and modes and yet it seems that most of the time it's completely ignoring me anyway. Why oh WHY does it put my screen in a mode that's nowhere in xorg.conf or anywhere else I can find? This is really driving me crazy.

Does anyone have a sample xorg.conf file that'll ONLY do exactly as told? Also, since my TV is shutting down when the signal isn't vald, is there a way to see what X11 was trying to do?

---

### Post by Kjella on 2008-01-08
Maybe I should add some useful information as well, since yesterday I was mostly venting. Basicly, no matter what I do every mode is ignored. From /var/log/Xorg.0.log:

(II) NVIDIA(0): Mode Validation Overrides for DFP-1:
(II) NVIDIA(0):     AllowNon60HzDFPModes
(II) NVIDIA(0):     NoMaxPClkCheck
(II) NVIDIA(0):     NoEdidMaxPClkCheck
(II) NVIDIA(0):     AllowInterlacedModes
(II) NVIDIA(0):     NoMaxSizeCheck
(II) NVIDIA(0):     NoHorizSyncCheck
(II) NVIDIA(0):     NoVertRefreshCheck
(II) NVIDIA(0):     NoVesaModes
(II) NVIDIA(0):     NoEdidModes
(II) NVIDIA(0):     NoWidthAlignmentCheck
(II) NVIDIA(0):     NoDFPNativeResolutionCheck
(II) NVIDIA(0):     NoVirtualSizeCheck
(II) NVIDIA(0): Assigned Display Device: DFP-1
(WW) NVIDIA(0): No valid modes for "1920x1080"; removing.
(WW) NVIDIA(0): No valid modes for "1280x720_60.00"; removing.
(WW) NVIDIA(0): No valid modes for "1280x720_59.94"; removing.
(WW) NVIDIA(0): No valid modes for "1280x720_60"; removing.
(WW) NVIDIA(0): No valid modes for "1280x720"; removing.
(WW) NVIDIA(0):
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".

Now, this is a mix of standard resolutions, custom modelines, things that should be in the nVidia modepool and absolutely none of it works. Before I disabled vesa modes, it would remove any of those as well. The EDID information on this screen is junk, so I can't use it. It says so itself when it's enabled:

(WW) NVIDIA(GPU-0): The EDID read for display device DFP-1 is invalid: EDID
(WW) NVIDIA(GPU-0):     version 1 extension exceeds EDID buffer size, or checks$
(WW) NVIDIA(GPU-0):     for EDID extension failed.

So I have to configure it manually. But for the love of ..., it doesn't seem to let me.

---

### Post by Kjella on 2008-01-08
Ok, learning to log more verbosely (-logverbose 6) I learned the following:

(II) NVIDIA(0): --- Building ModePool for DFP-1 ---
(II) NVIDIA(0):
(II) NVIDIA(0): Native backend timings for DFP-1:
(II) NVIDIA(0):   640 x 480 @ 60 Hz
(II) NVIDIA(0):     Pixel Clock      : 25.18 MHz
(II) NVIDIA(0):     HRes, HSyncStart :  640,  656
(II) NVIDIA(0):     HSyncEnd, HTotal :  752,  800
(II) NVIDIA(0):     VRes, VSyncStart :  480,  490
(II) NVIDIA(0):     VSyncEnd, VTotal :  492,  525
(II) NVIDIA(0):     H/V Polarity     : +/+
(II) NVIDIA(0):
(II) NVIDIA(0):   Validating Mode "1280x720_60.00":
(II) NVIDIA(0):     1280 x 720 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Configuration file ModeLine
(II) NVIDIA(0):        Pixel Clock      : 74.48 MHz
(II) NVIDIA(0):        HRes, HSyncStart : 1280, 1336
(II) NVIDIA(0):        HSyncEnd, HTotal : 1472, 1664
II) NVIDIA(0):     VRes, VSyncStart :  480,  490
(II) NVIDIA(0):     VSyncEnd, VTotal :  492,  525
(II) NVIDIA(0):     H/V Polarity     : +/+
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0):
(WW) NVIDIA(0): Unable to use mode "1280x720_60.00" for DFP-1; cannot compute
(WW) NVIDIA(0):     backend DFP timings (mode is larger than native backend
(WW) NVIDIA(0):     640 x 480).

So a major WTF here, for some reason the nvidia driver thinks my panel is 640x480. Now, tired with the nvidia driver and seeing a few posts on google that it might be related to that driver, I try the nv driver:

II) NV(0): EDID for output DVI0
(II) NV(0): Manufacturer: ANO  Model: 100  Serial#: 16843009
(II) NV(0): Year: 2005  Week: 24
(II) NV(0): EDID Version: 1.3
(II) NV(0): Digital Display Input
(II) NV(0): Max H-Image Size [cm]: horiz.: 80  vert.: 45
(II) NV(0): Gamma: 2.20
(II) NV(0): No DPMS capabilities specified; RGB/Color Display
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.625 redY: 0.340   greenX: 0.280 greenY: 0.595
(II) NV(0): blueX: 0.155 blueY: 0.070   whiteX: 0.283 whiteY: 0.298
(II) NV(0): Manufacturer: ANO  Model: 100  Serial#: 16843009
(II) NV(0): Year: 2005  Week: 24
(II) NV(0): EDID Version: 1.3
(II) NV(0): Digital Display Input
(II) NV(0): Max H-Image Size [cm]: horiz.: 80  vert.: 45
(II) NV(0): Gamma: 2.20
(II) NV(0): No DPMS capabilities specified; RGB/Color Display
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.625 redY: 0.340   greenX: 0.280 greenY: 0.595
(II) NV(0): blueX: 0.155 blueY: 0.070   whiteX: 0.283 whiteY: 0.298
(II) NV(0): Supported VESA Video Modes:
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@72Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@72Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported Future Video Modes:
(II) NV(0): #0: hsize: 1152  vsize 864  refresh: 60  vid: 16497
(II) NV(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) NV(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #3: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 74.2 MHz   Image Size:  708 x 398 mm
(II) NV(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_bo$
(II) NV(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border$
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 74.2 MHz   Image Size:  708 x 398 mm
(II) NV(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_bo$
(II) NV(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border$
(II) NV(0): Monitor name: AMOI-LCD TV
(II) NV(0): Ranges: V min: 49  V max: 61 Hz, H min: 15  H max: 46 kHz, PixClock

Suddenly EDID is alright, it appears the nvidia driver just can't read it. Now, this actually boots my screen into 1280x720p60. However, 1920x1080i60 doesn't work, instead I get a wierd 1920x540 mode (as you can see by the latest h_active: 1920, v_active: 540 modeline). Now, can I disable EDID with the nv driver? At least not with Option "UseEDID" "FALSE" as I did on the nvidia driver. And now it's treating any modelines I add as thin air - they're not even mentioned in Xorg.0.log.

So my conclusion? The X configuration in Linux is a piece of crap. Adding what you know is right is a major pain in the [beep], and the [beep] options aren't the [beep]ing same across drivers even though it's clearly a generic option, and I never even got as far as thinking about setting this up as two screens. These are things that WORK OUT OF THE BOX IN WINDOWS AND HAS DONE SO SINCE WINDOWS 2000!!!! :mad::mad::mad::mad: I just needed to get that out of my system, sigh. 

I'm settling on getting 1280x720 on nv driver out of this system. I've spent something like two days now trying to get this to work and it's just not worth it. I guess it also means this TV is useless under Linux once I get my regular monitor back from service and return to the nvidia driver (for the acceleration). In Windows, I had a nice dual setup using the PC to play movies with on the TV. Good thing I can still dual boot, but I was hoping not to.

---

