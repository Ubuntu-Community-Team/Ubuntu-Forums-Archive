---
title: "nVidia audio controller"
date: 2010-03-30
forum: Multimedia Software
---

### Post by bff7755a on 2010-03-30
I've Ubuntu 9.10 with 2.6.31-20 kernel. Sound kernel module is loaded, but doesn't works ;((. I have not got any errors and all programs (e.g. mplayer) thinks that sound driver is present and works OK but I can't hear a sound...

A part from **lspci -vvnn**

```
01:00.1 Audio device [0403]: nVidia Corporation Device [10de:0be3] (rev a1)
	Subsystem: Sony Corporation Device [104d:9067]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at e3080000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
```

Loaded kernel modules:

```
[vaio][mutex]~> lsmod | grep snd
snd_hda_codec_realtek   203328  0 
snd_hda_intel          26920  1 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  14 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm

```

---

### Post by coolcaseley67 on 2010-03-30
Hi 
 
ya you need to reinstall your driver for the nvidia . ...
 
hope it helps

---

### Post by bff7755a on 2010-03-30
Thank you!

That helped:

```
sudo apt-get install --reinstall linux-backports-modules-2.6.31-20-generic && reboot
```

---

### Post by coolcaseley67 on 2010-03-30
Hi
 
no probs .
 
any thing asle just post .
 
ps make  this post as soved in thead tools at the top.

---

