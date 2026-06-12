---
title: "mute tvtuner tvtuner at boot"
date: 2012-04-30
forum: Multimedia Software
---

### Post by kemsky on 2012-04-30
I would appreciate if someone also point me how to switch off tvtuner audio channel at boot time, the same as tvtime function MuteOnExit. 
I've configured module loopback as described here [http://linuxtv.org/wiki/index.php/Saa7134-alsa](http://linuxtv.org/wiki/index.php/Saa7134-alsa)

---

### Post by kemsky on 2012-05-05
second try

---

### Post by kemsky on 2012-08-30
third attempt

---

### Post by kemsky on 2013-03-17
one more attempt...

i've found that its possible to turn off source:
> set-source-mute alsa_input.pci-0000_0b_00.0.analog-stereo 1

but it is different from MuteOnExit from tvtime

---

