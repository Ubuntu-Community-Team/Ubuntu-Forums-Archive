---
title: "All of a sudden no sound"
date: 2008-04-30
forum: Multimedia Software
---

### Post by xvedejas on 2008-04-30
I've been running hardy for a bit, and the sound has worked great. But today, when I get on my computer, it doesn't work at all. I haven't changed *anything*.

aplay -l gives me;

```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by garyedwardjohnston on 2008-04-30
What happens when you do hardware testing?

System > Administration > Hardware Testing

---

### Post by xvedejas on 2008-04-30
I don't hear any sound. I already tried this with system > preferences > sound.

---

### Post by xvedejas on 2008-04-30
What's weird is the live CD works with sound... what am I doing wrong? :confused:

---

### Post by xvedejas on 2008-04-30
This is sort of urgent, does nobody know why this is happening? :(

---

### Post by xvedejas on 2008-05-02
Nobody?

---

### Post by caeroe on 2008-05-02
Same here...  I had no issues in 7.10.

Logging in gives me a little static in the background.


**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by ChameleonDave on 2008-05-03
Type *alsamixer* at the command line.  Are you able to get your volume levels up?

---

