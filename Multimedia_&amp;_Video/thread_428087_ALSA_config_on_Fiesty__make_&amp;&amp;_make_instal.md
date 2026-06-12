---
title: "ALSA config on Fiesty | make &amp;&amp; make install errors"
date: 2007-04-30
forum: Multimedia &amp; Video
---

### Post by brooksbp on 2007-04-30
Hi... I'm building the source from the latest ALSA rep and I'm getting errors when getting to the ->

sudo ./configure --with-cards=ca0106
sudo make
sudo make install

here's the error I'm getting during the "sudo make" command ->


make[3]: Entering directory `/usr/src/modules/alsa-driver/pcmcia/pdaudiocf'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pcmcia/pdaudiocf'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pcmcia/vx'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pcmcia/vx'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/pcmcia'
make[1]: Leaving directory `/usr/src/modules/alsa-driver'
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/usr/src/modules/alsa-driver  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
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
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [compile] Error 2
brooksbp@brooksbp-desktop:/usr/src/modules/alsa-driver$

---

### Post by brooksbp on 2007-04-30
anybody?

---

### Post by musicinmybrain on 2007-04-30
This is development code you're trying to build, right? I suspect you grabbed it while it was broken.

---

### Post by ubulis on 2007-05-04
I am hving the same problem... hope some one can tell me what&#347; wrong...

---

