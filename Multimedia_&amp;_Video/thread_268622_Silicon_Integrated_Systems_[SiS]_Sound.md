---
title: "Silicon Integrated Systems [SiS] Sound"
date: 2006-09-30
forum: Multimedia &amp; Video
---

### Post by suevil on 2006-09-30
hello,

i have a laptop with that sound device (Silicon Integrated Systems [SiS] Sound)

Before i installed ubuntu dapper,that sound device rules right with another debian SO.

The ubuntu dapper didnt detect it.

-->lspci | grep audio
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)



-->lsmod | grep snd
snd_intel8x0 36380 0
snd_ac97_codec 100512 1 snd_intel8x0
snd_ac97_bus 3328 1 snd_ac97_codec
snd_pcm_oss 56992 0
snd_mixer_oss 21248 1 snd_pcm_oss
snd_pcm 96516 3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer 27140 1 snd_pcm
snd 59748 6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore 11232 1 snd
snd_page_alloc 12296 2 snd_intel8x0,snd_pcm

can you help me?¿ (sorry for my english too)

---

