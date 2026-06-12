---
title: "sound stopped working; now refuses to be fixed"
date: 2007-11-23
forum: Multimedia &amp; Video
---

### Post by sunflowerfox on 2007-11-23
Sadly, I my machine no longer plays sound. It's a mystery, really. I'll explain how this happened, what I've done to try to remedy the situation, and where I am left. Hopefully someone will have the magical solution!

Once upon a time, sounds worked perfectly. Dapper Drake was installed, and everything was up-to-date. Then, one dark day, something happened. Nothing significant, nothing I can recall, but something... Sound stopped working! Oh noes!

The usually troubleshooting procedure involves checking through *alsamixer*, Everything was unmuted. Like usual. There are some posts floating around here that suggest on some machines, certain things *do* need to be muted for everything to work just right. That has never been the case for me, though.

Next, I moved on to checking to make sure the device exists, and is the right one. Indeed it does! Purging/removing alsa, and reinstalling didn't help either. What am I to do from here? Generally I use VLC to play media, and it seems to play fine. Just without any audio. So sad.

Finally, I blindly upgrade to Feisty, hoping that somehow a new version of something would fix everything. I did all my troubleshooting steps again, to no avail. Finally, now at Gutsy, and repeated them one last time. Nothing new.

Please, please, please guide me on a journey towards resolving this problem. I've included various data below...

machine: Dell Inspiron 710m (laptop)

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-IC
H4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 8
2801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #
```

```
lspci  | grep Audio
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
```

```
lsmod | grep snd
snd_intel8x0           34972  0 
snd_ac97_codec        100644  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
```

Please Ubuntu Forums. You're my only hope!

---

### Post by sunflowerfox on 2007-11-24
dropped off the front page!? alas it looks like i have to *bump*

---

### Post by Yellow Pasque on 2007-11-24
Try OSSv4 if you can't get ALSA to work, see my signature.

---

### Post by sunflowerfox on 2007-11-24
This reply was totally unhelpful. It strikes me that you may not have even read my post, but just proceeded to promote OSS. Despite my legitimate annoyance at this, I went ahead and tried the OSSv4 package. It not only failed to install, but then suddenly failed to remove as well. Broken package of doom! I had to dig about for a while, and was eventually able to get rid of it.

Honestly, I don't have strong feelings about the sound architecture I use, as long as it works. ALSA is dead, but at least it installs!

---

### Post by Yellow Pasque on 2007-11-24
> **sunflowerfox said:**
> This reply was totally unhelpful. 

It's been helpful to at least a handful of people struggling with ALSA and is a legitimate fix. I "promoted" it as an alternative solution if "you couldn't get ALSA to work". I'm sorry it didn't help you, but you could've at least posted some output and let people attempt to help you with the install.

> Honestly, I don't have strong feelings about the sound architecture I use, as long as it works.
I feel the same way. OSS works far better in my experience and is very easy to upgrade. The last time I upgraded ALSA, my sound broke. Compiling from source didn't work either. (And even when ALSA was working, it had bugs and only supported some of the features of my card.)

---

