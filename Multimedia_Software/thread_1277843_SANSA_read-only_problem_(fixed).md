---
title: "SANSA read-only problem (fixed)"
date: 2009-09-28
forum: Multimedia Software
---

### Post by tv0571 on 2009-09-28
I have a SANSA Fuze, configured with firmware upgrade and set to MSC.  The device is connected via a powered USB hub (which is actually a factor sometimes in troubleshooting USB stuff).

The device would mount, and could be read.  However, it would (often) not allow writing.  SUDO CHMOD commands were ignored ("read-only device").  

In browsing /media I noticed that there were multiple Fuze's listed, while my device was unmounted and not connected.  A SANSA FUZE_ and SANSA FUZE__ were there, both with "no read" icons.  Using Nautilus (file browser) I deleted both of these.

Since then it is has been working OK.  I'll post back here if I learn more about it.

---

