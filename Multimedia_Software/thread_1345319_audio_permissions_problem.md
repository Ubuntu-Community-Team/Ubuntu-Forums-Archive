---
title: "audio permissions problem"
date: 2009-12-03
forum: Multimedia Software
---

### Post by trickykungfu on 2009-12-03
I just installed a big update package, including a kernel update, for Ubuntu Jaunty, and now my sound is broken.  I believe it is a permissions problem.  When i do aplay -l, i get no soundcards found, but if i sudo aplay -l, i get
```
jeeves@jeeves:~$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
E: core-util.c: Home directory /home/jeeves not ours.
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

So I am fairly sure it's a permissions problem of some sort, but I have no idea how to fix it.  Help?

---

