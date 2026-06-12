---
title: "Sound Blaster not recognized"
date: 2006-01-29
forum: Multimedia &amp; Video
---

### Post by Dave Gall on 2006-01-29
I'm a newbie with Linux/Ubuntu.  My pc recognizes the cd and i can boot from it, however when i put an audio cd in  and select "cd Player" there is no sound. Following some of the suggestions I noticed for similiar problems I have issued the command "esd' at the terminal prompt. Results are below
dave@worm-eater:~$ esd
ALSA lib confmisc.c:560:(snd_determine_driver) could not open control for card 0
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver return ed error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned er ror: No such file or directory
ALSA lib confmisc.c:955:(snd_func_refer) error evaluating name
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned err or: No such file or directory
ALSA lib conf.c:3948:(snd_config_expand) Evaluate error: No such file or directo ry
ALSA lib pcm.c:2090:(snd_pcm_open_noupdate) Unknown PCM default
dave@worm-eater:~$

clearly something not right. I have a 16 bit Sound Blaster card, the cd is connected thru an Ultra 133 tx2 controller card ( I get the same results with the Cd connected to the mother board).

Suggestions? bear in mind I'm a newbie with linux please be specific on how to use any commands.
Thank you

---

### Post by FarEast on 2006-01-29
Welcome to the Linux world, Dave;) ,

Please read this.
[http://ubuntuforums.org/showthread.php?t=84832&highlight=snd-sb16](http://ubuntuforums.org/showthread.php?t=84832&highlight=snd-sb16)

---

### Post by Dave Gall on 2006-01-29
Yippeee!
installed  "snd-sbi6 io=0x220 irq=5 dma=1 dma16=3" into /etc/modules

And sound works.

Excellent  Thanks for the assistance.

Now to find out about those commands and what I actually did!:-D

---

