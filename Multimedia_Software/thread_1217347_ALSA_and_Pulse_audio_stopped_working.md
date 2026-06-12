---
title: "ALSA and Pulse audio stopped working"
date: 2009-07-19
forum: Multimedia Software
---

### Post by zepita on 2009-07-19
Hi,

I was watching a movie last night and when I turned on the computer today, there was no sound at all.
What I found in system>preferences>sound is that no matter I select ALSA or Pulse Audio, the "testing" dialog appears, but no sound at all. I only have sound by selecting OSS - Open Sound System, which is currently selected. 
Is there something bad by using OSS? I got to work VLC and SMPleyer with OSS, but not firefox and flash.

heres my lsmod | grep snd output:

```
darkstar@darkstar-laptop:~$ sudo lsmod | grep snd
snd_hda_intel         434100  2 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  2 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62628  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  2 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm

```

Any suggestions will be appreciated.

---

### Post by igorzwx on 2009-07-19
the system was updated, perhaps

---

### Post by igorzwx on 2009-07-19
[http://en.wikipedia.org/wiki/OSS](http://en.wikipedia.org/wiki/OSS)

---

