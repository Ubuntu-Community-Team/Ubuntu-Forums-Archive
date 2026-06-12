---
title: "Sound looks ok, but no sound"
date: 2007-01-07
forum: Multimedia &amp; Video
---

### Post by kverkeren on 2007-01-07
Hello, 

I have a problem... I've installed all alsa-drivers and stuff. followed some howtos and no result.
(Comprehensive Sound Problem Solutions Guide v0.5e - on this forum)

But the funny thing is, when i run alsamixer i hear strange tapping sound in the headsett when i boost the volume.
And when i run xmms from console i see no output erros. And the song runs fine. I don't know what to do anymore. I'm totally frustrated!

lspci: 

```

lspci | grep Multimedia

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)

```

lsmod:

```

lsmod | grep snd

snd_intel8x0           35228  4
snd_ac97_codec        102948  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47232  0
snd_mixer_oss          19712  1 snd_pcm_oss
snd_pcm                84996  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              24964  2 snd_pcm
snd                    60804  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11656  2 snd_intel8x0,snd_pcm

```

aplay -l

```

**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```
Thanks in advance.

reg 
kverkeren

---

### Post by kverkeren on 2007-01-07
bump

---

