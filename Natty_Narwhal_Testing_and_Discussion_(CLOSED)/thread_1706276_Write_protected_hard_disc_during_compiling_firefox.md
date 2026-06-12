---
title: "Write protected hard disc during compiling firefox"
date: 2011-03-13
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Sworddragon on 2011-03-13
I wanted to compile Firefox 4.0~rc1+build1+nobinonly-0ubuntu1 and used "apt-get build-dep firefox" and "apt-get source firefox --build". The compiling process was running ~1 hour and at the end I got a lot of error messages that some files couldn't be deleted. I figured out that I don't have write access anymore so I used "mount /dev/sda1 -oremount,rw". I got the error message that sda1 is write protected (I don't remember the exact message because I couldn't save the text).

I have compiled some months ago Firefox without a problem and the question is why the compiling proccess is acquiring a write lock on sda1? After a reboot I made the same steps again to go sure that it was because of the compiling process.

---

### Post by chrisccoulson on 2011-03-13
> **Sworddragon said:**
> I have compiled some months ago Firefox without a problem and the question is why the compiling proccess is acquiring a write lock on sda1? 

It's not. Your hard-drive is being remounted read-only because of a serious filesystem problem

---

### Post by Harry33 on 2011-03-13
This read-only mode is set in the fstab in cause of serious errors.
You can check it out.
See, you have this (for the root partition only) in your file /etc/fstab
```
UUID=*** / ext4 relatime,**errors=remount-ro**  0  1
```

---

### Post by Sworddragon on 2011-03-13
I have such an entry in /etc/fstab. Now I know an error occured during the compiling but the question is what caused the problem? sda1 has enough disk space (over 130 GB) so this isn't the problem. The compiling process happened in my home folder. I haven't an idea what's the error there.

---

