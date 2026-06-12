---
title: "K9copy DVD authoring mode crash on video addition"
date: 2008-11-26
forum: Multimedia Software
---

### Post by pxc on 2008-11-26
With any video file on Kubuntu 8.10 x86_64, K9copy consistently crashes upon adding a video file in order to create a DVD.

Here's the debug information given to me in the KDE crash handler.
```
Application: k9copy (k9copy), signal SIGSEGV
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0x7f3456d1f6f0 (LWP 12049)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#5  0x00007f345600ac80 in KUrlCompletion::staticMetaObject ()
   from /usr/lib/libkio.so.5
#6  0x00007f3456d23360 in ?? ()
#7  0x0000000000513fd0 in ?? ()
#8  0x0000000001fe6080 in ?? ()
#9  0x00000000f2c015a0 in ?? ()
#10 0x00007f3456b4b056 in ?? () from /lib64/ld-linux-x86-64.so.2
#11 0x00007f3456b4b29e in ?? () from /lib64/ld-linux-x86-64.so.2
#12 0x000000010000001f in ?? ()
#13 0x0000000000000001 in ?? ()
#14 0x0000000000000000 in ?? ()
#0  0x00007f345336e5f0 in nanosleep () from /lib/libc.so.6

```Additional information...
```
pxc@cooldude:~/Videos/movies$ uname -a
Linux cooldude 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:06 UTC 2008 x86_64 GNU/Linux
```

The error occurs with the default version of K9Copy (2.0.2) as well as the latest from getdeb.net (2.1.0). Removing the K9Copy configuration files does not solve the problem.

---

### Post by jondecker76 on 2008-11-28
I haven't debugged anything, but ever since moving to 0810, K9Copy will not work for me either with any DVD that I have tried (trying to rip a DVD to .iso).
It always worked fine for me in the past.

Hopefully someone will figure it out soon

---

