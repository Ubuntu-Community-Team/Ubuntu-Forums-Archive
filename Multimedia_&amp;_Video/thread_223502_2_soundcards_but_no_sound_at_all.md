---
title: "2 soundcards but no sound at all"
date: 2006-07-26
forum: Multimedia &amp; Video
---

### Post by mcframe on 2006-07-26
Hi, 
i am running a HP nx7000 under kubuntu dapper drake. This notebook has one Intel8x0 driven sound card. Unfotunately sound does not work although all driver seems to be loaded and all channels are unmuted.
Here are the details:

```
aplay -l
**** Liste von PLAYBACK Geräten ****
Karte 0: I82801DBICH4 [Intel 82801DB-ICH4], Gerät 0: Intel ICH [Intel 82801DB-ICH4]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
Karte 0: I82801DBICH4 [Intel 82801DB-ICH4], Gerät 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0

```
you see there are **two devices #0** although the notebook has just **one sound card installed**, is this normal?


```
lsmod | grep snd
snd_intel8x0           35932  0
snd_ac97_codec         99808  1 snd_intel8x0
snd_ac97_bus            2400  1 snd_ac97_codec
snd_pcm_oss            56448  0
snd_mixer_oss          20544  1 snd_pcm_oss
snd_pcm                96644  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              26884  1 snd_pcm
snd                    60004  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10784  1 snd
snd_page_alloc         11304  2 snd_intel8x0,snd_pcm

```
I assume everthing is ok here


I have followed the sound problem guide over here, but have no idea where the problem could be. Sound worked fine in Breezy.

Many thanks in advance for any clue
mcframe

---

### Post by rocketman768 on 2006-07-26
I always seem to have sound issues (as well as a ton of other things). Someone else may be able to give a better solution that I can, but I've always found the best thing to do is build your own kernel (download from [www.kernel.org](www.kernel.org)) and build support for your card directly into the kernel instead of as a module so that you don't have to worry about loading modules. If you don't have a lot of experience building kernels tho, it will most likely go bad. You might want to learn tho ;)

---

