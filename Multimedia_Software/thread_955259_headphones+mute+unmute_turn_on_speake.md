---
title: "headphones+mute+unmute turn on speake"
date: 2008-10-22
forum: Multimedia Software
---

### Post by mike.c on 2008-10-22
Hello,

Has anybody had the following issue ? I have an HP DV9000 laptop and when I have the headphones plugged in and mute-unmute with the dedicated button part of the hp quickplay buttons the speakers turn on.

I'm using hardy heron.

Anyone knows how to fix it ?

Thanks.

Relevant Information:

uname -a:

```
Linux laptop 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64 GNU/Linux
```


lspci:

```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Unknown device 30cc
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f8400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Unknown type IRQ 0
```


lsmod | grep snd

```
snd_hda_intel         440408  5 
snd_pcm_oss            47648  0 
snd_mixer_oss          20224  1 snd_pcm_oss
snd_pcm                92168  3 snd_hda_intel,snd_pcm_oss
snd_page_alloc         13200  2 snd_hda_intel,snd_pcm
snd_hwdep              12552  1 snd_hda_intel
snd_seq_dummy           5764  0 
snd_seq_oss            38912  0 
snd_seq_midi           10688  0 
snd_rawmidi            29856  1 snd_seq_midi
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi
snd_seq                63232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27912  2 snd_pcm,snd_seq
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    70856  20 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10400  1 snd
```

---

### Post by malleus74 on 2008-10-23
I have the same problem.

---

