---
title: "Basic alsa install + fluxbox"
date: 2009-06-28
forum: Multimedia Software
---

### Post by fatalGlory on 2009-06-28
so, I've tried to do a minimal install of ubuntu, got fluxbox installed and working, now trying to get sound to happen.

I installed alsa-base and alsa-utils.  I can aplay a .wav file from the terminal (before running startx to get into fluxbox), but if I try the same command from an xterm after I've started fluxbox, I get this:

```
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:590: audio open error: No such file or directory
```

Anyone able to identify the problem?  At first I thought alsa must not be detecting the card, but it works fine outside of the x session, even while the x session was still running (by using ctrl-alt-f2)

---

### Post by fatalGlory on 2009-06-28
after finding some interesting posts around the web, I wondered if my problems might relate to a permissions issue on /dev/dsp.

I tried running ```
sudo aplay whatever.wav
``` and it worked fine, but after making myself part of the group "audio", no dice.  Tried setting the permissions on /dev/dsp to 777 - still no sound from my main user but sudo aplay works fine.

Now I'm weirded out.  Anyone know what's going on?

---

### Post by yabbadabbadont on 2009-06-28
After you added your user to the audio group, did you logout and back in?  Group membership changes do not take effect until you do so.

---

