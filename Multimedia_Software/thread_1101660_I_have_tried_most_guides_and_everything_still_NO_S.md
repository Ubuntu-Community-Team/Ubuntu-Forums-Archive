---
title: "I have tried most guides and everything still NO SOUND"
date: 2009-03-20
forum: Multimedia Software
---

### Post by Final Fantasy on 2009-03-20
I'm running Xubuntu 8.10

hda-intel

Intel HD Audio Controller / Intel High Definition Audio

etc. etc..


Output of ```
aplay -l
```

Gives me: ```
aplay: device_list:215: no soundcards found...

```

How this all happened in the first place? Sound was working fine, although it starts getting choppy after a while and requires a reboot.  Other than that fine.  So then I do something stupid and install Realtek HD Audio drivers, after reboot - no sound.  Tried lots of things, probably made it worse.


```
speaker-test 1.0.17

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
ALSA lib confmisc.c:768:(parse_card) cannot find card 'Intel'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM default
Playback open error: -19,No such device
ALSA lib confmisc.c:768:(parse_card) cannot find card 'Intel'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM default
Playback open error: -19,No such device
ALSA lib confmisc.c:768:(parse_card) cannot find card 'Intel'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM default
Playback open error: -19,No such device
ALSA lib confmisc.c:768:(parse_card) cannot find card 'Intel'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM default
Playback open error: -19,No such device
^Z
[1]+  Stopped                 speaker-test

```

EDIT: Mine is ALC268 Intel HDA 

On a Dell Vostro 1510 laptop.

---

### Post by Final Fantasy on 2009-03-20
Bump :(

---

