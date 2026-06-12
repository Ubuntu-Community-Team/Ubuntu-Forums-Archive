---
title: "Microphone Problem"
date: 2009-04-30
forum: Multimedia Software
---

### Post by bbourdet on 2009-04-30
Hello All -

I have been reading through these forum for the past few hours and cannot find my answer.

I have just recently upgraded from 8.10 to 9.04 and now my mic no longer works. I have tried just about everything to get it to work. I have tried the volume settings, I have tried downloading audacity, I have downloaded pavucontrol.

I cannot get this thing to work! Can anyone help?!

---

### Post by RipperHoss on 2009-04-30
> **bbourdet said:**
> Hello All -

I have been reading through these forum for the past few hours and cannot find my answer.

I have just recently upgraded from 8.10 to 9.04 and now my mic no longer works. I have tried just about everything to get it to work. I have tried the volume settings, I have tried downloading audacity, I have downloaded pavucontrol.

I cannot get this thing to work! Can anyone help?!It may be helpful if you could post your sound configuration.

In the terminal, type:
```
arecord -l
```

---

### Post by bbourdet on 2009-04-30
Sure! Sorry, I didint know about that. Here it is:

tark@tark-desktop:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
tark@tark-desktop:~$

---

### Post by msrinath80 on 2009-04-30
Yup, I think I know how to fix this. Install aumix (sudo apt-get install aumix) and turn up the slider to say 75% on IGain. That ought to fix it. Let us know if this works.

---

### Post by bbourdet on 2009-04-30
Thanks for that. I did download and install it, however it made no difference. I turned up to 75% and then up to 100%.

Any other thoughts?

---

### Post by bbourdet on 2009-05-01
Anyone else faced this problem?

---

### Post by bbourdet on 2009-05-01
No one else is having this problem?

---

