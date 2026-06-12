---
title: "NVIDIA optimus, ironhide , HDMI working suboptimal."
date: 2012-03-09
forum: Multimedia Software
---

### Post by Jarige on 2012-03-09
Well I need your help again. I've got an MSI GE620DX which has NVIDIA optimus. I've got Ironhide installed and working. Optirun starts an X Server without errors and the FPS of glxgears is higher with optirun.

Then I tried connecting my HDMI tv, which has support for 1080p (allthough it's not a FullHD tv). The usual display program in Ubuntu shows only 1280x720 (720p) as a resolution. So I tried that resolution and the screen on the tv is very greenish, but there's something showing. And there's some weird sound from the tv. All in all not very optimal.

I would like to get HDMI working at FullHD as it works in Windows (because it does work there, thank you for not supporting Optimus in Linux, NVIDIA -_-). Now I've heard that Ironhide and Bumblebee are working on HDMI support, but as I've got it working suboptimal, maybe the step to optimal isn't that big.

This is my xrandr output. I've got a FullHD resolution on my laptop.
```

Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
LVDS1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 345mm x 194mm
   1920x1080      59.9*+
   1680x1050      60.0     59.9  
   1600x1024      60.2  
   1400x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 connected (normal left inverted right x axis y axis)
   1280x720       60.0     50.0  
DP1 disconnected (normal left inverted right x axis y axis)

```

I do not have DisplayPort though, don't know why it shows up in the list.

I was just wondering, I could get it working suboptimal, maybe the optimal settings are just some config file editting away. Maybe by configuring xorg.conf or xorg.conf.nvidia?
Is there anyone who could help me achieve this?

---

### Post by BicyclerBoy on 2012-03-10
From the outset nVidia publicly stated that optimus was not supported in linux.
There must have been a lot of support added into windows codebase.
Commercial pressure will only work if people buy linux supported h/w & stop buying windows licences by proxy.

If the TV is not full-HD then mode 1280x720 is probably the best because it is the panel native resolution.
Check the EDID data reported in /var/log/Xorg.0.log..

Driving the panel at 1080 just requires the internal pre-scaler to re-scale to native.
The best solution is native panel resolution with direct pixel mapping.

The colour error could be due to full (0-255) v.s. limited colour (16-255) space setting in nvidia-settings.

---

### Post by Jarige on 2012-03-10
Thank you for your reply,

I know it's theoretically the best resolution, but it does accept a FullHD resolution in Windows, and I think the native resolution of the tv is still higher then 720p (more like 1600x900 or something close to that.
I will check and post the EDID in the logs tomorrow as the tv is now in use by my family and I'll be going to bed after that :)

I'd also like NVIDIA to give native support for Optimus on Linux, but now we just have to live with the current situation and hope for the best. I suspect Ironhide and Bumblebee to improve over time, but I just wanted some guidelines for trying things out. Checking the logs for EDID is a great start, I'll find out some more about EDID by looking it up on Wikipedia or something.

Thanks for now, I hope to reply again tomorrow :)

---

