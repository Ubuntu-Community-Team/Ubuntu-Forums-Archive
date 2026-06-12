---
title: "No Audio"
date: 2013-09-23
forum: Multimedia Software
---

### Post by jacatone on 2013-09-23
I recently installed Ubuntu 12.04 LTS and  I find my audio doesn't work with either streaming or music files. Below is the info for my system.  Anyone know where I can start to fix this? Thanks.

jacatone@Compaq:~$ aplay -l | grep card
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
jacatone@Compaq:~$ sudo lsmod | grep snd
[sudo] password for jacatone:
snd_hda_codec_conexant    62317  1
snd_hda_intel          33719  2
snd_hda_codec         127706  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    79041  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm

---

### Post by Yellow Pasque on 2013-09-24
Start by using latest driver/module: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)
If that doesn't work give more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by jacatone on 2013-09-25
Still didn't work.

---

### Post by Yellow Pasque on 2013-09-25
> **jacatone said:**
> Still didn't work.

...

> If that doesn't work give more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

