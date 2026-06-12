---
title: "Executing Sox from PHP"
date: 2010-08-17
forum: Multimedia Software
---

### Post by bubblehead74 on 2010-08-17
Hi:

I have tried to execute Sox from PHP with exec and such. On Windows XP,
everything seems to work. On Ubuntu 10.04 converting works, however, playing and recording does not work, because the default ALSA device throws errors. The same command (sox song.ogg -d) works fine in the console. One obvious difference is that PHP runs as a different user "www-data" and I have read somewhere that ALSA has problems with this. The error message is below. Do you think this can be made to work somehow, or I just need to forget it?

Home directory /var/www not ours.
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_card_driver
returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_concat returned
error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_refer returned
error: No such file or directory
ALSA lib conf.c:4633:(snd_config_expand) Evaluate error: No such file or
directory
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
sox FAIL formats: can't open output file `default': snd_pcm_open error: No such
file or directory

Thanks,
Martin

---