### Post by Jarige on 2012-03-11
Allright, I tried some things today. My family gave me a few minutes to gather a log file. I turned on my laptop, plugged in the tv. At this point, no reconfiguring happened, so I turned the tv output on by the Displays utility. Again, only 720p was available and it showed up greenish with the annoying weird sound. Then I unplugged the HDMI cable, waited a few seconds and replugged it. It remembered the config I made last time, greenish 720p with weird sounds. At this point, I copied /var/log/Xorg.0.log to my desktop. Then I used this command:
```

[*name*@*computer name* ~]$ cat Desktop/Xorg.0.log | grep intel
[    27.568] (==) Matched intel as autoconfigured driver 0
[    27.568] (II) LoadModule: "intel"
[    27.569] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    27.570] (II) Module intel: vendor="X.Org Foundation"
[    27.571] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
[    27.575] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    27.577] (II) intel(0): Creating default Display subsection in Screen section
[    27.577] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    27.577] (==) intel(0): RGB weight 888
[    27.577] (==) intel(0): Default visual is TrueColor
[    27.577] (II) intel(0): Integrated Graphics Chipset: Intel(R) Sandybridge Mobile (GT2)
[    27.577] (--) intel(0): Chipset: "Sandybridge Mobile (GT2)"
[    27.577] (**) intel(0): Relaxed fencing enabled
[    27.577] (**) intel(0): Wait on SwapBuffers? enabled
[    27.577] (**) intel(0): Triple buffering? enabled
[    27.577] (**) intel(0): Framebuffer tiled
[    27.577] (**) intel(0): Pixmaps tiled
[    27.577] (**) intel(0): 3D buffers tiled
[    27.577] (**) intel(0): SwapBuffers wait enabled
[    27.577] (==) intel(0): video overlay key set to 0x101fe
[    27.577] (II) intel(0): Output LVDS1 has no monitor section
[    27.577] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video1
[    27.577] (II) intel(0): Output VGA1 has no monitor section
[    27.607] (II) intel(0): Output HDMI1 has no monitor section
[    27.656] (II) intel(0): Output DP1 has no monitor section
[    27.656] (II) intel(0): EDID for output LVDS1
[    27.656] (II) intel(0): Manufacturer: LGD  Model: 1e9  Serial#: 0
[    27.656] (II) intel(0): Year: 2009  Week: 0
[    27.656] (II) intel(0): EDID Version: 1.3
[    27.656] (II) intel(0): Digital Display Input
[    27.656] (II) intel(0): Max Image Size [cm]: horiz.: 35  vert.: 19
[    27.656] (II) intel(0): Gamma: 2.20
[    27.656] (II) intel(0): No DPMS capabilities specified
[    27.656] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    27.656] (II) intel(0): First detailed timing is preferred mode
[    27.656] (II) intel(0): redX: 0.621 redY: 0.352   greenX: 0.314 greenY: 0.586
[    27.656] (II) intel(0): blueX: 0.147 blueY: 0.118   whiteX: 0.313 whiteY: 0.329
[    27.656] (II) intel(0): Manufacturer's mask: 0
[    27.656] (II) intel(0): Supported detailed timing:
[    27.656] (II) intel(0): clock: 138.5 MHz   Image Size:  345 x 194 mm
[    27.656] (II) intel(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
[    27.656] (II) intel(0): v_active: 1080  v_sync: 1083  v_sync_end 1088 v_blanking: 1111 v_border: 0
[    27.656] (II) intel(0):  LG Display
[    27.656] (II) intel(0):  LP156WF1-TLC1
[    27.656] (II) intel(0): EDID (in hex):
[    27.656] (II) intel(0): 	00ffffffffffff0030e4e90100000000
[    27.657] (II) intel(0): 	00130103802313780a08d59f5a509625
[    27.657] (II) intel(0): 	1e505400000001010101010101010101
[    27.657] (II) intel(0): 	0101010101011a3680a070381f403020
[    27.657] (II) intel(0): 	350059c2100000190000000000000000
[    27.657] (II) intel(0): 	00000000000000000000000000fe004c
[    27.657] (II) intel(0): 	4720446973706c61790a2020000000fe
[    27.657] (II) intel(0): 	004c503135365746312d544c433100b0
[    27.657] (II) intel(0): EDID vendor "LGD", prod id 489
[    27.657] (II) intel(0): Printing DDC gathered Modelines:
[    27.657] (II) intel(0): Modeline "1920x1080"x0.0  138.50  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (66.6 kHz)
[    27.657] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    27.657] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    27.657] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    27.657] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    27.657] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    27.658] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    27.658] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    27.658] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    27.658] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    27.658] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    27.658] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    27.658] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    27.658] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    27.658] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    27.658] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    27.658] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    27.658] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    27.658] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    27.658] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    27.658] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    27.658] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    27.658] (II) intel(0): Printing probed modes for output LVDS1
[    27.658] (II) intel(0): Modeline "1920x1080"x59.9  138.50  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (66.6 kHz)
[    27.658] (II) intel(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    27.658] (II) intel(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    27.658] (II) intel(0): Modeline "1600x1024"x60.2  103.12  1600 1600 1656 1664  1024 1024 1029 1030 +hsync +vsync (62.0 kHz)
[    27.658] (II) intel(0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz)
[    27.658] (II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    27.658] (II) intel(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    27.658] (II) intel(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    27.658] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    27.658] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz)
[    27.658] (II) intel(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
[    27.658] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    27.658] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    27.658] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    27.658] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    27.658] (II) intel(0): EDID for output VGA1
[    27.682] (II) intel(0): EDID for output HDMI1
[    27.728] (II) intel(0): EDID for output DP1
[    27.728] (II) intel(0): Output LVDS1 connected
[    27.728] (II) intel(0): Output VGA1 disconnected
[    27.728] (II) intel(0): Output HDMI1 disconnected
[    27.728] (II) intel(0): Output DP1 disconnected
[    27.728] (II) intel(0): Using exact sizes for initial modes
[    27.728] (II) intel(0): Output LVDS1 using initial mode 1920x1080
[    27.728] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    27.728] (II) intel(0): Kernel page flipping support detected, enabling
[    27.728] (**) intel(0): Display dimensions: (350, 190) mm
[    27.728] (**) intel(0): DPI set to (139, 144)
[    27.729] (II) intel(0): [DRI2] Setup complete
[    27.730] (II) intel(0): [DRI2]   DRI driver: i965
[    27.730] (II) intel(0): Allocated new frame buffer 1920x1080 stride 7680, tiled
[    27.732] (==) intel(0): Backing store disabled
[    27.732] (==) intel(0): Silken mouse enabled
[    27.732] (II) intel(0): Initializing HW Cursor
[    27.808] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    27.860] (==) intel(0): DPMS enabled
[    27.860] (==) intel(0): Intel XvMC decoder enabled
[    27.860] (II) intel(0): Set up textured video
[    27.860] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    27.860] (II) intel(0): direct rendering: DRI2 Enabled
[    27.860] (==) intel(0): hotplug detection: "enabled"
[    27.884] (II) intel(0): Setting screen physical size to 508 x 285
[    29.825] (II) intel(0): EDID vendor "LGD", prod id 489
[    29.826] (II) intel(0): Printing DDC gathered Modelines:
[    29.826] (II) intel(0): Modeline "1920x1080"x0.0  138.50  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (66.6 kHz)
[    31.219] (II) intel(0): EDID vendor "LGD", prod id 489
[    31.219] (II) intel(0): Printing DDC gathered Modelines:
[    31.219] (II) intel(0): Modeline "1920x1080"x0.0  138.50  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (66.6 kHz)
[    39.624] (II) intel(0): EDID vendor "LGD", prod id 489
[    39.624] (II) intel(0): Printing DDC gathered Modelines:
[    39.624] (II) intel(0): Modeline "1920x1080"x0.0  138.50  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (66.6 kHz)
[    40.103] (II) intel(0): EDID vendor "LGD", prod id 489
[    40.103] (II) intel(0): Printing DDC gathered Modelines:
[    40.103] (II) intel(0): Modeline "1920x1080"x0.0  138.50  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (66.6 kHz)
[    40.221] (II) intel(0): EDID vendor "LGD", prod id 489
[    40.221] (II) intel(0): Printing DDC gathered Modelines:
[    40.221] (II) intel(0): Modeline "1920x1080"x0.0  138.50  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (66.6 kHz)
[    40.736] (II) intel(0): EDID vendor "LGD", prod id 489
[    40.736] (II) intel(0): Printing DDC gathered Modelines:
[    40.737] (II) intel(0): Modeline "1920x1080"x0.0  138.50  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (66.6 kHz)
[    62.292] (II) intel(0): EDID vendor "LGD", prod id 489
[    62.292] (II) intel(0): Printing DDC gathered Modelines:
[    62.292] (II) intel(0): Modeline "1920x1080"x0.0  138.50  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (66.6 kHz)
[   295.072] (II) intel(0): EDID vendor "LGD", prod id 489
[   295.072] (II) intel(0): Printing DDC gathered Modelines:
[   295.072] (II) intel(0): Modeline "1920x1080"x0.0  138.50  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (66.6 kHz)
[   304.142] (II) intel(0): EDID vendor "LGD", prod id 489
[   304.142] (II) intel(0): Printing DDC gathered Modelines:
[   304.142] (II) intel(0): Modeline "1920x1080"x0.0  138.50  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (66.6 kHz)
[   304.745] (II) intel(0): Allocated new frame buffer 3200x1080 stride 12800, tiled
[   354.588] (II) intel(0): EDID vendor "LGD", prod id 489
[   354.588] (II) intel(0): Printing DDC gathered Modelines:
[   354.588] (II) intel(0): Modeline "1920x1080"x0.0  138.50  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (66.6 kHz)
[   355.147] (II) intel(0): Allocated new frame buffer 1920x1080 stride 7680, tiled
[   367.140] (II) intel(0): EDID vendor "LGD", prod id 489
[   367.140] (II) intel(0): Printing DDC gathered Modelines:
[   367.140] (II) intel(0): Modeline "1920x1080"x0.0  138.50  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (66.6 kHz)
[   367.884] (II) intel(0): Allocated new frame buffer 3200x1080 stride 12800, tiled

```

