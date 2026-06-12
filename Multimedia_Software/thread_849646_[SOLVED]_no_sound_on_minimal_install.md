---
title: "[SOLVED] no sound on minimal install"
date: 2008-07-04
forum: Multimedia Software
---

### Post by markp1989 on 2008-07-04
i followed this guide 
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems) 

and installed a minimal 64bit hardy with openbox. I have installed rhythmbox, and needed codecs, but i have no sound in any programs.

am i missing something simple here?  Because sound works fin with a full hardy install.

Thanks Markp1989

---

### Post by regomodo on 2008-07-04
`

---

### Post by kerry_s on 2008-07-04
you need to install alsa first:
**sudo apt-get install alsa-base alsa-utils alsa-oss**

double check the packages, i'm on win2k so i can't look.

---

### Post by markp1989 on 2008-07-04
> **regomodo said:**
> as root (or sudo -i)

$ alsaconf
$ alsamixer
$ alsactl store

That last one may be a little wrong. I'm in Xp atm so can't check.

tried it and i get this: 

```
root@markspc:~# alsaconf
bash: alsaconf: command not found
root@markspc:~# 
```

---

### Post by urukrama on 2008-07-04
Once you have installed the packages kerry_s mentioned, you probably have to unmute the volume. To do so, type "alsamixer" in a terminal, and then press "M" to unmute each channel (use the arrows to cycle through the different channels)

---

### Post by markp1989 on 2008-07-04
> **urukrama said:**
> Once you have installed the packages kerry_s mentioned, you probably have to unmute the volume. To do so, type "alsamixer" in a terminal, and then press "M" to unmute each channel (use the arrows to cycle through the different channels)

That was the fastest fix ever , thank you all for your help

---

### Post by regomodo on 2008-07-04
`

---

### Post by Tanker Bob on 2008-07-04
> **urukrama said:**
> Once you have installed the packages kerry_s mentioned, you probably have to unmute the volume. To do so, type "alsamixer" in a terminal, and then press "M" to unmute each channel (use the arrows to cycle through the different channels)

Worked perfectly, thanks!

---

### Post by K.Mandla on 2008-07-04
Moved to Multimedia and Video.

---

