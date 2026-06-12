---
title: "terrible sound quality in xine, good in mplayer"
date: 2007-02-21
forum: Multimedia &amp; Video
---

### Post by tendays on 2007-02-21
Hello all,

I'm experiencing problems when playing *some* audio files under xine (actually, amarok which itself uses xine as an engine). I hear some kind of rrrrrrrrr sound over the music as if I were listening to radio with bad reception.

First I thought it was a problem with mp3 files so I reencoded them into ogg (using mplayer to turn mp3 into pcm and then oggenc to turn that into ogg) but the problem is still there.

mplayer plays the files perfectly (the mp3, the ogg, whatever).

I saw someone else who seemed to have the same problem, and his problem was solved by diminishing pcm volume and increasing master volume but this has no effect for my problem.

I tried changing settings in xine but it has no effect.

I put the first ten seconds of one such "problematic" song at [http://gamboni.org/~tendays/test.ogg](http://gamboni.org/~tendays/test.ogg) (33KB)

$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.06
DISTRIB_CODENAME=dapper
DISTRIB_DESCRIPTION="Ubuntu 6.06.1 LTS"

$ lspci | grep audio
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)

$ uname -a
Linux badiane.gamboni.org 2.6.15-27-amd64-generic #1 SMP PREEMPT Sat Sep 16 01:50:50 UTC 2006 x86_64 GNU/Linux

$ lsmod | grep snd
snd_intel8x0           38568  2
snd_ac97_codec        110396  1 snd_intel8x0
snd_ac97_bus            4096  1 snd_ac97_codec
snd_pcm_oss            59424  0
snd_mixer_oss          20608  1 snd_pcm_oss
snd_pcm               104584  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              29064  1 snd_pcm
snd                    68576  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              13216  1 snd
snd_page_alloc         13968  2 snd_intel8x0,snd_pcm

I'm using KDE and alsa but not arts.

the "about" window in gxine says version 0.5.7.

Tell me if you need something else

Thanks a lot

- tendays

---

### Post by tendays on 2007-02-24
Okay, so I sort of solved the problem.

Playing the song on another computer (running debian - different software versions, different sound card etc) showed the same problem (good quality in mplayer, bad in xine) so it's probably not a configuration problem.
After experimenting a bit I found out that xine can't play 11KHz songs properly so I resampled my songs up to 44.1KHz and now they play fine...

---

