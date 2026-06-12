---
title: "problem running aticonfig"
date: 2006-08-25
forum: Multimedia &amp; Video
---

### Post by parrusete on 2006-08-25
Hi, I'm triying to run aticonfig but every time I have the same problem:

fran@parrusete:~$ sudo aticonfig --initial
Found fglrx primary device section
Nothing to do, terminating.

But i also have 3D acceleation so I thought all was allrigth with the drivers but it seem that no.

My card is a X1400 and if i should print any more information let me know

Thanks.

---

### Post by meng on 2006-08-25
What's the output of
fglrxinfo

---

### Post by whatever on 2006-08-25
> **parrusete said:**
> Hi, I'm triying to run aticonfig but every time I have the same problem:

fran@parrusete:~$ sudo aticonfig --initial
Found fglrx primary device section
Nothing to do, terminating.
i don't see any problem there

---

### Post by parrusete on 2006-08-26
the output of fglrxinfo is:

fran@parrusete:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400 Generic
OpenGL version string: 2.0.5814 (8.25.18)

but i don't know what I have changed becouse yesterday the first line "Xlib..." wasn't there.

For whatever:

   - Why you say, there is no problem with that output when running aticonfig, I would like to run it, but i can't so must be some problem, can you explain yourself please.

Thanks by yours reports.

---

### Post by parrusete on 2006-08-26
I have ansewered myself, what I was looking for was fireglcontrolpanel.

I'm sorry, Anaway thanks

---

