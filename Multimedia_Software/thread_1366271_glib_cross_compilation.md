---
title: "glib cross compilation"
date: 2009-12-28
forum: Multimedia Software
---

### Post by shariefbe on 2009-12-28
i am compilaing and glib for my ARM baord and i am getting one error
see```

checking for format to printf and scanf a guint64... none
checking for an ANSI C-conforming const... yes
checking if malloc() and friends prototypes are gmem.h compatible... yes
checking for growing stack pointer... configure: error: in `/mnt/freescale/sources/glib-2.22.0':
configure: error: cannot run test program while cross compiling
See `config.log' for more details.
Configuration of glib library  has failed
sharief@sharief-desktop:/mnt/freescale/sources/glib-2.22.0$
```
can anyone help me..what is this? and how to clear that?

---

### Post by shariefbe on 2010-01-01
it works fine for me. now when i tried to compile again i am getting the following error

```
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for pkg-config... /mnt/freescale//toolchain/bin//pkg-config
configure: error: *** pkg-config too old; version 0.16 or better required.
Configuration of glib library  has failed
sharief@sharief-desktop:/mnt/freescale/sources/glib-2.22.0$ 

```
   Can anyone help me

---

