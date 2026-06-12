---
title: "Suddenly not getting any sound?! (alsa dmix issues?)"
date: 2008-07-23
forum: Multimedia Software
---

### Post by davemar on 2008-07-23
In the past few days I've stopped getting any sound from my Ubuntu 8.04 machine. First noticed it while trying to play torcs which crashed when it started the game part. Rhythmbox whinged giving an error the first time, now just hangs when I try to play anything. So I tried good old aplay and that returned this error (which torcs also did similarly):

```
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open] slave
aplay: main:546: audio open error: Device or resource busy
```

I haven't been fiddling with any alsa stuff, or sound stuff at all recently, so I'm not sure what's happened. Maybe an automatic update knocked something out.

I must admit I find alsa rather mystifying, so really don't know where to start to hunt this problem down. Any ideas?

Cheers, Dave.

---

### Post by davemar on 2008-07-26
Still no ideas anyone?

---

### Post by markbuntu on 2008-07-26
Something has performed a hostile takeover of your sound card. 

The first thing you can try doing is going to System/Preferences/Sound and changing from automatic to ALSA.

---

