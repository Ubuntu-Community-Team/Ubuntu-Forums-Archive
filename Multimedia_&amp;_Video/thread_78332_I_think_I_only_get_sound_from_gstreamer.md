---
title: "I think I only get sound from gstreamer"
date: 2005-10-18
forum: Multimedia &amp; Video
---

### Post by kombipom on 2005-10-18
I've got SiS7012 on-board sound.  It worked after some fiddling with hoary just loosing the system sounds (and having no crack-attack sound for some reason).  Now I'm in Breezy and I get sound from totem & rhythmbox but nothing else.

Things I've tried:
Muting IEC stuff in alsa-mixer
Looking at all the sound related threads here.

Things I've noticed:
In alsamixer my card is shown as SIS7012 as expected but the Chip is given as Realtek which is the manufacturer of my ethernet card.
I have no /dev/snd/seq. (Don't know if that means anything).
When starting up I get messages about starting ALSA card 0 and ALSA card 1 but I only have the one on-board card.

Any ideas people?
Happy to supply output of any command you care to name.

---

### Post by mlomker on 2005-10-18
> In alsamixer my card is shown as SIS7012 

I think I have the same card, but I use KDE so I mostly use Xine (amaroK being my main app).  What are you trying to get sound out of?

I assume the right drivers are loaded:

```

mlomker@mlomkernote:~$ lsmod | grep snd
snd_intel8x0           33344  1
snd_ac97_codec         84028  1 snd_intel8x0
snd_pcm_oss            53152  0
snd_mixer_oss          19392  1 snd_pcm_oss
snd_pcm                89032  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              24260  1 snd_pcm
snd                    55172  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9696  1 snd
snd_page_alloc         10696  2 snd_intel8x0,snd_pcm

```

---

### Post by kombipom on 2005-10-19
I'm trying to get sound out of games like Wesnoth and Crack-attack, system sound would be nice too but I lived without them in Hoary so... (shrug)

My output to lsmod | grep snd is different to yours:

```
snd_mpu401              6312  0
snd_mpu401_uart         7296  1 snd_mpu401
snd_rawmidi            24704  1 snd_mpu401_uart
snd_seq_device          8460  1 snd_rawmidi
snd_intel8x0           33248  1
snd_ac97_codec         83932  1 snd_intel8x0
snd_pcm_oss            52704  0
snd_mixer_oss          19296  1 snd_pcm_oss
snd_pcm                88840  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              24164  1 snd_pcm
snd                    54884  12 snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_ device,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9600  1 snd
snd_page_alloc         10600  2 snd_intel8x0,snd_pcm
```

but if the soundcard driver is wrong how come I get sound from gsteamer and I hear the drum-beats at startup?  (Forgive my dumb ass).

---

### Post by mlomker on 2005-10-19
> but if the soundcard driver is wrong how come I get sound from gsteamer and I hear the drum-beats at startup?  (Forgive my dumb ass).

Nope, you're right.  Standard troubleshooting dictates that you start at the lowest level and work your way up, rather than the other way around.

If you're getting a sound on start-up then those are system sounds, afaik.  Do you have xine installed?  **libxine1c2**

---

