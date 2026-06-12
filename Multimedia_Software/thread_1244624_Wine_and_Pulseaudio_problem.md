---
title: "Wine and Pulseaudio problem"
date: 2009-08-19
forum: Multimedia Software
---

### Post by deusvulpes on 2009-08-19
Hi!

This is my first post :D

Anyway, here is my problem:

I have just installed Pulseaudio, and it's working alright. My problem is when i run Guild Wars through Wine, I have no sound. Also, I have no startup sound :(

When I input "padsp winecfg"

I get:
```
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on CA0106, disabling mixer
```Does anybody know what to do? Thanks in advance!

---

### Post by deusvulpes on 2009-08-21
Don't worry, I fixed it :D 
I used that "change stream"-thing on pulseaudio. Worked like a charm :D

---

### Post by Cypher1101 on 2009-11-29
where did you find that? wine gives me the same error but I can only see streams to switch to when audio is actively being played, and then its only that program that shows up as an option.

---

