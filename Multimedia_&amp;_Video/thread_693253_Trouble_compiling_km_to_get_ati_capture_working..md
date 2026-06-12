---
title: "Trouble compiling km to get ati capture working."
date: 2008-02-10
forum: Multimedia &amp; Video
---

### Post by papafreebird on 2008-02-10
I am having trouble getting km to compile so that I can get my ati aiw capture card working in linux.  I have tried both the regular download and the cvs and get the same error using both.

```

 sudo make -C /usr/src/linux-headers-$(uname -r) SUBDIRS=$PWD modules
make: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/steven/Desktop/km/km_api.o
  CC [M]  /home/steven/Desktop/km/km_api_data.o
  CC [M]  /home/steven/Desktop/km/km_memory.o
In file included from /home/steven/Desktop/km/km_memory.c:24:
include/linux/pci.h: In function ‘pci_register_driver’:
include/linux/pci.h:604: error: ‘KBUILD_MODNAME’ undeclared (first use in this function)
include/linux/pci.h:604: error: (Each undeclared identifier is reported only once
include/linux/pci.h:604: error: for each function it appears in.)
make[1]: *** [/home/steven/Desktop/km/km_memory.o] Error 1
make: *** [_module_/home/steven/Desktop/km] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'

```

Any ideas what I should do.  It drives me nuts to have to boot into windows just to capture a video.  

thanks for any help you can offer.

---

