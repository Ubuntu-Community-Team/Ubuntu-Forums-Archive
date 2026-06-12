---
title: "How to concatenate .avi.001 &amp; .avi.002 et cetera files?"
date: 2011-09-17
forum: Multimedia Software
---

### Post by Ederico on 2011-09-17
I've searched this online but I didn't manage to find the right answer to my query. I have some files ending in .avi.001, .avi.002 et cetera and I would like to concatenate them in one file so I can actually view them.

I didn't manage to find any workable solution.

I hope someone can help. Thanks beforehand!

---

### Post by Bonster on 2011-09-18
u need HJ-Split app, get the java version

---

### Post by vanadium on 2011-09-18
Depending on how the file was split, combining it might simply be a matter of
```

cat *.avi.* > combined.avi

```

---

### Post by psrdotcom on 2011-09-18
please download this link

[http://www.hjsplit.org/linux/](http://www.hjsplit.org/linux/)

run the file .. and concatenate files

---

### Post by Ederico on 2011-09-19
Hello everyone, I used the HJ-Split app and it worked for my purposes. Thanks a lot!

---

