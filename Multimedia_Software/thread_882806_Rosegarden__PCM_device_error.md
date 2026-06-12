---
title: "Rosegarden / PCM device error"
date: 2008-08-07
forum: Multimedia Software
---

### Post by doink1212 on 2008-08-07
I am trying to get sound working on Rosegarden. 

Thus far I have succeeded in activating Jackd server and I wanted to see if timidity would fix the problem when i noticed this error message. 

> ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
Can't open pcm device 'default'.
Couldn't open ALSA pcm device (`s')
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
Can't open pcm device 'default'.
Couldn't open ALSA pcm device (`s')
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
Can't open pcm device 'default'.
Couldn't open ALSA pcm device (`s')
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
Can't open pcm device 'default'.
Couldn't open ALSA pcm device (`s')


Any ideas on how to fix this problem? Rosegarden works without error messages (outside of the terminal), It just runs without sound.

---

### Post by Kobus Trichardt on 2008-09-08
I have a similar problem which occured this morning when I downloaded the latest update.

I get the following:
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
Any ideas where to go for help ??

---

