---
title: "Problems with sound"
date: 2013-04-02
forum: Multimedia Software
---

### Post by matheast on 2013-04-02
I'm using Kubuntu, version 12.10. Using ALSA, pulseaudio is not installed. I have two sound cards, Echo Layla 24 and motherboards sound device:
```

08:00.0 Multimedia controller: Motorola DSP56361 Digital Signal Processor (rev 01)
        Subsystem: Echo Digital Audio Corporation Layla24
        Flags: bus master, medium devsel, latency 192, IRQ 16
        Memory at fbe00000 (32-bit, non-prefetchable) [size=1M]
        Kernel driver in use: snd_layla24
        Kernel modules: snd-layla24

00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
        Subsystem: ASUSTeK Computer Inc. Device 8357
        Flags: bus master, fast devsel, latency 0, IRQ 69
        Memory at f7ff8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities:
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd-hda-intel
 
``` 

```

$ uname -a
Linux studio 3.5.0-26-generic #42-Ubuntu SMP Fri Mar 8 23:18:20 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

``` 

Sometimes applications (vlc, youtube in firefox...) don't produce sound at all. Sometimes they (at least youtube, not sure about other) play back at reduced (half?) speed. On rare occasion sounds actually work normally. Wether or not sounds work doesn't change while computer is on, only when rebooting. With the exception that if things play at reduced speed, sometimes they start playing at normal speed after the computer has been on for a while (some hours). 

However, when I open KMix and go to Settings -> Audio Setup, choose right device and press test, it seems to always work with Intel card, but not with Layla.  alsamixer on terminal doesn't work. Doesn't work even with sudo.

```

$ alsamixer
cannot open mixer: No such file or directory

$ alsamixer -a basic
ALSA lib python.c:991:(alsa_mixer_simple_finit) Unable to find python module '/usr/lib/x86_64-linux-gnu/alsa-lib/smixer/python/main.py' cannot open mixer: No such device

```

---

### Post by matheast on 2013-04-04
Now sounds started to work after computer being on for few hours.

KMix -> Settings -> Audio Setup and Test sound doesn't work on layla24, though vlc works. alsamixer on terminal works.

---

