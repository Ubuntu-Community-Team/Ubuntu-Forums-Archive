---
title: "dapper ppc realtime patch compile troubles"
date: 2006-05-28
forum: Multimedia &amp; Video
---

### Post by dafyddhughes on 2006-05-28
Hi Folks

I'm sorta new to kernel compiling, and I'm hoping somebody can help me out...

I'm trying to compile the newest kernel 2.6.16.18 with the realtime patch (2.6.16-rt25) following the instructions at [http://ubuntustudio.com/wiki/index.php/Dapper:Vanilla_Kernel_With_Realtime_Preemption](http://ubuntustudio.com/wiki/index.php/Dapper:Vanilla_Kernel_With_Realtime_Preemption)

everything goes well until I'm actually compiling and I meet with:

  CC      arch/powerpc/platforms/powermac/feature.o
arch/powerpc/platforms/powermac/feature.c:65: error: conflicting types for 'feature_lock'
include/asm/pmac_feature.h:381: error: previous declaration of 'feature_lock' was here
make[3]: *** [arch/powerpc/platforms/powermac/feature.o] Error 1
make[2]: *** [arch/powerpc/platforms/powermac] Error 2
make[1]: *** [arch/powerpc/platforms] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.16.18-rt'
make: *** [stamp-build] Error 2

The computer's a 12" G4 Powerbook 867.

Does anybody have any ideas?  Like I said, I'm new to this and I'm pretty lost.

Thanks for any help

cheers
dafydd

---

### Post by dolson on 2006-05-28
I don't think the -rt patches are supposed to go against 2.6.16.x, but instead against 2.6.16.

That is just my thoughts on the matter.

I hope that I can work with some people toward getting a Dapper kernel done, but I haven't got much free time anymore.

---

### Post by dafyddhughes on 2006-05-29
Hey Arnold

Thanks for your reply.  I'll  try with 2.6.16.   WHat fun!

[QUOTE=dolson]I don't think the -rt patches are supposed to go against 2.6.16.x, but instead against 2.6.16.[/QUOTE]

Where do I find such information?  Does this mean that poor Ingo has to redo the patch every time there's a new sub-version of the kernel?

That is just my thoughts on the matter.

[QUOTE=dolson]I hope that I can work with some people toward getting a Dapper kernel done, but I haven't got much free time anymore.[/QUOTE]

Not that I'm much use immediately, but I'm determined to get this thing working and I'd love to help.

cheers
dafydd

---

### Post by dafyddhughes on 2006-05-29
Hey Arnold

Same troubles with 2.6.16:

  CC      arch/powerpc/platforms/powermac/pic.o
arch/powerpc/platforms/powermac/pic.c: In function 'pmacpic_find_viaint':
arch/powerpc/platforms/powermac/pic.c:663: warning: label 'not_found' defined but not used
  CC      arch/powerpc/platforms/powermac/setup.o
  CC      arch/powerpc/platforms/powermac/time.o
arch/powerpc/platforms/powermac/time.c:89: warning: 'to_rtc_time' defined but not used
arch/powerpc/platforms/powermac/time.c:96: warning: 'from_rtc_time' defined but not used
  CC      arch/powerpc/platforms/powermac/feature.o
arch/powerpc/platforms/powermac/feature.c:65: error: conflicting types for 'feature_lock'
include/asm/pmac_feature.h:381: error: previous declaration of 'feature_lock' was here
make[3]: *** [arch/powerpc/platforms/powermac/feature.o] Error 1
make[2]: *** [arch/powerpc/platforms/powermac] Error 2
make[1]: *** [arch/powerpc/platforms] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.16-rt'
make: *** [stamp-build] Error 2

I managed, with some fussing, to get 2.6.15.7 patched and working (that's what I'm using now).  Maybe I'll try and get that runnning smoothly.

cheers
dafydd

---

