---
title: "Need help with fglrx/kernel 2.6.17.9"
date: 2006-08-21
forum: Multimedia &amp; Video
---

### Post by pravuil on 2006-08-21
I compiled kernel 2.6.17.9 with the fbsplash patch but forgot to install the ati driver before compiling. Does installing the ati driver before compiling a new kernel do anything?

I noticed an error when attempting to build the fglrx module. It kept on trying to make a symlink for /usr/src/kernel-headers-2.6.17.9/scripts/Makefile.lib.c. even though there was no such file for 2.6.17. I could install the ati driver just fine by using module-assistant on 2.6.15-26/23. Other than that error I couldn't really see any other problem.

Could someone suggest any idea on how to resolve this (preferably without the need to suggest using the base installation/configuration.)

---

### Post by pravuil on 2006-08-25
nevermind, needed to touch the header and kernel source files/make scripts/, fixed the problem. Now I got to figure out how to do the same thing with nvidia. Probably can be resolved the same way. Only one way to find out.

---

