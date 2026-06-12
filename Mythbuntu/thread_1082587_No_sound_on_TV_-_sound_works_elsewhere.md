---
title: "No sound on TV - sound works elsewhere"
date: 2009-02-27
forum: Mythbuntu
---

### Post by gungfujoe on 2009-02-27
I'm not getting any sound with TV in MythTV (Mythbuntu 8.10 AMD64).  I get sound with local and streaming videos.  With local videos, I get sound regardless of what codec is used and whether or not I send the raw signal over S/PDIF.  This include videos with AC3 sound decoded by my receiver.

I can't get MythTV to produce any sound through "Watch TV" though.  I get video only, whether I tell MythTV to directly pass through AC3/DTS signals via S/PDIF (desired) or not to (not desired).  If I go back and manually play the MPG files that it saves with mplayer or VLC, I get video and sound, so the problem is not with my tuner (HDHomeRun), but with MythTV.

I've also asked for help on the SiliconDust forums for this problem, and thus far, I've gotten nowhere with this.  Any help would be greatly appreciated.

---

### Post by theophile on 2009-02-27
What are your audio settings?

---

### Post by gungfujoe on 2009-02-28
> **theophile said:**
> What are your audio settings?

I'm using ALSA 1.0.19, from [the upgrade script found here](http://ubuntuforums.org/showthread.php?t=1046137).  In the MythTV general settings, I've tried a variety of settings on the audio page.  It doesn't seem to matter whether I use ALSA:default, ALSA:spdif, ALSA:surround51, or even if I manually type something in to force S/PDIF output or HDMI output.  In all cases, audio goes through S/PDIF and the HDMI output is silent, and in all cases there's no audio at all when I hit "Watch TV."

I've also tried both enabling and disabling the "Enable Passthrough for AC3" (and DTS) checkboxes.  It has no effect.  The other settings on the MythTV General Settings Audio page don't seem like they should affect whether I get audio or not.

---

