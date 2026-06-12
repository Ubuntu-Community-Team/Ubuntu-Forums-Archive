---
title: "Ubuntu won't boot up"
date: 2008-12-25
forum: Multimedia Software
---

### Post by baddison on 2008-12-25
Hello and Merry Christmas to everyone.  For some reason I'm getting the following error messages that are preventing Ubuntu 8.10 from starting up completely:

[LIST=1]
[*]ALSA lib confmisc.c:768: (parse_card) cannot find card 'Audigy 2'
[*]ALSA lib conf.c:3513: (_snd_config_evaluate) function snd_func_card_driver returned error: No such device
[*]ALSA lib confmisc.c:392: (snd_func_concat) error evaluating strings
[*]ALSA lib conf.c:3513: (_snd_config_evaluate) function snd_func_concat returned error: No such device
[*]ALSA lib confmisc.c:1251: (snd_func_refer) error evaluating name
[*]ALSA lib conf.c:3513: (_snd_config_evaluate) function snd_func_refer returned error: No such device
[*]ALSA lib conf.c:3985: (snd_config_expand) evaluate error: No such device
[*]ALSA lib pcm.c:2196: (snd_pcm_open_noupdate) unknown pcm default
[/LIST]

I started having issues with ubuntu when I recently upgraded ubuntu from 8.04 to 8.10.  My first issue was that I wasn't getting sound out of my creative Audigy 2 zs notebook card when I was listening to sound or watching videos in firefox (the sound was coming through my internal laptop speakers and not my surround sound speakers) though I was getting sound in Listen music player.  So I installed default sound device and selected my Audigy 2 card as the defualt sound card but this didn't work (this method had worked in previous versions of Ubuntu).  So I then followed some steps from the comprehensice sound problem solutions guide in this forum.  From the solutions guide I got the ALSA drivers from a *fresh* kernel (step 4).  I also did sudo nano /etc/modules to add my Audigy 2 sound driver to the list (I believe its snd_emu10k1 or something like that to the end of the file).  I rebooted my computer and now Ubuntu won't boot properly.  

System specs:  I have a compaq Presario X6000 notebook with a intel P4 3.4ghz processor, 2gb of ddr-2 ram, a creative Audigy 2 zs notebook card (I think it's pci express), Mobility ati x600 video card, and Ubuntu 8.10.  Once the boot up issue has been resolved I would like to make my Audigy 2 card the default sound card for my system for all applications instead of my internal intel sound card.

Thanks,
Brett

---

