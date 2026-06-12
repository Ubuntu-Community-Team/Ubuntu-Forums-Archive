---
title: "skype and alsa"
date: 2007-03-22
forum: Multimedia &amp; Video
---

### Post by MadeR on 2007-03-22
From time to time when I try to start or to answer a call, skype tells me "problems with the audio device".

I'm using kubuntu, feisty fawn herd 5, the output of uname -a "is Linux silmarillion 2.6.20-12-generic #2 SMP Wed Mar 21 20:55:46 UTC 2007 i686 GNU/Linux", alsa is version 1.0.13, skype version is 1.3.0.53_API, sound in kde is enabled.

does anybody know the reason why this happens?

```
cat /dev/sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.14rc1 emulation code)
Kernel: Linux silmarillion 2.6.20-12-generic #2 SMP Wed Mar 21 20:55:46 UTC 2007 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
Intel ICH5 with ALC655 at 0xf2001000, irq 22
saa7133[0] at 0xf1026000 irq 21

Audio devices:
0: Intel ICH5 (DUPLEX)
1: SAA7134 PCM

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
31: system timer

Mixers:
0: Realtek ALC655 rev 0
1: SAA7134 Mixer
```



```
mader@silmarillion:~$ skype
ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix_format'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: Nessun file o directory
ALSA lib conf.c:3957:(snd_config_expand) Args evaluate error: Nessun file o directory
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM dmix:ICH5
```

---

