---
title: "Sound problem on my computer"
date: 2019-01-20
forum: Multimedia Software
---

### Post by sylvain.gut on 2019-01-20
Hy everyone, I just installed Ubuntu on my computer (deleting W10) and this one is now silenced... ^^

I searched on many forums and subjects but everything I already tried didn't work at all...

The speakers and jack port aren't working and here are the error messages I get:

```
sylvain@sylvain-EZbook:~$ pulseaudio
W: [pulseaudio] pid.c: Stale PID file, overwriting.
Killed

sylvain@sylvain-EZbook:~$ pulseaudio --start
E: [pulseaudio] main.c: Daemon startup failed.

sylvain@sylvain-EZbook:~$ /sbin/lsmod | grep snd
snd_soc_sst_bytcr_rt5651    20480  0
snd_intel_sst_acpi     16384  1
snd_intel_sst_core     53248  1 snd_intel_sst_acpi
snd_soc_sst_atom_hifi2_platform   102400  3 snd_intel_sst_core
snd_soc_acpi           16384  2 snd_soc_sst_bytcr_rt5651,snd_intel_sst_acpi
snd_soc_acpi_intel_match    20480  1 snd_intel_sst_acpi
snd_soc_rt5651         90112  2 snd_soc_sst_bytcr_rt5651
snd_soc_rl6231         16384  1 snd_soc_rt5651
snd_soc_core          241664  3 snd_soc_rt5651,snd_soc_sst_bytcr_rt5651,snd_soc_sst_atom_hifi2_platform
snd_hdmi_lpe_audio     24576  1
snd_compress           20480  1 snd_soc_core
ac97_bus               16384  1 snd_soc_core
snd_pcm_dmaengine      16384  1 snd_soc_core
snd_pcm                 98304  6  snd_soc_rt5651,snd_soc_sst_bytcr_rt5651,snd_hdmi_lpe_audio,snd_soc_sst_atom_hifi2_platform,snd_soc_core,snd_pcm_dmaengine
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                65536  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              32768  2 snd_seq,snd_pcm
snd                     81920  11  snd_seq,snd_seq_device,snd_timer,snd_compress,snd_hdmi_lpe_audio,snd_soc_sst_atom_hifi2_platform,snd_soc_core,snd_pcm,snd_rawmidi
soundcore              16384  1 snd



on alsamixer, I have nothing by default and when I go to the second  sound card, I can't increase sound on the headphone and speaker, this  one is blocked at the value of 0.

```
If anyone have an idea, thank you very much! :smile:

---

### Post by wildmanne39 on 2019-01-20
Hello and welcome to the forum!

*Thread moved to **Multimedia Software a more appropriate sub-forum**.*

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 

If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Thanks

---

