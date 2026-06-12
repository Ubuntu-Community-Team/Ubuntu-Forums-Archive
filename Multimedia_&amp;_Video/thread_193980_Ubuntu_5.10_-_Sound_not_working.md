---
title: "Ubuntu 5.10 - Sound not working"
date: 2006-06-10
forum: Multimedia &amp; Video
---

### Post by Soco_Phreak on 2006-06-10
My (integrated) sound is not working and I was wondering how i could fix this problem and get my sound working again.

specs: Amd 900Mhz Proc(not sure what core)
256Mb SD RAM
ATi-9XXX Video card(cant remember if its a 9250 or 9550)

Its an HP pavillion pre-build so its got a really crappy mobo in it. 
It told me to run esd in command script and this is what it put out

ALSA lib confmisc.c:560:(snd_determine_driver) could not open control for card 0ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:955:(snd_func_refer) error evaluating name
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3948:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2090:(snd_pcm_open_noupdate) Unknown PCM default

Any help would be greatly appreciated

---

### Post by 2501 on 2006-06-10
try Kmix.

sudo apt-get install kmix

-2501

---

### Post by Soco_Phreak on 2006-06-10
When I start volume control it says no volume control elements and/or devices found.... May it be that Ubuntu is not recognizing my integrated audio?

---

### Post by Ivhassel on 2006-06-10
Look what kind of audio chipset your computer has. Most likely you can find that in the specs for your computer (manufacturer's site would be a good bet). Then you can find out what driver you're looking to install.

---

