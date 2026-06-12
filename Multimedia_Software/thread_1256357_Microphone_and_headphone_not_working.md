---
title: "Microphone and headphone not working"
date: 2009-09-02
forum: Multimedia Software
---

### Post by hrafninn on 2009-09-02
I'm running Ubuntu 9.04 on a Dell Precision M4300. Sound is fine except that I can neither record sound using a microphone nor listen to sound using a headphone.

Here is some info:

1) lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

2) When I run alsamixer -V capture, it shows:
Card: HDA Intel
Chip: SigmaTel STAC9205

First Capture bar is 100<>100, the second 93<>93

Any suggestion?

---

