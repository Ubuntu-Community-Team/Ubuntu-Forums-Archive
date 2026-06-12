---
title: "No sound, devices busy, and can't get rid of pulseaudio"
date: 2009-02-26
forum: Multimedia Software
---

### Post by Noccy on 2009-02-26
Hi all!

I'm experiencing the problem with my sound device being busy due to PulseAudio (from what I gathered from googling). Attempting to remove pulseaudio will also get rid of "ubuntu-desktop" which sounds a bit dangerous.

The error i receive from aplay is:

```
ALSA lib pcm_dmix.c:1008:(snd_pcm_dmix_open) unable to open slave
aplay: main:583: audio open error: Device or resource busy
```

I get similar errors from Audacious, and any other programs I've tried. No matter what, I'm unable to get any kind of sound output from the system, and the pulseaudio tools are unable to connect to my pulseaudio server, which is also unkillable.

Is it safe to remove ubuntu-desktop or is there any other solution to my problem?

---

### Post by markbuntu on 2009-02-26
Rather than get rid of pulseaudio you should fix it which you can do in 10 minutes or less

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

