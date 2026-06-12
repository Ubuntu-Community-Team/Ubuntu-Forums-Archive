---
title: "Only CD sound Ubuntu 5.10 Ensoniq1371 audio card"
date: 2006-04-06
forum: Multimedia &amp; Video
---

### Post by eyeonus on 2006-04-06
I don't know what it is, but for some reason I am unable to get any sound except by playing a CD with Grip. I've tried doing everything I could find to do, including reinstalling a slew of audio packages, all to no avail. I have made sure that the volume control is not muted, but the only thing I've been able to get is a static sound when I max the master volume.

I also have no clue why Grip is able to play Audio CDs when nothing else is able to successfully play /anything/.

The only I can see that might be a problem is the chip identification in alsamixer, which is "0x8a054e53 ?[]N" where '[]' is a box character. "0x8a054e53 ?" is also the name in gnome-alsamixer's tab, and as device "_1" in the Volume Control.

Here's some terminal output if it helps:
```
eyeonus@panther:~$ lsmod | grep snd
snd_ens1371            22240  7
gameport               14472  1 snd_ens1371
snd_rawmidi            22816  1 snd_ens1371
snd_seq_device          8204  1 snd_rawmidi
snd_ac97_codec         72188  1 snd_ens1371
snd_pcm_oss            46368  1
snd_mixer_oss          16128  2 snd_pcm_oss
snd_pcm                78344  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  18 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  4 cs46xx,snd
snd_page_alloc         10120  1 snd_pcm
```

This a new install, of Ubuntu 5.10 "Breezy Badger", and the only sound I get is PC speaker beeps.

---

### Post by TPower on 2006-04-27
I have the same sound card. New install of Badger and no sound! any ideas?:confused:

---

### Post by deadgobby on 2006-04-27
[https://wiki.ubuntu.com/HowToSetupSoundCards?highlight=%28cards%29%7C%28sound%29](https://wiki.ubuntu.com/HowToSetupSoundCards?highlight=%28cards%29%7C%28sound%29)
try this link and see if this helps. 
gobby

---

### Post by eyeonus on 2006-04-27
That didn't help at all. I've already done what it says to do, and all I get is static from the speakers if I turn the master volume to max.

---

