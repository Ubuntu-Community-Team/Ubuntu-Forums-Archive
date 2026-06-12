---
title: "Problem with v4l-dvb"
date: 2010-06-06
forum: Multimedia Software
---

### Post by dpkg on 2010-06-06
HEY, i am in a middle of tv installation and i got a problem during the installation:

i got this:

when i try put the command: **make** like worte

> make -C /home/benny/v4l-dvb/v4l 
make[1]: Entering directory `/home/benny/v4l-dvb/v4l'
Updating/Creating .config
Preparing to compile for kernel version 2.6.32
File not found: /lib/modules/2.6.32-22-generic/build/.config at ./scripts/make_kconfig.pl line 32, <IN> line 4.
make[1]: *** No rule to make target `.myconfig', needed by `config-compat.h'.  Stop.
make[1]: Leaving directory `/home/benny/v4l-dvb/v4l'
make: *** [all] Error 2


then make install

> make -C /home/benny/v4l-dvb/v4l install
make[1]: Entering directory `/home/benny/v4l-dvb/v4l'
-e 
Removing obsolete files from /lib/modules/2.6.32-22-generic/kernel/drivers/media/video:

-e 
Removing obsolete files from /lib/modules/2.6.32-22-generic/kernel/drivers/media/dvb/cinergyT2:

-e 
Removing obsolete files from /lib/modules/2.6.32-22-generic/kernel/drivers/media/common:
ir-common.ko rm: remove write-protected regular file `/lib/modules/2.6.32-22-generic/kernel/drivers/media/common/ir-common.ko'? y
rm: cannot remove `/lib/modules/2.6.32-22-generic/kernel/drivers/media/common/ir-common.ko': Permission denied

-e 
Removing obsolete files from /lib/modules/2.6.32-22-generic/kernel/drivers/media/dvb/frontends:

Installing kernel modules under /lib/modules/2.6.32-22-generic/kernel/drivers/media/:
/sbin/depmod -a 2.6.32-22-generic 
FATAL: Could not open /lib/modules/2.6.32-22-generic/modules.dep.temp for writing: Permission denied
make[1]: *** [media-install] Error 1
make[1]: Leaving directory `/home/benny/v4l-dvb/v4l'
make: *** [install] Error 2



please i need to install it currectly to continue.

ur help guys?

---

### Post by rizzeh on 2010-06-06
you didnt give permissions to make install
```
sudo make install
```

---

