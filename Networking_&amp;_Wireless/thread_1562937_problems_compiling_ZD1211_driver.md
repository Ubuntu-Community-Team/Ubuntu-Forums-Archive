---
title: "problems compiling ZD1211 driver"
date: 2010-08-28
forum: Networking &amp; Wireless
---

### Post by accoustika on 2010-08-28
hello, i have ubuntu studio 10.04 installed and i'm trying to compile the wireless ZD1211 driver but i'm having quite some trouble for a while now and i can't seem to find an answer for my problem.
i followed the steps as mentioned in the user guide but i keep getting the same error: lib/modules/2.6.32-21-generic/build: No such file or directory

in the path lib/modules/ i found 2 folders, one is "2.6.31-10-rt" and inside it is a link folder called "build" and the other folder found in the modules folder is "2.6.32-21-generic" but inside it there is no folder called "build"

now i can't seem to find out whether my kernel is 2.6.31-10-rt or 2.6.32-21-generic since i have both.

in /usr/src/ i found 2 folders:
"linux-headers-2.6.31-10-rt" and "linux-rt-headers-2.6.31-10"

some help please!!

---

### Post by chili555 on 2010-08-28
Does the zd1211rw.ko module built in to your kernel not work correctly?> i can't seem to find out whether my kernel is 2.6.31-10-rt or 2.6.32-21-generic Please run the command:```
uname -r
```

---

