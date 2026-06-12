---
title: "MPlayer has broken A/V sync when using channels 6"
date: 2009-03-08
forum: Multimedia Software
---

### Post by Pitel on 2009-03-08
I guess the title summarize my problem -- whenever I start h264 film and I want to listen to it in surround sound, it gets out of A/V sync in parts with lot of movement. Starting titles from [The Big Bang Theory](http://en.wikipedia.org/wiki/The_Big_Bang_Theory) is a good example, or some in-jungle run in [Lost](http://en.wikipedia.org/wiki/Lost_(TV_series)). When I don't pass -channels 6 parametr to MPlayer, it's fine. It's not caused by slow CPU, it has ~20% usage.

There is my config:
```

subcp=enca:cs:cp1250
ao=alsa
fontconfig=1
vo=gl:osdcolor=0xffff80:lscale=1:yuv=3:cscale=1
font="DejaVu Sans"
monitoraspect=5:4
subfont-text-scale=3
cache=8192
fixed-vo=1
double=1
dr=1
softvol=1
softvol-max=1000
vf=pp=ac
lavdopts=threads=2

```

MPlayer (latest from intrepid repository):
```

MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz (Family: 6, Model: 23, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

```

I'm using Ubuntu 8.10, my sound card is SB Live! 5.1 (emu10k1), I've removed Pulseaudio.

---

