---
title: "My headphones don't work in 11.10"
date: 2012-02-24
forum: Multimedia Software
---

### Post by Madonnas BoyToy on 2012-02-24
I've tried everything that I can find to fix this problem.
Each solution works for a short period of time but usually breaks after a reboot.
The laptop speakers work just fine, but the headphones don't produce any sound.

I'm on a Gateway MX7515.
lspci | grep -i audio
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)

Any help would be greatly appreciated.
I'm basically a beginner, so take it easy on me, please.
Thank you.

---

### Post by Rodney9 on 2012-02-25
> sudo apt-get install pavucontrol

PulseAudio Volume Control (pavucontrol) is a simple GTK+ based volume
control tool (mixer) for the PulseAudio sound server. In contrast to
classic mixer tools this one allows you to control both the volume of
hardware devices and of each playback stream separately. It also allows
you to redirect a playback stream to another output device without
interrupting playback.


Rodney

---

### Post by Madonnas BoyToy on 2012-02-25
> **Rodney9 said:**
> PulseAudio Volume Control (pavucontrol) is a simple GTK+ based volume
control tool (mixer) for the PulseAudio sound server. In contrast to
classic mixer tools this one allows you to control both the volume of
hardware devices and of each playback stream separately. It also allows
you to redirect a playback stream to another output device without
interrupting playback.


Rodney


Aha.  Well so far it seems to be working, so thank you very much, Rodney.
-MBT.

---

