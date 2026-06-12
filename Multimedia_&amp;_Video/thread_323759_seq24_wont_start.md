---
title: "seq24 wont start"
date: 2006-12-22
forum: Multimedia &amp; Video
---

### Post by jakonj on 2006-12-22
I downloaded se24 but i can`t start it!? I tried to launch it from terminal so i can see the error message and here it is:

krak@xubuntu:~$ seq24
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
snd_seq_open() error
krak@xubuntu:~$ 


What to do?

---

### Post by jakonj on 2006-12-22
fixed! i added snd_seq_oss in my /etc/modules

---

### Post by Daemon Mort on 2006-12-26
where did you find this file?

---

