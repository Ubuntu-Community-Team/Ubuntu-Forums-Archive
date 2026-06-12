---
title: "No sound Dapper (CM8738)"
date: 2006-05-28
forum: Multimedia &amp; Video
---

### Post by Matten on 2006-05-28
I have a C-media Electronics soundcard CM 8738 and I've just installed Dapper. And again I have no sound! Is there anyone here that knows a solution?

This is what I get with: lsmod | grep snd and amixer

matthias@Ubuntu-desktop:~$ lsmod | grep snd
snd_cmipci 34336 0
gameport 15496 1 snd_cmipci
snd_pcm_oss 53664 0
snd_mixer_oss 18688 1 snd_pcm_oss
snd_pcm 89864 2 snd_cmipci,snd_pcm_oss
snd_page_alloc 10632 1 snd_pcm
snd_opl3_lib 10624 1 snd_cmipci
snd_timer 25220 2 snd_pcm,snd_opl3_lib
snd_hwdep 9376 1 snd_opl3_lib
snd_mpu401_uart 7808 1 snd_cmipci
snd_rawmidi 25504 1 snd_mpu401_uart
snd_seq_device 8716 2 snd_opl3_lib,snd_rawmidi
snd 55268 10 snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_o pl3_lib,snd_timer,snd_hwdep,snd_mpu401_uart,snd_ra wmidi,snd_seq_device
soundcore 10208 1 snd


matthias@Ubuntu-desktop:~$ amixer
amixer: Mixer attach default error: No such device

---

