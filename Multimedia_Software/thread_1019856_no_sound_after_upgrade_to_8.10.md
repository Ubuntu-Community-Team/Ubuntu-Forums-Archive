---
title: "no sound after upgrade to 8.10"
date: 2008-12-23
forum: Multimedia Software
---

### Post by firsttimeuser on 2008-12-23
it worked fine in kubuntu 8.04 and after I upgraded to 8.10 there is no sound at all. 
I want to check if the sound got muted, but there is even no speaker icon at the system panel so nothing I can click here.

THe following are some info, anyone has similar experience?

laptop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.17.
laptop:~$ cat /proc/asound/cards
 0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                      Intel 82801DB-ICH4 with AD1981B at irq 11
laptop:~$ lsmod | grep snd
snd_intel8x0           37532  0
snd_ac97_codec        111652  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10884  0
snd_seq_oss            38528  0
snd_seq_midi           14336  0
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_intel8x0,snd_pcm

---

### Post by wd5gnr on 2008-12-23
Do you have multiple sound cards (maybe a USB one?). I found that the KDE sound selector doesn't remember your settings, so if you happen to use whatever sound card it keeps using as the default, fine. If not, it keeps going silent (sending to wrong card). I filed a bug with KDE.

Also, maybe obvious but bring up kmixer and make sure you aren't muted? What does aplay -l tell you? Can aplay play sound? How about aplay -D?

---