The weird thing here is that I do not see any reference to a 720p resolution. The FullHD resolution mentioned for the LGD I assume to be my laptop monitor.

I'll check on the color settings later, probably tommorow again. My family doesn't seem to be very fond of me messing around with the tv ;)

Thanks, hopefully this will help me some more (allthough it doesn't look that way).

EDIT: I have an NVIDIA GeForce GT 555M

---

### Post by BicyclerBoy on 2012-03-11
So your desktop colour/noise is when running the intel X server.
The sandybridge GPU is still work-in-progress..
Are you using xorg-edgers ppa for the updated intel driver?
The ironhide readme mentions using xorg-edgers.

I've never had to use ironhide so am probably just wasting your time..
What does the colour-space & range look like when you launch a video player or nvidia-settings with optirun or the ironhide applet?

Would be interesting to see the last 20 lines of output of:
dmesg
when you plug in ext monitor & run optirun smplayer.
Curious how the hdmi ELD will work..

---

### Post by Jarige on 2012-03-11
> Are you using xorg-edgers ppa for the updated intel driver?
No, not yet. I know it was recommended, but I've managed to get it working without those. Do you recommend me to update to that? I know I can always revert back if needed (I know how to do that, or at least I can find out how to do that).

> Would be interesting to see the last 20 lines of output of:
dmesg
when you plug in ext monitor & run optirun smplayer.
I tried vlc as I do not have smplayer. I runned it using optirun vlc, it started, I moved it to the external screen and it turned up green just like the rest of the screen.
dmesg outputs nothing of interest. Just some stuff related to my wireless card reconnecting after a suspend. Nothing about connecting an HDMI cable. So I disconnected the cable and connected it again, then ran dmesg and got this relevant output on dmesg:
```

[ 2202.488099] Raw EDID:
[ 2202.488106] <3>00 ff ff ff ff ff ff 00 2a c3 8b 20 01 01 01 01  ........*.. ....
[ 2202.488111] <3>00 0f 01 03 80 3a 20 78 2a 7c 11 9e 59 47 9b 27  .....: x*|..YG.'
[ 2202.488116] <3>10 50 54 00 01 ff ff ff ff ff ff ff ff ff ff ff  .PT.............
[ 2202.488121] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[ 2202.488126] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[ 2202.488131] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[ 2202.488136] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[ 2202.488140] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[ 2202.488144] 

```

This seems to be very usefull? The wiki page on EDID shows exactly how to decode such a message so I'll get working on that immediately. Don't know how much work that'll cost, never did such a thing. Probably gonna try and find a little script or program that does the work for me ;)

Thanks for your help until now :) Do you think updating Xorg to edgers will work?

