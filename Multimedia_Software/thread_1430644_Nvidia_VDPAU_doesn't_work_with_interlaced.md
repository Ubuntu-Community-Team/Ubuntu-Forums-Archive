---
title: "Nvidia VDPAU doesn't work with interlaced?"
date: 2010-03-15
forum: Multimedia Software
---

### Post by bsmith1051 on 2010-03-15
I've successfully installed the 'current' Nvidia proprietary drivers on my Ubuntu 9.10 with Geforce 8400GS videocard.  Then I added the Nvidia PPA, refreshed Synaptic, and installed the updated versions of mplayer etc.  Finally I switched the video-output method in Smplayer to 'vdpau'.  Now when I play a high-def h.264 video the cpu utilization is much much better, so I know the vdpau acceleration is working.

But all my Sony home-videos (AVCHD 1080i) still stutter like crazy. I also have 1080i videos I recorded on my Hauppauge HD-PVR and they stutter, too.  So it appears as if my VDPAU is not recognizing or correctly decoding interlaced video?

Does anyone know more detail about this?

P.S. I'm currently running the 185.18.36 driver since that's what was supported by the built-in Hardware Drivers function.  But I also did a test install of Lucid Alpha 3 (and upgraded to the AMD64 kernel, too) and installed the latest latest 195.35(?) version; same problem.

---

### Post by AdrianVeidt on 2010-03-15
This question is best asked in the nvforums. This thread might help get you started:

[http://www.nvnews.net/vbulletin/showthread.php?t=141995](http://www.nvnews.net/vbulletin/showthread.php?t=141995)

---

### Post by bsmith1051 on 2010-03-17
FYI - I have a workaround for this now, though not exactly what I'd call a fix.

The upshot is that my VDPAU _is_ installed and functioning properly -- it's the Mplayer defaults (as well as Smplayer) that's screwing things up.  One of the ffmpeg editors over at the Nvidia forums suggested that I try running mplayer manually and with different command-line options.  In doing so I was able to find a working combination of settings!

The main issues were the default demuxer (mpeg-ts) and default PTS Correction (enabled).  Playback was normal when I specified:
> > mplayer avchd.ts -demuxer lavf -nocorrect-pts
(I'm skipping listing all the vdpau commands...)
_Now_ the problem is that I can't get the same settings to work in Smplayer, so I still can't simply double-click on my home movies and have them pop-up correctly.

---

