---
title: "Sound broken"
date: 2006-09-11
forum: Multimedia &amp; Video
---

### Post by bedfojo on 2006-09-11
My sound is broken, having previously been working.

I'm running an Acer 3613WLMi.  I have tried everything on the Comprehensive Sound Problem Solutions Guide v0.5e ([http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)) including the General Help, Getting the ALSA drivers from a *fresh* kernel and ALSA driver Compilation.  The system is still not seeing my sound card.

lspci shows the card as 
0000:00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)

aplay -l shows
aplay: device_list:221: no soundcards found...

This despite running 
sudo modprobe snd-intel8x0
without any error messages.

It's like the card is somehow disabled.  I have checked the BIOS settings on boot (via f2) but there is nothing there about sound cards.

.xsession-errors contains, repeatedly:
ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default


The sound is working fine on Win XP OS (I'm runing dual boot).
Any ideas?  I've only just come over to Ubuntu and Linux and was loving it.

---

### Post by bedfojo on 2006-09-11
Also, for got to say running Dapper 6.06.1 and 

lsmod | grep snd gives:
snd_intel8x0           34076  0
snd_ac97_codec         92832  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            61728  0
snd_mixer_oss          19456  1 snd_pcm_oss
snd_pcm                99080  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              26500  1 snd_pcm
snd                    62956  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixe r_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         11272  2 snd_intel8x0,snd_pcm

---

### Post by bedfojo on 2006-09-12
Problem solved.  Privileges issue.
See [http://www.ubuntuforums.org/showthread.php?t=218685](http://www.ubuntuforums.org/showthread.php?t=218685)
These forums are fantastic.

---

