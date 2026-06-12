---
title: "how to enable soft synth"
date: 2007-05-19
forum: Multimedia Production
---

### Post by tko829 on 2007-05-19
Hey all,
So, after much bumping around and reading and rereading. (sigh) I have managed to make US work with my mpu 401 connected midi keyboard and sound canvas. But, how can I get a soft synth to work properly? When I cat /proc/asound/oss/sndstat I get:

> Sound Driver:3.8.1a-980706 (ALSA v1.0.14rc1 emulation code)
Kernel: Linux ubuntustudio 2.6.20-15-lowlatency #2 SMP PREEMPT Sun Apr 15 07:39:03 UTC 2007 i686
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
Intel 82801DB-ICH4 with ALC202 at 0xffa7f800, irq 21
Yamaha DS-1 (YMF724F) at 0xff8f8000, irq 18

Audio devices:
0: Intel 82801DB-ICH4 (DUPLEX)
1: YMFPCI (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices:
1: Yamaha DS-1 (YMF724F) MIDI

Timers:
31: system timer

Mixers:
0: Realtek ALC202 rev 0
1: SigmaTel STAC9704

What do I need to do to make the Synth Devices line show a synth? Or am I barking up the wrong tree?:confused: I can make my midi keyboard play through my computer to my sound canvas. I can also make rosegarden play to my sound canvas. If I use Qsynth and get my JACK connections correct, the midi keyboard sends signal to Qsynth (I can see the green light blink and the meters bounce) but get no sound from my speakers. If you have any ideas or need more info, let me know thanks!

---

### Post by kayosiii on 2007-05-24
Just checking but do you have a soundfont loaded into qsynth?

---

