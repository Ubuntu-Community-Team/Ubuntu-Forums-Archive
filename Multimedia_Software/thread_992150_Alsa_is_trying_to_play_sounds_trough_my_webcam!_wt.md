---
title: "Alsa is trying to play sounds trough my webcam! wtf?"
date: 2008-11-24
forum: Multimedia Software
---

### Post by crazyfuturamanoob on 2008-11-24
Whenever I try to run something that uses alsa, I get this:
> 
fixme:mixer:ALSA_MixerInit No master control found on USB Camera, disabling mixer

No sound.

It's trying to play sounds trough my web cam? lol why? :D How to fix it?

---

### Post by psyke83 on 2008-11-24
> **crazyfuturamanoob said:**
> Whenever I try to run something that uses alsa, I get this:

No sound.

It's trying to play sounds trough my web cam? lol why? :D How to fix it?

It's actually PulseAudio causing that issue. See the [PulseAudio Fixes]("http://ubuntuforums.org/showthread.php?t=789578") guide. Part A, Step 5 explains how to select a default playback device.

---

### Post by crazyfuturamanoob on 2008-11-24
> **psyke83 said:**
> It's actually PulseAudio causing that issue. See the [PulseAudio Fixes]("http://ubuntuforums.org/showthread.php?t=789578") guide. Part A, Step 5 explains how to select a default playback device.

Ok I unplugged my webcam. Now it says:
```

ALSA lib pcm_dmix.c:996(snd_pcm_dmix_open) unable to open slave 96:(snd_pcm_dmix_open)

```

Also, some time ago (today) I fixed my pulseaudio thing. Now it's possible to play multiple audio things at the same time, although wine sound isn't working.

---

