---
title: "AGPTEK HDMI -&gt; USB3 Capture Device FPS Lag"
date: 2020-07-22
forum: Multimedia Software
---

### Post by Adam_GUI on 2020-07-22
I have an AGPTEK HDMI to USB3 Capture device.  Model Number VG0061.

I have it working in VLC.  TVTime told me it wasn't a valid Video for linux 2 device.  Xawtv doesn't see it, either. 
Anyway, I have several consoles.
At software init, it sends signal over HDMI to be 60FPS.  I think this is intended, as the device is advertised as being 60FPS.  
However, this causes serious input lag.

I have to manually go into VLC settings thusly:

Media>
Open Capture Device>
Advanced Options>

Change "Frame Rate" from "60" to "30."

After doing that, my input lag is gone and I'm good to go.

Problem is that it does this on game change, too.  So, for example, I have a Playstation 3.
On boot init to hypervisor > 60FPS.
-----> Change FPS to 30.
Select Program/Game/Blu-Ray/
----->System sends init to 60 FPS.
-----> Manually change FPS to 30.
-----> Exit Game to Hypervisior.  Return to 60 FPS.  D.C. Al Coda Ad Nauseum.

The XBox 360 is a bit more sane.
On boot init to hypervisior > 60 FPS.
-----> Change FPS to 30.
Software stays at 30 FPS no matter what's launched until power down.

Playstation 4 acts similarly to the XBox 360.

I have a Roku device that behaves this way as well.  Colors wrong and lag at 60FPS.  Colors correct and no lag at a corrected 30 FPS.

Is there a way, in VLC, I can permanently set this card to capture at 30 FPS?
I'm happy with my resolution!  I can read things I never had hopes of reading on my old Pinnacle S-Video card!

I just want to break this cycle of me fighting the hardware/software capture reset to 30FPS at every console/game start function.

I'm willing to play with config files.  Just point me at 'em!

---

### Post by TheFu on 2020-07-23
[https://wiki.videolan.org/VLC_command-line_help](https://wiki.videolan.org/VLC_command-line_help)

Too bad the VLC team didn't see fit to put this into a useful manpage.

---

### Post by Adam_GUI on 2020-07-23
> **TheFu said:**
> [https://wiki.videolan.org/VLC_command-line_help](https://wiki.videolan.org/VLC_command-line_help)

Too bad the VLC team didn't see fit to put this into a useful manpage.

I appreciate the RTFM.  I really do.

If anything, it gave me the inspiration I needed to try tvtime again.
Sucker works!  No frame-rate shenanigans!

When I got the video4linux2 error, I had it connected to a USB2 hub.  
I know, I know.  But, on-board USB3 ports were dead and the expansion card was on order.


I had everything connected via HDMI yesterday when the pcie USB3 card arrived.  
Never thought to check tvtime again before now.
One dpkg-reconfigure later and I've got the correct video device at the correct frame rate.

I'll mark the thread as solved.

---

### Post by TheFu on 2020-07-23
I wondered why you insisted on using vlc for this when there are so many better tools, but, for once, I was paying attention to the specific question.

I have an AGPTek recording device. It doesn't need a computer, just storage connected.  It automatically adjusts to the input HDMI signal, so I just force 720p.  For my needs, 1080p is just wasted storage and CPU time.  The problem with my AGPTek is that the recorded files are not efficiently encoded at all, so I always transcode using a cq of 19.0.  The files are usually 75% smaller and I can't see any artifacts.  My only real complaint is that AGPTek corrupts the NTFS file system about once a month and that it only supports stereo audio. I miss the DD 5.1 and AC3 audio my prior, much more expensive, Haupauge 1212 and 1515 devices supported. They all burned out after about a year.  I'm on my second AGPTek, but the first lasted about 3 yrs. For the cheap price, can't complain too much.

---

