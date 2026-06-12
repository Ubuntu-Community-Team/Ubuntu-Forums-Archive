---
title: "Matrox G450 / Anyone got mga-vid working in intrepid ?"
date: 2009-01-01
forum: Multimedia Software
---

### Post by ansicplusplus on 2009-01-01
Hy,
I just tried to get mga-vid working in order to use my Matrox G450 with mplayer. It had worked in gutsy although I got tired of recompiling with each kernel change.

Anyhow I once again followed the instructions in this thread "[Matrox users - do you have /dev/mga_vid? ]("http://ubuntuforums.org/showthread.php?t=632105&highlight=mga-vid")". Version 2.6.24-2 (from the repository) results in a compile error. The latest version 2.6.24-3 from mirrors.kernel.org compiles but after modprobing the module it produces a Segmentation fault. Strangely the syslog locks fine, lsmod reports a loaded module, but there is no /dev/mga_vid.

As google didn't find anything about this I still have hope that everyone else got their G450 working. ;-)

Can anyone tell me the trick, please ?

Yours, ansicplusplus
BTW: Happy new year!

---

