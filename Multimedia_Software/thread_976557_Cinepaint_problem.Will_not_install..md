---
title: "Cinepaint problem.Will not install."
date: 2008-11-09
forum: Multimedia Software
---

### Post by fidde88pven on 2008-11-09
Hi!

Ubuntu 8.10, cinepaint 0.22-1.

./configure --- Works
make --- Errors
Make install --- Error.


This is the error:
```
libtile.c:294: fatal error: opening dependency file .deps/libtile.Tpo: Permission denied
compilation terminated.
make[3]: *** [libtile.lo] Fel 1
make[3]: Lämnar katalogen "/home/fredrik/Skrivbord/cinepaint-0.22-1/lib/wire"
make[2]: *** [all-recursive] Fel 1
make[2]: Lämnar katalogen "/home/fredrik/Skrivbord/cinepaint-0.22-1/lib"
make[1]: *** [all] Fel 2
make[1]: Lämnar katalogen "/home/fredrik/Skrivbord/cinepaint-0.22-1/lib"
make: *** [all-recursive] Fel 1

```


libtile??

Hope someone can help. Regards Fredrik

---

### Post by fidde88pven on 2008-11-12
No one?

---

### Post by edgaruy1980 on 2008-11-14
I tried   too and didnt work, their website says they are working in new packages, I wonder if anyone has tried successfully to installed in this version 8.10 :(

---

### Post by stoneage on 2008-11-29
Have you tried installing the experimental .debs from the Cinepaint website?

---

