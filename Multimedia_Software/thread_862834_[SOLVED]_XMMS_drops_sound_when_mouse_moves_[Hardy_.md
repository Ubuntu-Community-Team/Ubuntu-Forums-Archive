---
title: "[SOLVED] XMMS drops sound when mouse moves [Hardy Heron]"
date: 2008-07-17
forum: Multimedia Software
---

### Post by MattP220 on 2008-07-17
About two weeks ago I installed 8.04.1 from an older 7.10 install. Have had no problems so far.

Last night, I clicked on a podcast from a website, mp3 format, which played fine. However after that, XMMS gave me an error that it was not configured properly.

Just a few moments ago I installed updates and rebooted. XMMS would then play mp3 files, but on moving the mouse, sound would instantly drop. Some players were not affected, as I could play mp3 files in MPLayer. However Rhythmbox wouldn't work at all. 

I'm using the OSS driver, which has worked fine (until now, anyway).

Any ideas? 

Here's more system info if that will help:

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
lsmod | grep snd 
snd_atiixp_modem       19724  0 
snd_atiixp             24340  5 
snd_ac97_codec        123224  2 snd_atiixp_modem,snd_atiixp
ac97_bus                3840  1 snd_ac97_codec
snd_pcm_oss            47648  0 
snd_mixer_oss          20224  1 snd_pcm_oss
snd_pcm                92168  5 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           5764  0 
snd_seq_oss            38912  0 
snd_seq_midi           10688  0 
snd_rawmidi            29856  1 snd_seq_midi
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi
snd_seq                63232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27912  3 snd_pcm,snd_seq
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    70856  20 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10400  1 snd
snd_page_alloc         13200  3 snd_atiixp_modem,snd_atiixp,snd_pcm
```

---

### Post by MattP220 on 2008-07-18
meh, I just decided to give up on XMMS. XMMS2 sucked, but Audacious supports most of the same things I'm looking for (I don't need the whole organizer thing, just playback). Thanks anyway.

---

### Post by markbuntu on 2008-07-19
There is a thread around here somewhere about getting xmms to work in hardy. It involves getting the deb from launchpad but it definitely works because I am using xmms right now on my Hardy. 

So, if you want your xmms back you can try to find it. I'm sorry, but I can't find the thread for you right now, but it should be pretty easy for you to find.

Edit:
Ok, here is one of the threads. There is some thing it there that will give you a link to the Hardy xmms.

[http://ubuntuforums.org/showthread.php?t=791382](http://ubuntuforums.org/showthread.php?t=791382)

---

