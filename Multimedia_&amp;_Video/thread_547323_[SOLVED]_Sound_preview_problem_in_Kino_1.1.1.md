---
title: "[SOLVED] Sound preview problem in Kino 1.1.1"
date: 2007-09-09
forum: Multimedia &amp; Video
---

### Post by Irihapeti on 2007-09-09
I've managed to compile Kino 1.1.1 but I'm having some trouble with the sound preview. I get nothing at all out of the Alsa option, and if I choose OSS instead, it's choppy - cuts in and out rapidly. Previous versions of Kino have been fine.

Could anyone tell me what I should be looking at to get sound to work properly.

Irihapeti

---

### Post by Amazona aestiva on 2007-09-10
See the first link in my signature.

Find Kino. There is it in .deb!

---

### Post by Irihapeti on 2007-09-10
I discovered the .deb version of Kino 1.1.1 AFTER I'd done the compilation, and it's good to know it's there as an option. Thanks for pointing it out.

However, I also like to know how things work and to get them to work properly. And so, if there's something I can learn here about compiling from source, I'd still like to find an answer. (I guess if I weren't an investigator and a tinkerer, I'd never have stuck with Ubuntu.)

Thanks
Irihapeti

---

### Post by Amazona aestiva on 2007-09-11
The only problem usually that Kino need permission to /dev/raw1394.
The solution in my link too, at Kino's deb.

Compiling is something that usually fails... a program compilation is often difficult... We (I) need exact problem which We can solve. For example missing files, permissions etc.
So there isn't a way that solves everything.

---

### Post by Irihapeti on 2007-09-11
I've found the answer: a missing library. Seems to be working now.

Thanks

Irihapeti
:redface:

---

### Post by Amazona aestiva on 2007-09-12
Hmmm... a library?
 This wasn't a regular problem, because the package manager should automatically solve these things.

Good luck with Kino!

---

### Post by Irihapeti on 2007-09-12
> **Amazona aestiva said:**
> Hmmm... a library?
 This wasn't a regular problem, because the package manager should automatically solve these things.

Perhaps I should have been a bit more specific. I didn't have the necessary alsa libraries installed while compiling. I had assumed that if ./configure gets to the end, all is well. Not necessarily. When I ran it again, I spotted a warning about alsa libraries not being installed.

All in a good day's learning. Keeps the brain from rusting!:)

Irihapeti

---

### Post by Amazona aestiva on 2007-09-12
I understand now.

---

