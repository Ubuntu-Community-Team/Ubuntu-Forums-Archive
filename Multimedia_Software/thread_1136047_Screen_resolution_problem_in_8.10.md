---
title: "Screen resolution problem in 8.10"
date: 2009-04-24
forum: Multimedia Software
---

### Post by StanBaker on 2009-04-24
I am pretty new at the Ubuntu thing, as most of my machines are opensuse.  However, this is a special case and for this I chose Ubuntu.

I am connecting a machine via the VGA connector on my HDTV, but it won't go beyond 800x600, and editing the Xorg.conf file doesn't seem to do anything at all.

My TV can handle most standard monitor resolutions at either 60 or 120 Hz refresh rates.  But below is the probe output in my xorg.0.log:

---

(II) CHROME(0): Configured Monitor: Using default hsync range of 31.50-37.90 kHz
(II) CHROME(0): Configured Monitor: Using default vrefresh range of 50.00-70.00 Hz
(WW) CHROME(0): Unable to estimate virtual size
(II) CHROME(0): Clock range:  20.00 to 230.00 MHz
(II) CHROME(0): ViaValidMode: Validating 640x350 (31500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "640x350" (vrefresh out of range)
(II) CHROME(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 640x400 (31500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "640x400" (vrefresh out of range)
(II) CHROME(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 720x400 (35500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "720x400" (vrefresh out of range)
(II) CHROME(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 640x480 (25175)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 640x480 (31500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "640x480" (vrefresh out of range)
(II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 640x480 (31500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "640x480" (vrefresh out of range)
(II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 640x480 (36000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "640x480" (hsync out of range)
(II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 800x600 (36000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 800x600 (40000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 800x600 (50000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "800x600" (hsync out of range)
(II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 800x600 (49500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "800x600" (hsync out of range)
(II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 800x600 (56300)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "800x600" (hsync out of range)
(II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (44900)
(II) CHROME(0): Not using default mode "1024x768" (interlace mode not supported)
(II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (65000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "1024x768" (hsync out of range)
(II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (75000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "1024x768" (hsync out of range)
(II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (78750)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "1024x768" (hsync out of range)
(II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1024x768 (94500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "1024x768" (hsync out of range)
(II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (108000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "1152x864" (hsync out of range)
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1280x960 (108000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "1280x960" (hsync out of range)
(II) CHROME(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1280x960 (148500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "1280x960" (hsync out of range)
(II) CHROME(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1280x1024 (108000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "1280x1024" (hsync out of range)
(II) CHROME(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1280x1024 (135000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "1280x1024" (hsync out of range)
(II) CHROME(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1280x1024 (157500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "1280x1024" (hsync out of range)
(II) CHROME(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1600x1200 (162000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "1600x1200" (hsync out of range)
(II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1600x1200 (175500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "1600x1200" (hsync out of range)
(II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1600x1200 (189000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "1600x1200" (hsync out of range)
(II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1600x1200 (202500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "1600x1200" (hsync out of range)
(II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1600x1200 (229500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "1600x1200" (hsync out of range)
(II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1792x1344 (204800)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "1792x1344" (hsync out of range)
(II) CHROME(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1856x1392 (218300)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "1856x1392" (hsync out of range)
(II) CHROME(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 832x624 (57284)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "832x624" (hsync out of range)
(II) CHROME(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (81620)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "1152x864" (hsync out of range)
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (96770)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "1152x864" (hsync out of range)
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (104990)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "1152x864" (hsync out of range)
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (119650)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "1152x864" (hsync out of range)
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (121500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "1152x864" (hsync out of range)
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1152x864 (143470)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "1152x864" (hsync out of range)
(II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1360x768 (72000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "1360x768" (hsync out of range)
(II) CHROME(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1360x768 (84750)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "1360x768" (hsync out of range)
(II) CHROME(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1400x1050 (122000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "1400x1050" (hsync out of range)
(II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1400x1050 (145060)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "1400x1050" (hsync out of range)
(II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1400x1050 (155800)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): CrtcHSyncEnd out of range.
(II) CHROME(0): Not using default mode "1400x1050" (horizontal sync too wide)
(II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1400x1050 (179260)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "1400x1050" (hsync out of range)
(II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1440x900 (106500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "1440x900" (hsync out of range)
(II) CHROME(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1600x1024 (103125)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "1600x1024" (hsync out of range)
(II) CHROME(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1680x1050 (119000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "1680x1050" (hsync out of range)
(II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1680x1050 (146250)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "1680x1050" (hsync out of range)
(II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1680x1050 (174000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "1680x1050" (hsync out of range)
(II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1680x1050 (187000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "1680x1050" (hsync out of range)
(II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1680x1050 (214750)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "1680x1050" (hsync out of range)
(II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1920x1080 (138500)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "1920x1080" (hsync out of range)
(II) CHROME(0): Not using default mode "960x540" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 1920x1200 (154000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): Not using default mode "1920x1200" (hsync out of range)
(II) CHROME(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) CHROME(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) CHROME(0): ViaValidMode: Validating 800x600 (40000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 800x600 (36000)
(II) CHROME(0): ViaModePrimaryVGAValid
(II) CHROME(0): ViaValidMode: Validating 640x480 (25175)
(II) CHROME(0): ViaModePrimaryVGAValid
(--) CHROME(0): Virtual size is 800x600 (pitch 800)
(**) CHROME(0): *Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz
(II) CHROME(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) CHROME(0): *Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.2 Hz
(II) CHROME(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) CHROME(0): *Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 59.9 Hz
(II) CHROME(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)

---

This is a VIA box I want to use to run XBMC.  Its perfect because its fanless and so extremely quiet.  I can't figure out how to get the thing to recognize that my TV can do 1920x1080 at 60 Hz or even change the monitor from default to something else that can be set to support that resolution.

I tried a suggestion from another thread about running "sudo displayconfig-gtk" but I get a Command Not Found on that.

Any help is appreciated.

Thanks!

Chris

---

