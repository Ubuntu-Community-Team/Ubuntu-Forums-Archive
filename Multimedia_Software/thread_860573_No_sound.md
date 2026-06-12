---
title: "No sound"
date: 2008-07-15
forum: Multimedia Software
---

### Post by ADoades on 2008-07-15
My new install of Kubuntu 8.04 has got no sound, in the past it has detected and installed it first time.

any clues or help?

Andrew

---

### Post by Cone on 2008-07-15
No one can really help you unless you provide more details.

What kind of sound card do you have?

Have you tried going through the things in [this thread?]("http://ubuntuforums.org/showthread.php?t=205449")

---

### Post by ADoades on 2008-07-17
yes sorry,

I have a Dell Dimension 5150 and I am using the built in sound adaptors, I can't see any packages in apt for drivers etc.

Yes I have had a look trough that tread, but to no avail.

Andrew

---

### Post by Cone on 2008-07-17
Could you post the results of ```
lspci -v | grep Audio
```
and ```
aplay -l
```
as a starting point?

---

### Post by ADoades on 2008-07-17
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)


**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

---

