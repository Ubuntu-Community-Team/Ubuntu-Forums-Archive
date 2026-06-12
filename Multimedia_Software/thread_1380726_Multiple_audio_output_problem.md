---
title: "Multiple audio output problem"
date: 2010-01-14
forum: Multimedia Software
---

### Post by TorontoStorm on 2010-01-14
I have a desktop computer, which has a audio output at the back, and one of the front (in addition to a microphone input at the back and front as well). The back works, but I can't get any audio out of the front. PulseAudio Volume Control only shows one output and alsamixer has nothing muted. 
Following are some terminal outputs that may be useful: 

```
tml@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
```
tml@ubuntu:~$ cat /proc/asound/modules
 0 snd_hda_intel
```
```
tml@ubuntu:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Jan  9 2010 for kernel 2.6.31-18-generic (SMP).
```
```
tml@ubuntu:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xe0200000 irq 28
```

Thanks for all the help in advance!

---

### Post by TorontoStorm on 2010-01-14
bump?

---

### Post by TorontoStorm on 2010-01-17
bump. no one has any idea on this problem? maybe i can provide some more info if its needed?

---

### Post by TorontoStorm on 2010-01-24
bump, haven't solved this yet

---

