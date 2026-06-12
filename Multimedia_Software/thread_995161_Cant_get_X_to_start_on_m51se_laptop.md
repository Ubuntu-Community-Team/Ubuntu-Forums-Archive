---
title: "Cant get X to start on m51se laptop"
date: 2008-11-27
forum: Multimedia Software
---

### Post by Baegel on 2008-11-27
Hi!
Ive been searching like a crazy person on both the internet and this forum for a solution but i cant find anything...
Anywho my problem is i cant start X. it says no video ram detected, and screen found but not configured. i have installed with the alternative installation cd. Im running a m51se-as121c laptop with the mem=2900MB parameter in grub. attaching log and xorg.conf
/Baegel

---

### Post by cariboo on 2008-11-27
You don't need the memory directive in grub.

If you start in recovery mode can you paste the output of:

```
sudo lshw -C video > video.txt
```

this will create a text file of your the viedo hardware information, that you can include in your next post.

Jim

---

### Post by Baegel on 2008-11-27
Thx for answering, heres the file you asked for. hope it helps
/Baegel

saw that the log was empty so here's a new one :P

---

