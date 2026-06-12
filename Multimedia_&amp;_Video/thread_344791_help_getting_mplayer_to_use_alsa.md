---
title: "help getting mplayer to use alsa"
date: 2007-01-23
forum: Multimedia &amp; Video
---

### Post by Dillinger on 2007-01-23
I seem to be having a problem getting mplayer to use alsa.  

tyler@Spike:~$ mplayer -ao help
MPlayer 1.0rc1-4.1.2 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) XP 2600+ (Family: 6, Model: 8, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE
Available audio output drivers:
        oss     OSS/ioctl audio output
        mpegpes DVB audio output
        null    Null audio output
        pcm     RAW PCM/WAVE file writer audio output

As you can see alsa is not configured for mplayer and I'm not sure what to do, is there another package I need to install?

---

### Post by david_2001 on 2007-01-23
Did you compile this version of mplayer from source?  If so then it's possible that either the options passed to configure were not correct or not all of the build dependencies were present.  The standard Edgy mplayer package gives the following output:> 
david@darkstar:~$ mplayer -ao help
MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU:               Intel(R) Pentium(R) D CPU 2.80GHz (Family: 15, Model: 4, Stepping: 7)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
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

---

### Post by Dillinger on 2007-01-23
Solved.  I was using this script to install mplayerplug-in and for some reason it didn't compile alsa support, I redid the install with apt and it works fine now, thanks.

---

