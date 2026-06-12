---
title: "sound gone after second reboot"
date: 2011-11-14
forum: Multimedia Software
---

### Post by zaibotrenktas on 2011-11-14
Hello,

I installed ubuntu and there was no sound. After rebooting sound appeared. But after rebooting again sound was gone. I tried sound troubleshooting on ubuntu wiki, but it didn't helped. Have you got any ideas?

Ubuntu 10.04.3
Asus N73Jn

---

### Post by inobe on 2011-11-14
[http://ubuntuforums.org/showthread.php?t=1880245](http://ubuntuforums.org/showthread.php?t=1880245)

someone with a similar problem solved the issue today.

post #11 was the fix.

---

### Post by zaibotrenktas on 2011-11-14
> **inobe said:**
> [http://ubuntuforums.org/showthread.php?t=1880245](http://ubuntuforums.org/showthread.php?t=1880245)

someone with a similar problem solved the issue today.

post #11 was the fix.

There is PulseAudio sound system in my startup applications and pulse audio is running in system monitor > processes. So I don't think it is solution for my problem.

---

### Post by inobe on 2011-11-14
can you not post the log?

---

### Post by zaibotrenktas on 2011-11-15
The sound was appeared once again, but just until next reboot. And an interesting thing is that now my boot screen looks like this:

Ubuntu, Linux 26. 32-35
.. recovery
Ubuntu, Linux 26. 32-33
.. recovery
Windows Vista
Windows 7

The funny thing is that I don't have Vista. By the way, I use installed ubuntu using wubi.

---

### Post by zaibotrenktas on 2011-11-17
If I put a this command in the terminal:
```
aplay -l | grep card

```

I got:
```
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
card 0: Intel [HDA Intel], device 1: ALC269 Digital [ALC269 Digital]
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]

```

Is it ok? It's just suspicious for me to have three cards on card 0 slot. Maybe that's the problem?

---

