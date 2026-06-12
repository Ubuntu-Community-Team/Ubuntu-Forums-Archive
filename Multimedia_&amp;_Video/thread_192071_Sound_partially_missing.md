---
title: "Sound partially missing"
date: 2006-06-08
forum: Multimedia &amp; Video
---

### Post by syntern on 2006-06-08
Hello!

I have a tvtuner card (Pinnacle PCTV 110i), a soundcard (SB-like, old but works), and a motherboard integrated (disabled in bios) sound card (NVidia, Asus A8N-E). mpg321 plays music well, but Firefox does not produce any sound (Flash, Java), nor does tvtime (picture works). The sndstat is the following. Can you help me to let my system use only one soundcard? Thanks for your help

# cat /dev/sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.10rc3 emulation code)
Kernel: Linux aurora 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
Ensoniq AudioPCI ENS1371 at 0xa000, irq 66
MPU-401 UART at 0x330, irq 10
saa7133[0] at 0xd0000000 irq 74

Audio devices:
0: ES1371 DAC2/ADC (DUPLEX)
2: SAA7134 PCM

Synth devices: NOT ENABLED IN CONFIG

Midi devices:
0: ES1371
1: MPU-401 UART MIDI

Timers:
7: system timer

Mixers:
0: SigmaTel STAC9721,23
1: mixer10
2: SAA7134 Mixer

---

### Post by syntern on 2006-06-08
A little extension: mplayer plays movies with sound, totem (xine) does not.

---

