---
title: "can't build v4l-dvb"
date: 2010-06-05
forum: Multimedia Software
---

### Post by someitalian123 on 2010-06-05
problems when i run make install for v4l-dvb

make -C /home/linux/v4l-dvb-7ea0da6a5ac0/v4l install
make[1]: Entering directory `/home/linux/v4l-dvb-7ea0da6a5ac0/v4l'
-e 
Removing obsolete files from /lib/modules/2.6.32-22-generic/kernel/drivers/media/video:

-e 
Removing obsolete files from /lib/modules/2.6.32-22-generic/kernel/drivers/media/dvb/cinergyT2:

-e 
Removing obsolete files from /lib/modules/2.6.32-22-generic/kernel/drivers/media/common:
ir-common.ko rm: remove write-protected regular file `/lib/modules/2.6.32-22-generic/kernel/drivers/media/common/ir-common.ko'? 

-e 
Removing obsolete files from /lib/modules/2.6.32-22-generic/kernel/drivers/media/dvb/frontends:

Installing kernel modules under /lib/modules/2.6.32-22-generic/kernel/drivers/media/:
        video/gspca/m5602/: gspca_m5602.ko install: cannot remove `/lib/modules/2.6.32-22-generic/kernel/drivers/media/video/gspca/m5602/gspca_m5602.ko': Permission denied

strip:/lib/modules/2.6.32-22-generic/kernel/drivers/media/video/gspca/m5602/gspca_m5602.ko: could not create temporary file to hold stripped copy: No error
make[1]: *** [media-install] Error 1
make[1]: Leaving directory `/home/linux/v4l-dvb-7ea0da6a5ac0/v4l'
make: *** [install] Error 2

---

### Post by WinterRain on 2010-06-05
I see a permission denied. Did you do **sudo make install**?

---

### Post by someitalian123 on 2010-06-05
I'm sorry, i can't believe i made such a stupid mistake, thank you.

---

