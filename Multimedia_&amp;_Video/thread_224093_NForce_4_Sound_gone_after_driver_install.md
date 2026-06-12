---
title: "NForce 4 Sound gone after driver install"
date: 2006-07-27
forum: Multimedia &amp; Video
---

### Post by ironfistchamp on 2006-07-27
Hey all

I installed the NFORCE drivers from the Nvidia website. Installed fine. Loaded X Server and audio was fine but my Eth card was gone. ebotted eth back audio gone, rebooted both gone, rebooted eth back. The network seems stable now but the audio will not come back. When I issue esd I get this output

ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default


I tried to uninstall the drivers but nothing happened. Any ideas?

Also what is very weird is when I don't have the NFORCE drivers installed the little splash bit when you first login, the first icon seems to be from a different icon set but with them installed it is from the Human set. Why on earth does this change the icon?

Thanks

Ironfistchamp

---

### Post by ironfistchamp on 2006-07-27
Just rebooted and although there is no logon or system sounds banshee seems to have decent output. However OSS apps (flash in firefox) has very stuttery sound.

I noticed something from dmesg output. nvidia license "taints" kernel.

What does that mean. Sounds weird.

---

