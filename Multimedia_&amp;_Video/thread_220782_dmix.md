---
title: "dmix"
date: 2006-07-22
forum: Multimedia &amp; Video
---

### Post by Megatog615 on 2006-07-22
```
ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave
```
I get these errors when trying to use ALSA for sound in programs.

For example, from the ALSA Wiki:
aoss mpg321 some.mp3
returns:
```
Playing MPEG stream from some.mp3 ...
MPEG 1.0 layer III, 128 kbit/s, 44100 Hz stereo
ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave
ALSA snd_pcm_open error: Device or resource busy
- using device default
- using device default
ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave
Creating link /home/megatog615/.kde/socket-falcon-2.
can't create mcop directory
```
Why is it trying to "create mcop directory"?

---

