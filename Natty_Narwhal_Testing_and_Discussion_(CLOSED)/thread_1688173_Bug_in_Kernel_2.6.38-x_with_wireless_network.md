---
title: "Bug in Kernel 2.6.38-x with wireless network"
date: 2011-02-15
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by SickSnickers on 2011-02-15
Hello there.
I've got an annoying problem since I upgraded from 2.6.37-12 to 2.6.38-x wich is frustrating me:
The internet connection is limited to about 137 kb/s with kernel 2.6.38-x but I got 702 kb/s with 2.6.37-12 and lower. Fortunately 2.6.38 fixed the random kernel crash at boot time.
I installed the maverick (2.6.35-x) to solve that problem temporary, but the random error accurs again and that keeps a bit confusing me (cause maverick doesn't crash on my machine).

**The hardware I use:**
Laptop Samsung R780 with
nvidia gf 330gt
wireless ath9k driver
intel core i5-430
4GB Ram
(more I won't list, cause everything except the wireless works very fine with 2.6.38-x (compositing, sound, VirtualBox, etc))

So are there any workarounds or fixes to handle that? (Note: 2.6.38-3 didn't fix that too)

Greetz
-SickSnickers

---

### Post by cariboo on 2011-02-15
There is a possible solution in [this]("http://ubuntuforums.org/showthread.php?t=1682388&page=2") thread

---

### Post by SickSnickers on 2011-02-15
Hello cariboo907.
Thx for that reply. It solves my problem with connection speed on linux 2.6.38-3.
I simply added/created **ath9k.conf** in **/etc/modprobe.d** 
```
options ath9k nohwcrypt=1
```
and it helped, so I thank you again that the long journey through possible fixes (I tried a lot of things) ends here. 

Now everything is fine.

-SickSnickers

---

### Post by levk on 2011-04-18
I wouldn't call this [SOLVED], it's a workaround. Whenever they fix hardware encryption you should turn it back on.

---

### Post by dino99 on 2011-04-18
> **levk said:**
> I wouldn't call this [SOLVED], it's a workaround. Whenever they fix hardware encryption you should turn it back on.

and run into a terminal: ubuntu-bug linux

---

