---
title: "wireles help"
date: 2010-01-18
forum: Networking &amp; Wireless
---

### Post by crazysilver69 on 2010-01-18
i just installed ubuntu 8 and cant get internet
when i go  to networks it doesnt show up wireless 
but under hardware test it finds the wireless card
its a belkin

---

### Post by bkratz on 2010-01-18
> **crazysilver69 said:**
> i just installed ubuntu 8 and cant get internet
when i go  to networks it doesnt show up wireless 
but under hardware test it finds the wireless card
its a belkin

Do you know which Belkin adaptor?

try in terminal
lspci
(that is LSPCI in lowercase)

---

### Post by crazysilver69 on 2010-01-18
im not sure but my friend had it working in ubuntu 9

---

### Post by bkratz on 2010-01-18
If you type in the command in the last post, it will tell us something like BCM43xx, that is what we need.

---

### Post by crazysilver69 on 2010-01-18
bcm4212

---

### Post by bkratz on 2010-01-18
> **crazysilver69 said:**
> bcm4212

Did you mean BCM4312?  If so, see this thread

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by Hogosha on 2010-01-18
is there any reason you are using 8.04/.10? i had a lot of problems with wireless till i got to 9.04.  If you can try using that.

---

### Post by crazysilver69 on 2010-01-18
if i use 9.04 my screen gets stuck on grub loading 
thats all it will say GRUB loading

---

### Post by bkratz on 2010-01-18
> **Hogosha said:**
> is there any reason you are using 8.04/.10? i had a lot of problems with wireless till i got to 9.04.  If you can try using that.

+1 I also only began to have good luck when I got to 9.04. If it because of the 8.04 being a long term release, the next LTS is due out in April 10.04 and you probably would have to end up doing a fresh install from something that old, but an upgrade would be available from more recent versions 9.10.

---

### Post by bkratz on 2010-01-18
> **crazysilver69 said:**
> if i use 9.04 my screen gets stuck on grub loading 
thats all it will say GRUB loading

Did you check to checksum (MD5) on the disk when you made it? Perhaps you just had a bad download. Always burn the disk at the slowest rate possible.

---

