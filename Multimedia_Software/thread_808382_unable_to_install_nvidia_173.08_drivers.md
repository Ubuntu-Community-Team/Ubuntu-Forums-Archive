---
title: "unable to install nvidia 173.08 drivers"
date: 2008-05-26
forum: Multimedia Software
---

### Post by damansandhu on 2008-05-26
hi , i am using ubuntu 8.04 and nvidia 9600 GT , i downloaded drivers from nvidia website and during installation i got this error "no precompiled kernel interface was found to match your kernel."

---

### Post by xc3RnbFO8P on 2008-05-26
Read this:
[http://www.linuxforums.org/forum/peripherals-hardware/122078-solved-cant-get-nvidia-9600-gt-drivers-installed.html]("http://www.linuxforums.org/forum/peripherals-hardware/122078-solved-cant-get-nvidia-9600-gt-drivers-installed.html")

---

### Post by damansandhu on 2008-05-27
it didn't helped me :(

---

### Post by briandu on 2008-05-28
just follow exactly:

[http://ubuntuforums.org/showthread.php?p=5064980#post5064980](http://ubuntuforums.org/showthread.php?p=5064980#post5064980) msg#430

Cheers

---

### Post by ~David on 2008-05-28
Neither of you read his first post correctly, he's not having problems with the drivers, he simply doesn't have the latest headers installed.

Damansandhu, run this in terminal:
```
sudo apt-get install build-essential linux-headers-`uname -r`
```

And then run the installer again.

---

