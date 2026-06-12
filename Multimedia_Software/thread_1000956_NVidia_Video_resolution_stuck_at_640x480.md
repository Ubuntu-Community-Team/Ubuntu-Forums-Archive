---
title: "NVidia: Video resolution stuck at 640x480"
date: 2008-12-03
forum: Multimedia Software
---

### Post by wirawan0 on 2008-12-03
Hi all... I have an Ubuntu desktop (8.04) with nVIDIA card (an old one). The PC is Dell Inspiron 8300 (a desktop PC). lspci gives:

01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev a2) .

This card has a dual output, i.e a DVI (digital) output and the VGA (analog) output.

Recently I changed the monitor to a SGI widescreen monitor with 1600x1024 resolution, which necessitates the use of DVI output. What I did to use that resolution was to simply restart the X server via ctrl+alt+backspace shortcut. It worked the first time without restarting the whole PC! This Monday I rebooted the computer and now it would not recognize the digital output anymore. Even the analog output is restricted to 640x480 all the time. What could possibly wrong with this? I am using nvidia restricted driver. ( I don't know the version but if you can give instruction to fetch the version, I can do that )

My look into /var/log/Xorg.0.log reveals the following: [http://sh.nu/p/25183](http://sh.nu/p/25183)

> 
(WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
(II) NVIDIA(0): NVIDIA GPU GeForce4 MX 440 with AGP8X at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 65536 kBytes
(--) NVIDIA(0): VideoBIOS: 04.18.20.21.15
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce4 MX 440 with AGP8X at
(--) NVIDIA(0):     PCI:1:0:0:
(--) NVIDIA(0):     CRT-0
(--) NVIDIA(0): CRT-0: 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): 
(WW) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(WW) NVIDIA(0):     will be used as the requested mode.
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 640 x 480
(WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from CRT-0's EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default


Does anybody have any clue on what's happening?


(I asked this question on #nvidia IRC channel yet there was no answer. So I post the same question here to see if anybody can help me with this.)

---

### Post by dorkdork777 on 2008-12-03
If you disable the restricted driver and instead use the open-source one, what happens? Disable it then restart your computer.

---

### Post by element_G on 2008-12-03
> (WW) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(WW) NVIDIA(0):     will be used as the requested mode.
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 640 x 480
(WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from CRT-0's EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default 			 		

Looks like you need to explicitly state the screen resolution in your xorg.conf
The easiest way to do this would be with nvidia settings ( sudo nvidia-settings  from a terminal) Just remember to click the save to X configuration button when you're done.

---

### Post by wirawan0 on 2008-12-04
> **dorkdork777 said:**
> If you disable the restricted driver and instead use the open-source one, what happens? Disable it then restart your computer.

This is what happens:

> 
(--) NV(0): CRTC 0 appears to have a CRT attached
(II) NV(0): Using CRT on CRTC 0
(--) NV(0): VideoRAM: 65536 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): Configured Monitor: Using default hsync range of 31.50-37.90 kHz
(II) NV(0): Configured Monitor: Using default vrefresh range of 50.00-70.00 Hz
(WW) NV(0): Unable to estimate virtual size
(II) NV(0): Clock range:  12.00 to 350.00 MHz
(II) NV(0): Not using default mode "640x350" (vrefresh out of range)
(II) NV(0): Not using default mode "320x175" (vrefresh out of range)
(II) NV(0): Not using default mode "640x400" (vrefresh out of range)
(II) NV(0): Not using default mode "320x200" (vrefresh out of range)
(II) NV(0): Not using default mode "720x400" (vrefresh out of range)
(II) NV(0): Not using default mode "360x200" (vrefresh out of range)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (vrefresh out of range)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (vrefresh out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "320x240" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
...
(--) NV(0): Virtual size is 800x600 (pitch 800)
(**) NV(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) NV(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) NV(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) NV(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) NV(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) NV(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) NV(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) NV(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) NV(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
(**) NV(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
(==) NV(0): DPI set to (96, 96)


I used LiveCD of 8.04 (stock Ubuntu) to try this. Somehow it still doesn't feel right to me. The resolution is limited to 800x600 max. The hsync and vrefresh ranges seem to be too small. I know monitors can handle up to 85 or higher Hz for vertical refresh right now.

In any case this does not solve another piece of puzzle: The digital (DVI) output did not show up during the POST stage (before booting the OS). Don't you think this is strange? I don't think it is right for a video card to force us using the VGA during the POST stage, so that we can use the DVI output only after X is up.

Wirawan

---

### Post by element_G on 2008-12-04
> **wirawan0 said:**
> 

In any case this does not solve another piece of puzzle: The digital (DVI) output did not show up during the POST stage (before booting the OS). Don't you think this is strange? I don't think it is right for a video card to force us using the VGA during the POST stage, so that we can use the DVI output only after X is up.

Wirawan

Do you mean that if your monitor is plugged in to the DVI, you won't see anything until ubuntu's login (GDM)? When does the monitor come to life?

As far as getting your screen resolution set correctly goes, I think the best approach is to start from the ground up and make sure the NVIDIA Binary drivers (from their site) are being installed correctly. 

This HOW-TO : [http://ubuntuforums.org/showthread.php?t=514161](http://ubuntuforums.org/showthread.php?t=514161)
has helped me since Fiesty to get my NVIDIA drivers installed without fail. It is a bit in-depth but it was easy for me to follow. 

After that I would say to use the nvidia-settings program I mentioned earlier to correctly set the resolution. 

Your issue with the DVI output may be a bit more pressing but I can't offer as much help there ;)

---

### Post by wirawan0 on 2008-12-17
Thanks to all who answered my question. It turned out that the LCD signal adapter was messed up (like "crashed"?). All I needed to do was turn off that signal adapter completely, then turned it on. It worked perfectly now, and the 1600x1024 resolution is back working.

---

### Post by Maelgwyn on 2008-12-18
I'm having a similar issue to the OP - I've got an nVidia 8600GT card, and only recently has Ubuntu booted into 640x480, yet the splash screen appears to be normal... I can't resize resolution as the highest resolution on offer is 640x480! This is also the case in nvidia-settings.

I've disabled/uninstalled the restricted drivers and then re-enabled/installed them, but no difference. Any ideas on my next step?

---

### Post by tilerwen on 2009-01-14
Edit your xorg.conf with:

Section "Device"
   ...
   Option "IgnoreEDID" "1"
EndSection

---

