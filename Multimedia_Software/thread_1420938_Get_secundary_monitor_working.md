---
title: "Get secundary monitor working"
date: 2010-03-03
forum: Multimedia Software
---

### Post by Drejcek on 2010-03-03
Hi!

I just got secondary monitor and I can't get it working. My graphic card is Nvidia GF GTX260 and both monitors are from Samsung. Now I tried to enable new monitor with nvidia-settings and got this error:
[IMG]http://www.shrani.si/f/19/XD/QQi8nYN/error.png[/IMG]
at the same time terimanl gives me this error:
```
VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
Undefined Device "(null)" referenced by Screen "Default Screen".
```

What should I do?

---

### Post by Drejcek on 2010-03-04
Anyone?

---

### Post by realzippy on 2010-03-04
Open terminal:

[B]sudo rm /etc/X11/xorg.conf
[/B]
[B]sudo nvidia-xconfig
[/B]

...then parsing error is gone.

---

### Post by Drejcek on 2010-03-04
It worked. Thanks!

---

