---
title: "New fglrx drivers?"
date: 2006-07-11
forum: Multimedia &amp; Video
---

### Post by SteinbergerNate on 2006-07-11
Noticed today that there is a new fglrx driver in the updates. Just wanting to know if anyone has had any trouble with those. It took me so long to get my drivers working properly that I don't want to install new ones until I know that they work properly.

---

### Post by lazyd2 on 2006-07-11
No problems here after the update.

---

### Post by loserboy on 2006-07-11
Edit: nm

---

### Post by matthew on 2006-07-11
There is a kernel update as well. I updated both at the same time and after rebooting everything worked perfectly for me with no hassle whatsoever.

---

### Post by SteinbergerNate on 2006-07-11
So fglrxinfo returned your card info and not mesa? (I hope I hope I hope :) ) I would really like an official fix instead of my duct-tape and cardboard type fix :)

---

### Post by matthew on 2006-07-11
> **SteinbergerNate said:**
> So fglrxinfo returned your card info and not mesa? (I hope I hope I hope :) ) I would really like an official fix instead of my duct-tape and cardboard type fix :)Yep. I did have them installed correctly and working before the update, though.
```
matt@telecaster:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 2.0.5814 (8.25.18)

matt@telecaster:~$ uname -a
Linux telecaster 2.6.15-26-686 #1 SMP PREEMPT Fri Jul 7 19:48:22 UTC 2006 i686 GNU/Linux


```

---

### Post by DoubtingThomas on 2006-07-11
I pray this will fix my issue of the DRI module crashing X *crosses fingers*

---

