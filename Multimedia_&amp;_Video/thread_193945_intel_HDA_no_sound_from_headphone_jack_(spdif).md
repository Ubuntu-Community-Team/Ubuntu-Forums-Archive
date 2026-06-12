---
title: "intel HDA no sound from headphone jack (spdif)"
date: 2006-06-10
forum: Multimedia &amp; Video
---

### Post by linuksamiko on 2006-06-10
I have an Asus a6va with an intel hda chipset.
Sound works just fine, as long as you don't want to listen to sound over headphones.

there was a thread over this problem for breazy badger but it seams that it doesn't work with dapper drake (look here: [http://ubuntuforums.org/showthread.php?t=76307&highlight=intel+hda+sound](http://ubuntuforums.org/showthread.php?t=76307&highlight=intel+hda+sound))

first there was a header missing in the sources. After I recompiled the kernel it was there (but the compilation had an error).
After starting "make" it crashed with an error saying this: that one file is missing (hwdep.o)
It should be shipt with the driver but isn't where it is supposed to be. Any idea?

```
make[1]: Entering directory `/usr/src/linux-source-2.6.15'

  WARNING: Symbol version dump /usr/src/linux-source-2.6.15/Module.symvers
           is missing; modules will have no dependencies and modversions.

copying file /home/eanor/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/core/hwdep.c
cp: Aufruf von stat für &#8222;/home/eanor/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/core/hwdep.c&#8220; nicht möglich: No such file or directory
patch: **** Can't find file /home/eanor/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/hwdep.c : No such file or directory
  CC [M]  /home/eanor/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/hwdep.o
gcc: /home/eanor/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/hwdep.c: No such file or directory
gcc: keine Eingabedateien
make[3]: *** [/home/eanor/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore/hwdep.o] Fehler 1
make[2]: *** [/home/eanor/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26/acore] Fehler 2
make[1]: *** [_module_/home/eanor/Desktop/realtek-linux-audiopack-3.5-6/alsa-driver-1.0.9b_26] Fehler 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.15'
make: *** [compile] Fehler 2
```

---

