---
title: "Sound problem in Ubuntu 10.04"
date: 2010-07-28
forum: Multimedia Software
---

### Post by anup.techonly on 2010-07-28
Hi,

I don't have any sound in my machine. I am using Ubuntu 10.04. 

Some sample tests to make you acquainted with my system...

```
anup@anup-desktop:~$ sudo cat /dev/sndstat 
Sound Driver:3.8.1a-980706 (ALSA v1.0.23 emulation code)
Kernel: Linux anup-desktop 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:20:59 UTC 2010 x86_64
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
HDA Intel at 0xe0220000 irq 31

Audio devices:
0: STAC92xx Analog (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
7: system timer

Mixers:
0: SigmaTel STAC9227

```

Alsamixer settings are attached...

I played with it for some time...once I tried to remove pulseaudio ad re-install it.. after that sound icon is missing from top panel...

please help...

---

### Post by anup.techonly on 2010-07-29
By the way, I am using Zenith PC...

```
anup@anup-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by P4man on 2010-07-29
Not really my area of expertise, but if you open the sound preferences and go in to "hardware", what profile do you have selected?

---

### Post by anup.techonly on 2010-07-29
thanks..

I selected Analog Stereo Duplex in Hardware

---

### Post by anup.techonly on 2010-07-29
The problem is solved.../usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz mentions options snd-hda-intel model in /etc/modprobe.d/alsa-base.conf


I tried them one by one and reloaded alsa with sudo alsa force-reload

I succeeded with red-no-jd

thanks everyone....:D

---

### Post by jeetendra.choudhary on 2010-10-02
Hey Anup,

Thanks same worked for me also. My laptop suddenly become dumb after restarting and i was trying to solve that  and it worked like charm.

Regds
Jeetendra

---

