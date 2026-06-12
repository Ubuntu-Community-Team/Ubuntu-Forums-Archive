---
title: "Pulseaudio Issues"
date: 2011-05-15
forum: Multimedia Software
---

### Post by MGMorden on 2011-05-15
Ok, I've been Googling for 2 days now and I'm at my wits end, so I figured I'd check here.

I've been using Ubuntu since 9.04 - never had an audio issue before.  Now, on the upgrade from 10.10 to 11.04 my audio has become problematic.

Occasionally, the pulseaudio daemon develops an issue.  It'll be fine, then all of a sudden (usually 2 to 3 times per day) it'll go crazy and all audio will become scratchy and distorted.  

I have to kill pulseaudio, restart it, and then restart any applications that play sound for it to be corrected.  This is PARTICULARLY annoying as I keep a Windows VM running iTunes, and I'm having to shut that down down several times per day just to play music.

I tried going into Synaptic and initiating a reinstall on pulseaudio.  It had no effect.

Any ideas?

---

### Post by kostkon on 2011-05-15
Since, this is an upgraded system, then try deleting your hidden *.pulse* folder. A fast way to do it, is to just give the following command:
```
rm -rf ~/.pulse
```
then logout and login back again (and obviously pulseaudio will make a new .pulse folder).

---

