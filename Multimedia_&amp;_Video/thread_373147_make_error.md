---
title: "make error?"
date: 2007-03-01
forum: Multimedia &amp; Video
---

### Post by sohaibma on 2007-03-01
I am trying to install openchrome drivers for my video card on edgy, following this guide:
**[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)**
(please take a look at it.)

anyway, when i came to this step
**make LINUXDIR=/lib/modules/`uname -r`/build DRM_MODULES=via **

terminal gave me this error:

**make LINUXDIR=/lib/modules/`uname -r`/build DRM_MODULES=via **
make -C /lib/modules/2.6.17-11-386/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[1]: Entering directory `/lib/modules/2.6.17-11-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.17-11-386/build'
make: *** [modules] Error 2


what is this error and how can i fix it?

---

