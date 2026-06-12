---
title: "Pulseaudio + applications using alsa = segmentation fault"
date: 2008-06-27
forum: Multimedia Software
---

### Post by barisurum on 2008-06-27
I choose pulseaudio as sound server in System/Preferences/Sound, because it gives a much clearer sound from my usb-audio device, but applications that use alsa as sound server fail or give segmentation faults. Amarok when using pulseaudio runs perfectly. All the alsa inputs and outputs are shown in pulseaudio's manager as Default sink or source, so what is the problem?

---

### Post by barisurum on 2008-06-29
bump

---

### Post by xak on 2009-07-09
I'm also experiencing segfaults, but mine occur when another application uses ALSA while pulseaudio is playing.  Specifically, I'm playing music with rhythmbox through pulseaudio and whenever Pidgin makes a sound (send/receive IM, etc) it causes pulseaudio to segfault and rhythmbox stops playing.  Pidgin plays its sound successfully.

Log from /var/log/messages and /var/log/kern.log:
```
Jul  6 15:08:02 xak kernel: [73151.790563] pulseaudio[9559]: segfault at 7f7a2a7b95b5 ip 00007f7a2a7b95b5 sp 00007f7a29d99f40 error 14 in module-alsa-sink.so[7f7a2a9cf000+2000]
```

Versions:
```
Pulseaudio 1:0.9.15-3ubuntu1~ppa2
Alsa 1.0.18.dfsg-1ubuntu8
Pidgin 1:2.5.8-1ubuntu2~pidgin1.9.04
GStreamer: 0.10.22-5
Kernel 2.6.28-13-generic
```

This is on the system in my sig.

---