---

### Post by Jarige on 2012-03-11
I managed to get a little extra information by using this great open source PHP script I've found on the internet:

```

Extracted contents:
header:          d3 47 df 7d f7 df 7d f7
serial number:   df 7d fd 34 d9 a7 37 f1 bd b4
version:         d3 5d
basic params:    35 d3 5d 35 d3
chroma info:     4d 1f d3 5d 37 f3 4d da db 4e
established:     fc d9 ae
standard:        dc d7 5f 5e e7 de 3b f5 bd bb d7 4e 74 e7 8d 34
descriptor 1:    d3 57 df 7d f7 df 7d f7 df 7d f7 df 7d f7 df 7d f7 df
descriptor 2:    7d f7 df 7d f7 df 7d f7 df 7d f7 df 7d f7 df 7d f7 df
descriptor 3:    7d f7 df 7d f7 df 7d f7 df 7d f7 df 7d f7 df 7d f7 df
descriptor 4:    7d f7 df 7d f7 df 7d f7 df 7d f7 df 7d f7 df 7d f7 df
extensions:      7d
checksum:        f7

```
Link to the scripts (also includes some more stuff including C code, I haven't tried that) is right here: [https://github.com/claar/php-edid-decode]("https://github.com/claar/php-edid-decode").

I'll go check out some stuff about this EDID code, I'll post back whatever I find. I'm not able to try the tv anymore for at least 10 hours from now.

---

### Post by Jarige on 2012-03-11
It seems that the earlier extracted contents wheren't correct. I've managed to get the PHP script working better after encoding my hex string into base64. Now I got this:
```

Extracted contents:
header:          00 ff ff ff ff ff ff 00
serial number:   2a c3 8b 20 01 01 01 01 00 0f
version:         01 03
basic params:    80 3a 20 78 2a
chroma info:     7c 11 9e 59 47 9b 27 10 50 54
established:     00 01 ff
standard:        ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
descriptor 1:    ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
descriptor 2:    ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
descriptor 3:    ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
descriptor 4:    ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
extensions:      ff
checksum:        ff

Manufacturer: JVC Model 208b Serial Number 16843009
EDID version: 1.3
Digital display
Maximum image size: 58 cm x 32 cm
Gamma: 2.20
DPMS levels: Off
Supported color formats: RGB 4:4:4, YCrCb 4:2:2
First detailed timing is preferred timing
Established timings supported:
  1280x1024@75Hz
  1152x870@75Hz
Standard timings supported:
  2288x1372.8@123Hz
  2288x1372.8@123Hz
  2288x1372.8@123Hz
  2288x1372.8@123Hz
  2288x1372.8@123Hz
  2288x1372.8@123Hz
  2288x1372.8@123Hz
  2288x1372.8@123Hz
Detailed mode: Clock 655.350 MHz, 4095 mm x 4095 mm
               4095 5118 6141 8190 hborder 255
               4095 4158 4221 8190 vborder 255
               +hsync +vsync interlaced
Detailed mode: Clock 655.350 MHz, 4095 mm x 4095 mm
               4095 5118 6141 8190 hborder 255
               4095 4158 4221 8190 vborder 255
               +hsync +vsync interlaced
Detailed mode: Clock 655.350 MHz, 4095 mm x 4095 mm
               4095 5118 6141 8190 hborder 255
               4095 4158 4221 8190 vborder 255
               +hsync +vsync interlaced
Detailed mode: Clock 655.350 MHz, 4095 mm x 4095 mm
               4095 5118 6141 8190 hborder 255
               4095 4158 4221 8190 vborder 255
               +hsync +vsync interlaced
Has 255 extension blocks
Checksum: 0xff (should be 0xf3)
EDID block does NOT conform to EDID 1.3!
	Missing name descriptor
	Missing monitor ranges
EDID block does not conform at all!
	Block has broken checksum
	Bad year of manufacture

```

I'll keep on searching, but this shows that the EDID code received isn't a correct code as the checksum isn't correct and apparently it doesn't conform to EDID 1.3. Weird. I haven't had any problems with this in Windows (allthough I wouldn't know how to get an EDID code from there).

