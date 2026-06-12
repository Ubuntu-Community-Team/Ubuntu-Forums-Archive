---
title: "Random crashing - Nvidia drivers issues with Hardy - Solution!"
date: 2008-05-05
forum: Mythbuntu
---

### Post by db260179 on 2008-05-05
Hi people,

If you are experiencing random crashing, instability and own a Nvidia Graphics card. Using a x2 core processor can be affected and ATI cards suffer from a suspend/resume issues.

Then you will need to compile your own kernel, as the current hardy kernel has settings that causes these problems.

Let me explain my findings (please note: it doesnt affect everyone, but of the two pc's i own, 1x has the problem)

1. The Kernel has a schedule set to SLUB not SLAB (SLAB is more compatible and reliable with NVidia and ATI drivers)

2. If using your custom kernel - the ubuntu-restricted modules doesnt compile properly - nvidia names the modules wrong, thus unable to get driver to load.

I have a custom kernel using hardy kernel source that i made, for i386 and amd64. Message me if you wish to prove my statement or have a pc having problems.

---

### Post by laga on 2008-05-05
Thanks! Did you report your findings as a bug in launchpad?

---

### Post by db260179 on 2008-05-06
Oops, will do! - also as a last note: cool and quiet causes problems as well!

Creates NVRM: errors, hard locks

> **laga said:**
> Thanks! Did you report your findings as a bug in launchpad?

---

### Post by vaxius on 2008-05-09
> **db260179 said:**
> Hi people,

Then you will need to compile your own kernel, as the current hardy kernel has settings that causes these problems.

Let me explain my findings (please note: it doesnt affect everyone, but of the two pc's i own, 1x has the problem)

1. The Kernel has a schedule set to SLUB not SLAB (SLAB is more compatible and reliable with NVidia and ATI drivers)


This was an issue a while ago, but nVidia has since fixed the problem; nVidia's driver now lives happily with SLUB.  However, after installing the driver like normal, [there's a few more things to do to get suspend working.]("http://blog.vaxius.net/?p=43")  (That's a link).

---

### Post by db260179 on 2008-05-09
Thanks for that tip!

SLAB stills works better for me.

Also i missed out another issue with the nvidia driver - turning on the cool and quiet feature in the bios causes problems. On my Asrock HDready 7G board.

> **vaxius said:**
> This was an issue a while ago, but nVidia has since fixed the problem; nVidia's driver now lives happily with SLUB.  However, after installing the driver like normal, [there's a few more things to do to get suspend working.]("http://blog.vaxius.net/?p=43")  (That's a link).

---

### Post by db260179 on 2008-05-10
Further testing - i've turned the cool&quiet back on, and turned off the powernowed service. No lockups so far. obviously this issue is still here with the powernowed service.

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/109643](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/109643)

Still in 2.6.24

---

