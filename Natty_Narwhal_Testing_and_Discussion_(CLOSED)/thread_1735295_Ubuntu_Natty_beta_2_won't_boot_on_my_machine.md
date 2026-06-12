---
title: "Ubuntu Natty beta 2 won't boot on my machine"
date: 2011-04-21
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by matthewbpt on 2011-04-21
Hey everyone,

I have been trying to boot the beta 2 live cd (64 bit version) but I always get a kernel panic before boot completes. I have also tried the daily build, and the kubuntu images with the same result. The 386 image works fine. Anyone else have this problem? It's quite worrying because we are so near release!

PS. This is the first time I'm testing Ubuntu 11.04

---

### Post by dino99 on 2011-04-21
[http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now](http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now)

---

### Post by matthewbpt on 2011-04-21
This is not a thread about the merits or disadvantages of 64bit vs 32bit ... I am already aware of them and I would still like to have 64bit Ubuntu on my machine.

---

### Post by matthewbpt on 2011-04-21
I've tracked down the bug, the kernel panic call trace had messages about my wireless card, I did an alternate cd install which failed to boot with the same error, so I booted a live rescue cd and added the kernel module for that wireless card to the blacklist file, then it worked fine. The module is question is vt6656_stage, so this module is causing problems on 64bit Ubuntu Natty ...

EDIT: Posted a bug report [https://bugs.launchpad.net/ubuntu/+source/linux-ports-meta/+bug/768524](https://bugs.launchpad.net/ubuntu/+source/linux-ports-meta/+bug/768524)

---

