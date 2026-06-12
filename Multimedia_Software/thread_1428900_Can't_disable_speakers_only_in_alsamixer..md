---
title: "Can't disable speakers only in alsamixer."
date: 2010-03-13
forum: Multimedia Software
---

### Post by TheSkax on 2010-03-13
Hey there,

im using speakers as well as headphones with alsa.
When both are plugged in, both play sounds simultaneously.
Problem is, I cant deactivate the speakers only in alsamixer. :-?
In fact, I dont even find a entry for my speakers. The only entries not muted are Master, PCM, Headphones and Front. Front deactivates both speakers and headphones.

Any advice?

Max

---

### Post by Yellow Pasque on 2010-03-13
What kind of system are you using (i.e. model of laptop, system, or mobo)? Also, what's the output of:
```
aplay -l
```

---

### Post by TheSkax on 2010-03-13
Hi Temüjin,

aplay -l gives me this:

```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I'm on a Fujitsu Siemens desktop pc.

---

### Post by Yellow Pasque on 2010-03-14
Does your PC have a model name/number? I searched around a bit, but didn't see anything applicable.

---

