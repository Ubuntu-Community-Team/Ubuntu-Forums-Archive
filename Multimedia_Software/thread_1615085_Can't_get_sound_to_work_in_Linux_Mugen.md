---
title: "Can't get sound to work in Linux Mugen"
date: 2010-11-06
forum: Multimedia Software
---

### Post by blazini on 2010-11-06
I've tried just about everything I can to get sound working through Pulseaudio (and disabling) For Mugen on my Acer revo but I can't figure it out. Sounnd works fine for everything other than this game. Running Lucid on this machine and Karmic on my main desktop. Sound works Fine on my Karmic machine. I've tried the windows versions of Mugen and Jmugen but they don't run well or at all.

running lsof in a separate terminal with mugen running:
> jmoney@jmoney-Revo:~/mugen/mugen2$ lsof /dev/dsp* /dev/audio* /dev/mixer* /dev/snd/*
COMMAND    PID   USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
pulseaudi 1186 jmoney   37u   CHR  116,9      0t0 4535 /dev/snd/controlC0
3         2165 jmoney    6w   CHR   14,3      0t0 4531 /dev/dsp
3         2166 jmoney    6w   CHR   14,3      0t0 4531 /dev/dsp
3         2167 jmoney    6w   CHR   14,3      0t0 4531 /dev/dsp


Which I suppose means it's trying to access the card directly with OSS. I get the same output no matter how I configure the sound in Mugen. I tried launching it with padsp ./mugen, still no sound and same output. I installed all alsa/OSS/pulseaudio packages that my Karmic machine has with no difference. Not sure where else I should be looking.

---

### Post by lidex on 2010-11-06
Scroll down to this heading:
```
No sound or stuttering sound in SDL-based games
```
on this page:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)
and see if it helps.

---

### Post by Whiteulver on 2011-12-12
I use Debian and i solved the problem by installing oss.

Oss creates /dev/dsp devices needed by mugen to work with sound.

Also set ```
WavDevice = OSS
``` to your mugen.cfg file

---

