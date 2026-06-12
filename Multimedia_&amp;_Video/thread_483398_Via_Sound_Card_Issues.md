---
title: "Via Sound Card Issues"
date: 2007-06-24
forum: Multimedia &amp; Video
---

### Post by codypumper on 2007-06-24
I was having issues with my ac97 via on board sound card. I followed the comprehensive sound guide, and I got this when "making" the alsa-source for my driver.(via82xx):


 (vtmake -C /usr/src/linux-headers-2.6.20-16-generic SUBDIRS=/usr/src/modules/alsa-driver  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /usr/src/modules/alsa-driver/acore/memalloc.o
In file included from /usr/src/modules/alsa-driver/acore/memalloc.c:1:
/usr/src/modules/alsa-driver/acore/memalloc.inc:1:26: error: linux/config.h: No such file or directory
In file included from /usr/src/modules/alsa-driver/acore/memalloc.inc:13,
                 from /usr/src/modules/alsa-driver/acore/memalloc.c:1:
/usr/src/modules/alsa-driver/include/adriver.h:742: error: redefinition of ‘jiffies_to_msecs’
include/linux/jiffies.h:268: error: previous definition of ‘jiffies_to_msecs’ was here
/usr/src/modules/alsa-driver/include/adriver.h:761: error: redefinition of ‘msecs_to_jiffies’
include/linux/jiffies.h:290: error: previous definition of ‘msecs_to_jiffies’ was here
In file included from /usr/src/modules/alsa-driver/acore/memalloc.inc:13,
                 from /usr/src/modules/alsa-driver/acore/memalloc.c:1:
/usr/src/modules/alsa-driver/include/adriver.h: In function ‘snd_pci_orig_save_state’:
/usr/src/modules/alsa-driver/include/adriver.h:1099: error: too many arguments to function ‘pci_save_state’
/usr/src/modules/alsa-driver/include/adriver.h: In function ‘snd_pci_orig_restore_state’:
/usr/src/modules/alsa-driver/include/adriver.h:1103: error: too many arguments to function ‘pci_restore_state’
make[3]: *** [/usr/src/modules/alsa-driver/acore/memalloc.o] Error 1
make[2]: *** [/usr/src/modules/alsa-driver/acore] Error 2
make[1]: *** [_module_/usr/src/modules/alsa-driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [compile] Error 2

---

### Post by atfrase on 2007-06-24
Yeah, I had the same problem when I tried recompiling ALSA.  As far as I can tell, the provided source (both Ubuntu source package and bleeding-edge from alsa-project) simply does not compile on a standard Ubuntu 7.04 system.  I'm not sure why, except maybe some #ifdef or #include is wrong somewhere, and maybe nobody's noticed because people don't usually have to recompile ALSA, and when they do, they're usually having such serious sound issues that nobody in the community wants to touch it with a ten foot pole.

*shrug*

---

### Post by codypumper on 2007-06-24
So, it looks like I won't be getting anywhere soon, eh?

---

### Post by lastnite on 2007-06-25
i'm also using the onboard AC'97 sound card and got exactly same error message with  you, any help?

> **codypumper said:**
> I was having issues with my ac97 via on board sound card. I followed the comprehensive sound guide, and I got this when "making" the alsa-source for my driver.(via82xx):

make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [compile] Error 2

---

