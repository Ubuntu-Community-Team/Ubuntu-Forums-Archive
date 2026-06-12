---
title: "Sound - Absent"
date: 2008-07-03
forum: Multimedia Software
---

### Post by ryan@pcwf on 2008-07-03
Hey guys, this is also my first post, so........Hello.

Anyways...

I have Ubuntu 8.04 currently installed, I have installed graphics and wireless drivers, but I need to use skype alot and i like to listen to music etc, I cant get my sound drivers sorted.  

Any Ideas?

My Motherboard is a Gigabyte S series M61P-S3.

Regards,

Ryan

---

### Post by MrClearPore on 2008-07-03
If you've never installed sound drivers before, try this:
```
apt-get install alsa-utils alsa-base
```

After those packages (and their dependencies) are installed, run the ALSA configuration program (as an administrator):
```
alsaconf
```

Follow the prompts.  ALSA should pick up your sound card(s).  If all goes well, you should then configure the proper volumes on the ALSA mixer:
```
alsamixer
```

Good luck.

P.S. If you're new to ALSA, it's pretty much the standard sound architecture for Linux now.  Go here for more info:
[http://www.alsa-project.org]("http://www.alsa-project.org")

---

### Post by Pjotr123 on 2008-07-03
Check this:
[http://ubuntutip.googlepages.com/sound](http://ubuntutip.googlepages.com/sound)

---

### Post by ryan@pcwf on 2008-07-03
Cheers guys, ill get on that now.

---

### Post by ryan@pcwf on 2008-07-03
Hey cheers fellas, worked wonders,

The only problem now is my mic has stopped working with skype, and ideas would be greatly appreciate it.

Regards,

---

