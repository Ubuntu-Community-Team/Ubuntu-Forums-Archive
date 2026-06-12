---
title: "No Sound: Via8237 on a Biostar p4m800 m7-Pro"
date: 2009-08-25
forum: Multimedia Software
---

### Post by lamarkm2 on 2009-08-25
I am completely new to Ubuntu and have downloaded the latest version with all the latest updates.  I have cannibalized some old computers that I had laying around and everything is working but the sound card!

Please help, I have searched forums and am somewhat blind.

Can anyone help?

I am running a Via8237 on-board sound card.

mike@mike-desktop:~$ lsmod|grep '^snd'
snd_via82xx            31768  3 
snd_ac97_codec        110880  1 snd_via82xx
snd_pcm_oss            45984  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         17032  2 snd_via82xx,snd_pcm
snd_mpu401_uart        15360  1 snd_via82xx
snd_seq_dummy          10884  0 
snd_seq_oss            39296  0 
snd_seq_midi           14240  0 
snd_rawmidi            29472  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57456  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29320  2 snd_pcm,snd_seq
snd_seq_device         15372  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    65444  18 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device


PLEASE HELP!

---

### Post by juntjoo on 2009-11-21
good luck.  i am in the same boat.  i had been working with this thread:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

but i'm almost about to give up and wait til someone smart programs a fix for us. otherwise i may just buy a sound card.

---