---

### Post by Jarige on 2012-03-11
My earlier statements about the tv supporting 1080p are incorrect. It only supports 1080i as far as I know. 
And to clarify this: I do not know if the script correctly states that the EDID code is incorrect. But the shown results of the script aren't very close to what I assume it's supposed to be even though it does recognise the brand correctly (JVC).

I now remember that I was in a friend's house, and connected my laptop to the tv in his house (1080p) using Ubuntu and it just connected flawlessly. No weird things happening at all, just needed to change some settings on the tv. In other words, it should be possible.

---

### Post by BicyclerBoy on 2012-03-11
The EDID decoding script is likely incorrect, the extracted info from standard timing on is nonsense.
But this seems like an interesting distraction..

Your problem seems to occur with the intel driver & your iCPU/iGPU graphics, it has little or nothing to do with nVidia or optimus.

If the intel part was working well you could just forget the nVidia GPU; just leave it switched off.

The output from dmesg could have had info about snd-hda-intel.

When you read the freedesktop.org/intel-glx mailing lists, you realise that the intel kernel driver (SNA, INL + old) is under constant improvement.
There have been recent patches to properly support interlaced modes etc.
But these changes will only hit kernel 3.3 or 3.4..so 1-2 years from *buntu 12.04..

xorg-edgers only updates the user-space driver & not the kernel module.

