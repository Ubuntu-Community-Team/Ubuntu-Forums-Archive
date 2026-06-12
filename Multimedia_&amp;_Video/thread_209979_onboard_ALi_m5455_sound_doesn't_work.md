---
title: "onboard ALi m5455 sound doesn't work"
date: 2006-07-06
forum: Multimedia &amp; Video
---

### Post by orzechowskid on 2006-07-06
I'm attempting to use the onboard sound which came with my Gigabyte GA-K8U-939 motherboard.  It's an ALi M5455 card, which appears to use the snd_intel8x0 kernel module.  I modprobe'd the module, which inserted correctly, and GNOME informed me that I had a new audio device I should configure.  So far, so good, but I can't get sound out of my speakers.  I've double-checked alsamixer, and all channels are unmuted except for External Amplifier (and unmuting that one makes no difference).  beep-media-player happily plays MP3s, gstreamer-properties is set up to use ALSA and seems to run its tests successfully, and both the OSS and ALSA tests in Cedega pass.

I've rebooted a million times, fiddled with mixer settings, and every audio jack on the motherboard.  Nothing works for me.

Here's the entire contents of my /etc/modprobe.d/alsa-base:

```
alias snd-card-0 snd-intel8x0
alias sound-slot-0 snd-intel8x0
```

This was stored on disk by alsaconf as /etc/modprobe.d/sound .  I backed up my original alsa-base file (which belonged to a sound card I no longer have) and symlinked sound -> alsa-base .

I'm running the 32-bit version of Dapper on an AMD64 CPU.

anyone have any idea what else I could try?  thanks in advance.

---

### Post by orzechowskid on 2006-07-06
I should also note that I've tried the drivers available on Nvidia's site (Nvidia being the company that bought ALi not too long ago), which recommend that I use the snd-hda-intel module.  This hasn't worked either - in fact, my sound card isn't even detected when this module is loaded instead of snd-intel8x0.

Anyone have any thoughts?

---

### Post by kedde on 2007-02-17
hey

i posted a reply here:

[http://ubuntuforums.org/showthread.php?p=2170978#post2170978](http://ubuntuforums.org/showthread.php?p=2170978#post2170978)

---

