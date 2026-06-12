---
title: "HDA Intel ALC888 Sound stopped working"
date: 2010-08-17
forum: Multimedia Software
---

### Post by knichel on 2010-08-17
Recently my sound stopped working.  Sometimes when I boot up, I get the Kubuntu chimes when I log in sometimes not.  I tried going to the Multimeida options and running a test and sometimes it works sometimes not.  I am not a linux guru so if someone can help me I would be grateful.

It seems that if I reboot and try amarok, It will work.  The second multimedia app I try usually fails to produce sound and my Notifier tells me the HDA Intel sopped working....

The output of aplay -l is:
```

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```


Mike

---

