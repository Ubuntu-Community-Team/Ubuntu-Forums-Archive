---
title: "new  kernel update"
date: 2011-02-06
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by rburkartjo on 2011-02-06
ran safe update and installed the newest kernel no problems. still lots of x stuff held back.

---

### Post by zika on 2011-02-06
> **rburkartjo said:**
> ran safe update and installed the newest kernel no problems. still lots of x stuff held back.What does aptitude full-upgrade offers? **Do not accept (use q=quit)**, just to see what is the problem...

---

### Post by rburkartjo on 2011-02-06
two MYSQL updates and bunch of x stuff

---

### Post by zika on 2011-02-06
> **rburkartjo said:**
> two MYSQL updates and bunch of x stuffSorry, I was not precise enough: what are the „conflicts“...?

---

### Post by rburkartjo on 2011-02-06
z- all having to do with the nvidia drivers.

---

### Post by rburkartjo on 2011-02-06
there is a note in one of the held back updates that installing will break x

---

### Post by zika on 2011-02-06
> **rburkartjo said:**
> z- all having to do with the nvidia drivers.I'm on ATI. That is our differentia specifica...
I was in a similar situation several testing periods ago... Be patient...
I do not use fglrx but...[http://ubuntuforums.org/showthread.php?t=1682128](http://ubuntuforums.org/showthread.php?t=1682128)

---

### Post by rburkartjo on 2011-02-06
tks z i have all the time in the world. i fixed it so i can access all programs that i have installed. i will just keep doing safe updates until all is fixed. also i use orphan to remove unneeded packages that dont affect my computer and ubuntu tweak to clean the system cache

---

### Post by zika on 2011-02-06
> **rburkartjo said:**
> tks z i have all the time in the world. i fixed it so i can access all programs that i have installed. i will just keep doing safe updates until all is fixed. also i use orphan to remove unneeded packages that dont affect my computer and ubuntu tweak to clean the system cacheGood (and safe (pun intended)) plan!

---

### Post by odysseusjak on 2011-02-06
The new kernel is supposed to be installed but it is not showing in the menu when I boot the system. Any thoughts?

---

### Post by cariboo on 2011-02-06
Open a terminal and run:

```
sudo update-grub
```

It should show up in the list.

---

### Post by odysseusjak on 2011-02-06
Awesome! That did it. Thanks.

---

