---
title: "i removed pulse audio now aplay doesnt work"
date: 2009-07-24
forum: Multimedia Software
---

### Post by markp1989 on 2009-07-24
I tried to set up pulse audio on my media pc, and decided it was too much trouble, so i removed it .

all other programs i have tried have sound, except for aplay.

what i try to run it from the command line. i get this error: 
```

mark@torrentslave:~$ aplay
ALSA lib pcm.c:2165:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
aplay: main:590: audio open error: No such file or directory
mark@torrentslave:~$ 
```

how do i tell aplay to use the original sound program?

Thanks Markp1989

---

### Post by igorzwx on 2009-07-24
It should be so.
I tried this too.
Eventually, I installed OSS4,
and all problems were solved.
I do not know if you hardware is supported by OSS4

read this:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

