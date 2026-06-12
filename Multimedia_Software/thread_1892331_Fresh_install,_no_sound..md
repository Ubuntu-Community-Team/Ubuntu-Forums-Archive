---
title: "Fresh install, no sound."
date: 2011-12-07
forum: Multimedia Software
---

### Post by code.1101 on 2011-12-07
I just installed Xubuntu 10.04 on a rather old PC (~5-6 yrs) and I can't get the sound working.
Nothing is muted in alsamixer but there's no output (see attached screenshots). 

Output of lspci -v:

```
02:07.0 Multimedia audio controller: ESS Technology ES1968 Maestro 2
    Subsystem: ESS Technology Device 0001
    Flags: bus master, medium devsel, latency 32, IRQ 19
    I/O ports at e800 [size=256]
    Capabilities: [c0] Power Management version 1
    Kernel driver in use: ES1968 (ESS Maestro)
    Kernel modules: snd-es1968, radio-maestro
```aplay -l:

```
**** List of PLAYBACK Hardware Devices ****
card 0: E2 [ESS ES1968 (Maestro 2)], device 0: ESS Maestro [ESS Maestro]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
```

---

### Post by editheraven on 2011-12-08
What ```
speaker-test
``` is telling?

Do you have pulseaudio server installed? If yes, it's better to remove it. I find alsa to be a lot better.

Try ```

killall pulseaudio
sudo alsa force-reload

```

---

### Post by code.1101 on 2011-12-08
Installed kubuntu 10.04 instead. No more pulseaudio, same problem though.

speaker-test:
```

speaker-test 1.0.22

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 128 to 65024
Period size range from 128 to 65024
Using max buffer size 65024
Periods = 4
was set period_size = 16256
was set buffer_size = 65024
 0 - Front Left
Time per period = 1.702477
 0 - Front Left
Time per period = 2.711265
 0 - Front Left
Time per period = 2.706301
 0 - Front Left
Time per period = 2.711261
 0 - Front Left
Time per period = 2.711309
 0 - Front Left
Time per period = 2.711277
 0 - Front Left
Time per period = 2.711292

```

---

