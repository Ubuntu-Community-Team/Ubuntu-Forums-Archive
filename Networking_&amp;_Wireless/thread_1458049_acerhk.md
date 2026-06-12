---
title: "acerhk"
date: 2010-04-19
forum: Networking &amp; Wireless
---

### Post by KaiJordanDay on 2010-04-19
Ok, so I need to install acerhk against my new kenral headers.

But I keep getting the following error:

> kai@kai-laptop:~/acerhk-0.5.35$ make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/kai/acerhk-0.5.35 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
make[1]: Makefile: No such file or directory
make[1]: *** No rule to make target `Makefile'. Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make: *** [acerhk.ko] Error 2
kai@kai-laptop:~/acerhk-0.5.35$ 


Any idea? Without it no wireless, no internet access...

---

### Post by KaiJordanDay on 2010-04-19
bump

---

### Post by KaiJordanDay on 2010-04-19
and again... I have no laptop wireless until this is sorted.

---

