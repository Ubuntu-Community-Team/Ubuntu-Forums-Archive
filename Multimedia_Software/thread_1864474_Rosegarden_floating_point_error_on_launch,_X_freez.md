---
title: "Rosegarden floating point error on launch, X freeze on file load"
date: 2011-10-19
forum: Multimedia Software
---

### Post by ElectricTriangle on 2011-10-19
Hello, all!

Until recently, I was having some issues with Rosegarden occasionally crashing with a floating point error on start-up, but I didn't really bother with it because I could get through it if I tried to open Rosegarden enough times in succession. I recently put my old install of Ubuntu on a new machine, and in addition to the floating point error on start-up, now when I try to open a file in it, it either causes X to become nearly unresponsive or hang up completely. I use a custom kernel, standard kernel with OSS support and some other things, but testing it with a standard kernel yielded no different results.

Some system info:

Rosegarden version: 10.10 ("Betty Prior")
Ubuntu 10.10 - Natty Narwhal -- 64-bit
Linux kernel version - 2.6.38.4

Any help is greatly appreciated!

---

### Post by ElectricTriangle on 2011-10-28
*bump*

Unticking the 'use Thorn style' option in the preferences seems to have fixed the crash on loading a file, so I can at least use it now. Rosegarden still crashes on launch quite often though, I tried using a standard kernel, but there was no difference.

---