Does your laptop have VGA or DVI-I (with analogue) ? Because it is possible the interlaced VGA output works.

As a note:
The video over VGA is always analogue RGB encoded. TVs used limited or reduced range. computers use(d) full range.
Video over DVI/HDMI/DP can be YUV/RGB-full/RGB-limited (& deep-colour). Arguably YUV colour-space is best for video/photos.
The wrong colour-space causes crushed blacks &/or totally wrong colours..

---

### Post by Jarige on 2012-03-11
VGA probably works on the tv, I haven't tried. But I use an other older non-hdmi monitor together using VGA with this laptop and that works flawlessly. I do not have DVI though. I cannot say whether I'm using an interlaced mode though, I do not have enough knowledge yet to find out or guess that :)

The weird thing is that it did work a few weeks ago, on my friend's TV, which did actually support 1080p. It showed up quite nicely indeed :)
I seem to have mentioned two tv's and in my previous comment mentioned 'the' tv having 1080i instead of 1080p. By 'the' I meant my tv. Connectioning to my friend's tv worked flawlessly.

But you think it has got something to do with the Intel kernel module not supporting an interlaced mode?

And I've noticed that I could get higher resolutions using HDMI from the tv then using the VGA input. That does make some sense to me, but I've only realised that some months ago, using Windows. Now that I (finally) have Ubuntu again it failed on me.

---

### Post by BicyclerBoy on 2012-03-12
I have read that the intel kernel driver has serious problems with interlaced modes unless the TV/VGA video is generated by external support IC.

Digital monitors  & TVs have input prescalers.
The different inputs have diff limits/requirements.
VGA is not HDCP so full HD is not supported.
The VGA input is normally limited to std video modes & excludes native.

---

