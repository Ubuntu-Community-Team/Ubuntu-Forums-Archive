---
title: "Alsa surround51 wierd behavior"
date: 2012-10-22
forum: Multimedia Software
---

### Post by PeterTaps on 2012-10-22
Folks,

I have two identical machines with identical hardware. Both the machines are running minimal Ubuntu 12.04.

The 3 audio line-outs from the rear panel are connected to a six speaker setup.

When I run speaker-test on one machine as follows, it works perfectly:

$ speaker-test -c 6 -Dsurround51 -t wav

I can hear each individual speaker just fine.

However, when I run the same command on the second machine, here is what happens:

1. Front-left output appears on front-left and rear-left speakers
2. Front-right output appears on front-right and rear-right speakers.
3. No audio output for center, rear-left, rear-right and LFE.

I am wondering if anyone has any idea on what could possibly be wrong with the second machine setup.

The machines have alsa setup only. Pulse has not been installed.

Thank you in advance for your help.

Regards,
Peter

---

