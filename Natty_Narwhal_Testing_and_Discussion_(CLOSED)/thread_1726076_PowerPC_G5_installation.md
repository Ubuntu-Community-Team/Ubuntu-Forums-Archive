---
title: "PowerPC G5 installation"
date: 2011-04-10
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by pauljwells on 2011-04-10
OK so this is where I am now with my G5 mac:
I can run the beta iso live, but the installer hangs reporting a 'Bad Mirror' even if I'm installing off-line - looks like it's trying to find some kind of hard-wired repository rather than lookin on the CD itself.
I can install 10.10, run the updates and then run th edist-upgrade. This gets me into 11.04 but I cannot boot the new kernel! It will only boot on the 10.10 kernel.
What's weird is that the 11.04 kernel shows as a shared library and not an executable. Do I need to have the 32 bit kernel loaded too and this calls the 64 bit as an .so ???

I filed a bug against ubuiquity for the installer problem.

Anyone else at all testing 11.04 on powerpc??

---

