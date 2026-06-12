---
title: "No audio, missing any directory related to audio"
date: 2010-10-21
forum: Multimedia Software
---

### Post by a4840639 on 2010-10-21
I am using Ubuntu 10.10 on Acer 6935G.
There was audio from the speaker but headphone was not working so I download the linux driver from Realtek and tried installing it. 
After some failures  of installation I found my sound devices are gone. 
I tried reinstall ALSA,  it did not work.

My /dev/snd directory is missing as well as /proc/asound, and here is the result of "aplay"

```
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4633:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:654: audio open error: No such file or directory
```

---

