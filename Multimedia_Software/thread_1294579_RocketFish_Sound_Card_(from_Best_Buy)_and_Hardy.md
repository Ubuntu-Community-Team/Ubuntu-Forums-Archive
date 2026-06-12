---
title: "RocketFish Sound Card (from Best Buy) and Hardy?"
date: 2009-10-18
forum: Multimedia Software
---

### Post by jrolland on 2009-10-18
Hello, all!

I have a Dell Dimension 2350 with a 1.7 GHz (single core) processor and 1 GB of RAM running Ubuntu Hardy Heron.

Using the on-board sound card, an Intel 82801DB-ICH4, has not yielded any sound whatsoever, no matter how many walkthroughs I follow, so I would like to buy a new sound card and try it.

Has anyone tried the [RocketFish]("http://www.bestbuy.com/site/olspage.jsp?skuId=9180405&type=product&id=1218047304449") sound card from Best Buy? It's supposedly a brand new sound card model, so there aren't even any drivers for it in XP or Vista, so I don't know what would be necessary to install drivers for it in Hardy, but it's cheap and available and I'd like to try it.

Thanks in advance for any assistance you can provide.

---

### Post by jrolland on 2009-10-19
OK, so I purchased and installed the Rocketfish card, and it appears to be a re-branded Creative Labs Sound Blaster Audigy LS SB0310 sound card, so I should have no problem finding drivers, etc.

I tried following the instructions on the [SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting") and, in fact, generated the information about my sound setup [here]("http://www.alsa-project.org/db/?f=951030ebe65d7608a0e40350036bb4523fee80af").

I found my ALSA version (Driver version: 1.0.16, Library version: 1.0.15, Utilities version: 1.0.15) and found the ALSA module (snd_ca0106) used for my sound card. I looked up the [webpage for my ALSA version]("http://git.alsa-project.org/?p=alsa-kmirror.git;a=blob;f=Documentation/ALSA-Configuration.txt;h=9a56b9b273cd089c2460dd0dcb5564480cb36f13;hb=c10025ae3a6e636e9f2f29ef29cd88a47a726b3a") and found the information for my module (snd-ca0106).

However, it appears I am missing the section in [my sound setup]("http://www.alsa-project.org/db/?f=951030ebe65d7608a0e40350036bb4523fee80af") on what codec my sound system uses. I don't know exactly what this means, but it appears to mean I don't have a sound codec loaded. Can anyone help me by reading the troubleshooting guide and my information and telling me how to get the codecs loaded. I would be eternally grateful. I think this is the only piece I am missing.

Thank you in advance for any assistance you can provide.

---

### Post by jrolland on 2009-10-19
As an update, when I type

```
user@machine:~$ speaker-test -Dplug:front -c2
```

I get the following output

```
speaker-test 1.0.15

Playback device is plug:front
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
ALSA lib confmisc.c:768:(parse_card) cannot find card 'I82801DBICH4'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM front
Playback open error: -19,No such device
```

I have disable the onboard sound card (which is what it appears to be trying to find) in BIOS.

Thanks in advance for any assistance you can provide.

---

### Post by just12b4gotn on 2010-09-21
> **jrolland said:**
> As an update, when I type

```
user@machine:~$ speaker-test -Dplug:front -c2
```

I get the following output

```
speaker-test 1.0.15

Playback device is plug:front
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
ALSA lib confmisc.c:768:(parse_card) cannot find card 'I82801DBICH4'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM front
Playback open error: -19,No such device
```

I have disable the onboard sound card (which is what it appears to be trying to find) in BIOS.

Thanks in advance for any assistance you can provide.
If you actually get a (helpful or effective) response I'll also be getting it as I have a similar problem, let's hope we aren't looking at  another "solved" flag on the thread unless it is actually resolved.

---

