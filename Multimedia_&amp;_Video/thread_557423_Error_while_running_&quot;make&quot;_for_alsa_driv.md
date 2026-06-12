---
title: "Error while running &quot;make&quot; for alsa drivers"
date: 2007-09-22
forum: Multimedia &amp; Video
---

### Post by AxAeo on 2007-09-22
I'm following the instructions on the ALSA wiki for setting up drivers, and ./configure worked fine,  except when I tried to run make, I got this:

```
/lib/modules/2.6.20-16-generic/build/include/asm/hardirq.h:12: error: requested alignment is not a constant
make[1]: *** [hpetimer.o] Error 1
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.9rc4a/acore'
make: *** [compile] Error 1
```

After a bit of googling, I thought it might be CONFIG_MODVERSIONS, so i tried to install the module with it disabled, and I got the same result. Any suggestions?

---

### Post by Crenfinkle on 2007-09-22
Is this a stable release, or a release candidate that you are trying to install? I have compiled and installed the various alsa modules several times lately, all with absolutely no problems. 

Looking at the ouput above, this is a release candidate (rc4) of a very old release of alsa-driver (1.0.9). Try the newest stable release-- 1.0.14 --for updated functionality. It should install properly.

---

### Post by AxAeo on 2007-09-22
Ah, I wasn't sure if I had the latest one... Thanks a lot! :D

---

