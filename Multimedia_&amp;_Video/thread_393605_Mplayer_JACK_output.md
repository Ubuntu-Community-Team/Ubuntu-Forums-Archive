---
title: "Mplayer JACK output"
date: 2007-03-25
forum: Multimedia &amp; Video
---

### Post by louman on 2007-03-25
Lately I've been using an external USB synthesizer as my main soundcard in ubuntu (much better  than my onboard) but a lot of apps I use don't support JACK, which is the only way (and the preferable way) to get audio output.

The one app that I really wish worked with JACK (out of the box) was Mplayer. I really want JACK audio output with mplayer, but I don't want to compile mplayer myself. Does anyone know of a binary .deb of mplayer that contains support for JACK (ala mplayer -ao jack) ?

I can't find any related topics about this -- perhaps it's just me?

I'm running Edgy:

> $ mplayer -ao help
MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm)  (Family: 6, Model: 10, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.


Available audio output drivers:
        mpegpes DVB audio output
        oss     OSS/ioctl audio output
        alsa    ALSA-0.9.x-1.x audio output
        arts    aRts audio output
        esd     EsounD audio output
        nas     NAS audio output
        sdl     SDLlib audio output
        null    Null audio output
        pcm     RAW PCM/WAVE file writer audio output

Cheers,
 -louman

---

### Post by louman on 2007-05-22
shameless bump?
surprisingly, I've yet to find a solution that doesn't involve compiling my own mplayer package, and I'm now using Feisty.

Maybe I ought to consider this a bug? After all, I certainly *have* JACK support, but mplayer doesn't come packaged with it because of dependency politics, I assume.

---

### Post by th0mas on 2007-05-31
what was your solution to have jack with mplayer at the end ?
i'm using feisty and mplayer is not compiled with jack :

```

~$ mplayer -ao help
MPlayer 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.80GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Available audio output drivers:
        oss     OSS/ioctl audio output
        alsa    ALSA-0.9.x-1.x audio output
        arts    aRts audio output
        esd     EsounD audio output
        pulse   PulseAudio audio output
        sdl     SDLlib audio output
        mpegpes DVB audio output
        null    Null audio output
        pcm     RAW PCM/WAVE file writer audio output

```

---

### Post by HellMind on 2007-10-28
Same here i cant enable jack on mplayer gutsy

---

