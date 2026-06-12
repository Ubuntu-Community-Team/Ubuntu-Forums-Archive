---
title: "Cannot compile mplayer RC -- fatal error -- register in GENERAL_REGS"
date: 2008-11-05
forum: Multimedia Software
---

### Post by Corin-EU on 2008-11-05
As I have "upgraded" to Intrepid Ibex, one of the first tasks I have tried to do is to compile mplayer 1.0rc2 with the latest security patches, but the following fatal error occurs --

i386/dsputil_mmx.c: In function 'transpose4x4':
i386/dsputil_mmx.c:649: error: can't find a register in class 'GENERAL_REGS' while reloading 'asm'
i386/dsputil_mmx.c:649: error: 'asm' operand has impossible constraints
i386/dsputil_mmx.c: In function 'dsputil_init_mmx':
i386/dsputil_mmx.c:3748: warning: assignment from incompatible pointer type
i386/dsputil_mmx.c:3750: warning: assignment from incompatible pointer type
i386/dsputil_mmx.c:3756: warning: assignment from incompatible pointer type
i386/dsputil_mmx.c:3758: warning: assignment from incompatible pointer type
make[1]: *** [i386/dsputil_mmx.o] Error 1
make[1]: Leaving directory `/usr/src/apps/MPlayer-1.0rc2/libavcodec'
make: *** [libavcodec/libavcodec.a] Error 2

This fatal error was not present with Hardy Heron in which I successfully compiled mplayer and used it as my standard DivX/Xvid video player.

Can anybody offer a solution to the above problem?

I am also seeing lots of these warnings which did not occur with Hardy Heron --

cc1: warning: -funit-at-a-time is required for inlining of functions that are only called once

---

