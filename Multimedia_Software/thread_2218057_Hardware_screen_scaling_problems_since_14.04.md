---
title: "Hardware screen scaling problems since 14.04"
date: 2014-04-19
forum: Multimedia Software
---

### Post by Brent_Santin on 2014-04-19
Hello,

Just upgraded to Lubuntu 32-bit 14.04 from 13.10 yesterday.  
System is a P4, 2.8Ghz, 3GB RAM, NVidia GeForce 5700LE AGP graphics card with video drivers manually installed from Nvidia site (vERSION 173.14.39, RELEASE: 2013.12.6 - the latest possible version available for my graphics card).

Prior to the upgrade, the arcade emulator MAME, the Commodore 64 emulator VICE, and the Commodore Amiga emulator FS-UAE worked fantastically in full screen scaled mode.  No delay, smooth performance.  Reasonably low CPU usage for a processor of this vintage.

After the upgrade to 14.04, all full screen modes (1080x1920) in these emulators bring the system to a crawl.  Sound from the emulator is broken up, framerates are terrible (like two frames a second), CPU usage is near or past 100%.

I've found that in MAME and VICE, I can work-around this problem but shutting off "hardware scaling".  Essentially (I think), this takes my graphics card out of the loop and does the scaling in software/CPU. Scaling down the resolution of the emulation helps too. Frame-rates are better, CPU usage is lower, but because of these "scale-back measures" many nice full screen features of the emulators are lost and the screens don't look authentic anymore.

I also ran glxgears as a test and resized the window from its original small size, a little bigger every five seconds, until it was the full height of the screen (1080 lines) and got the following results:

```
brent@Brent-Lubuntu:~$ glxgears
552 frames in 5.0 seconds = 110.342 FPS
593 frames in 5.0 seconds = 118.471 FPS
416 frames in 5.0 seconds = 83.071 FPS
315 frames in 5.0 seconds = 62.810 FPS
287 frames in 5.0 seconds = 57.252 FPS
197 frames in 5.0 seconds = 39.354 FPS
165 frames in 5.0 seconds = 32.789 FPS
130 frames in 5.0 seconds = 25.937 FPS
124 frames in 5.0 seconds = 24.781 FPS
117 frames in 5.0 seconds = 23.274 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
      after 25689 requests (25666 known processed) with 0 events remaining.

```

I had originally switched to the Nvidia proprietary driver from Nouveau because of slight artifacts and stuttering in the latter.  The proprietary drivers worked like a dream in 13.10.

MP4 videos played in VLC VideoLAN player still play well with low CPU usage.

Based on my limited knowledge, this seems to be a problem with the graphics card full-screen scaling to 1080x1920 (desktop & monitor screenmode) under 14.04.  Might have to do something with OpenGL?

I would really appreciate any help in diagnosing the problem and fixing it.  I would prefer not to have to remove the proprietary NVIDIA driver as it were a pain to install (got the famous Nvidia black screen problem until I was finally able to get a working install), but will am willing to try it as a last resort.

The system works very well, other than when these emulators try to go into full screen mode.[TABLE="width: 100%"]
[TR]
[TD="colspan: 2"][/TD]
[/TR]
[TR]
[TD][/TD]
[TD="colspan: 2"][/TD]
[/TR]
[/TABLE]

---

### Post by Brent_Santin on 2014-04-20
Okay, it seems my Xorg.0.log file shows the following (notice the error line):

[B](II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
     compiled for 4.0.2, module version = 1.0.0
     Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  173.14.39  Wed Nov 27 15:02:30 PST 2013
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs

...

(**) NVIDIA(0): Enabling RENDER acceleration
[COLOR=#ff0000](EE) NVIDIA(0): Failed to initialize the GLX module; please check in
your X
(EE) NVIDIA(0):     log file that the GLX module has been loaded in your X
(EE) NVIDIA(0):     server, and that the module is the NVIDIA GLX
module.  If
(EE) NVIDIA(0):     you continue to encounter problems, Please try
(EE) NVIDIA(0):     reinstalling the NVIDIA driver.[/COLOR]
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5700LE (NV36) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 04.36.20.35.00
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5700LE at
(--) NVIDIA(0):     PCI:1:0:0:
(--) NVIDIA(0):     Samsung SMBX2240 (CRT-0)
(--) NVIDIA(0): Samsung SMBX2240 (CRT-0): 400.0 MHz maximum pixel clock[/B]

It couldn't initialize opengl with Trusty Tahr 14.04 --- so what now?  Do I wait for Nvidia to release a new version of its driver?

---

