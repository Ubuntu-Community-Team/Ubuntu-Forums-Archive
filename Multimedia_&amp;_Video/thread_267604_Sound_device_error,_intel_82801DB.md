---
title: "Sound device error, intel 82801DB"
date: 2006-09-28
forum: Multimedia &amp; Video
---

### Post by rovar on 2006-09-28
I went through the comprehensive sound problems guide completely. Using the section "Using drivers from alsa-project" I configured, compiled and installed the drivers successfully. 

I used intel8x0 as that seemed to be the closest match. 

modprobe snd-inted8x0 worked properly. 

however.. attempting to run alsamixer resulted in: alsamixer: function snd_ctl_open failed for default: No such device

here is output from aadebug:
Kernel ----------------------------------------------------
Linux char-desktop 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686 GNU/Linux

Loaded Modules --------------------------------------------
snd_intel8x0           34076  0
snd_ac97_codec         96676  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            47648  0
snd_mixer_oss          18816  1 snd_pcm_oss
snd_pcm                81032  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              24964  1 snd_pcm
snd_page_alloc         10760  2 snd_intel8x0,snd_pcm
snd                    56164  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer

Modprobe Conf ---------------------------------------------
Warning: module config file does not exist
This means any kernel modules will not be auto loaded
See your linux distro docs on how to create this file

Proc Asound -----------------------------------------------
Advanced Linux Sound Architecture Driver Version 1.0.12.
Compiled on Sep 28 2006 for kernel 2.6.15-27-386.
 0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                      Intel 82801DB-ICH4 with AD1981B at 0xffa20400, irq 201
  0: [ 0]   : control
 16: [ 0- 0]: digital audio playback
 20: [ 0- 4]: digital audio playback
 24: [ 0- 0]: digital audio capture
 25: [ 0- 1]: digital audio capture
 26: [ 0- 2]: digital audio capture
 27: [ 0- 3]: digital audio capture
 33:        : timer
cat: /proc/asound/hwdep: No such file or directory
00-04: Intel ICH - IEC958 : Intel 82801DB-ICH4 - IEC958 : playback 1
00-03: Intel ICH - ADC2 : Intel 82801DB-ICH4 - ADC2 : capture 1
00-02: Intel ICH - MIC2 ADC : Intel 82801DB-ICH4 - MIC2 ADC : capture 1
00-01: Intel ICH - MIC ADC : Intel 82801DB-ICH4 - MIC ADC : capture 1
00-00: Intel ICH : Intel 82801DB-ICH4 : playback 1 : capture 1
cat: /proc/asound/seq/clients: No such file or directory

Dev Snd ---------------------------------------------------
controlC0  pcmC0D0c  pcmC0D0p  pcmC0D1c  pcmC0D2c  pcmC0D3c  pcmC0D4p  timer

CPU -------------------------------------------------------
model name      : Intel(R) Pentium(R) 4 CPU 2.00GHz
cpu MHz         : 2000.413

RAM -------------------------------------------------------
MemTotal:      1035592 kB
SwapTotal:     1622524 kB

Hardware --------------------------------------------------
0000:00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)


Any hints, suggestions, etc would be much appreciated. 

Thanks

---

