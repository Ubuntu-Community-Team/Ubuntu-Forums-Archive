---
title: "Flash plugin sound  and firefox"
date: 2008-03-27
forum: Multimedia &amp; Video
---

### Post by g0ng on 2008-03-27
HEllo. I have a problem with my sound on flashplugin-nonfree & firefox2

It started when I changed my sound card to a soundblaster X-Fi. I had tou remove alsa and use oss4. I have sound in amarok and mplayer (with ao=oss:/dev/oss/sbxfi0/pcm0).

But I have no sound in flashplugin. I installed alsa-oss and I tried aoss firefox.
I get the following errors:

```
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib pcm_hw.c:1351:(_snd_pcm_hw_open) Invalid value for card
ALSA lib confmisc.c:769:(parse_card) cannot find card ''
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib pcm_hw.c:1351:(_snd_pcm_hw_open) Invalid value for card

```

I assume that my card isn't recognized by alsa, but that's why I installed oss. Is alsa-oss an alsa wrapper to use oss? And how can my card be found?

Thanks

---

### Post by eldragon on 2008-03-27
i had the same problem, to make sure the same is happening to you, create a new user
log in with it, and see if that user has sound with flash videos.

if thats the case:
i fixed the very same problem by doing


```

$ sudo chown -R user:user ~/.macromedia
$ sudo chown -R user:user ~/.adobe

```

where user should be your user with problems and must be executed from the user's account.

hope it helps

---

### Post by g0ng on 2008-03-28
Thanks but no this wasn't the problem. I suspect that my card isn't recognized by alsa.

---

