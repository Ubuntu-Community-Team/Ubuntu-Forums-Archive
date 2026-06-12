---
title: "driver saa7134"
date: 2007-09-01
forum: Multimedia &amp; Video
---

### Post by KJAM on 2007-09-01
well hi and new in linux system and i dont know much aboutm but a ihave a problem with my tv card saa7134 i have the driver but i dont now how install.
try to sudo make and this is the error:

jam@jam-desktop:~/Descargas/saa$ make
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/jam/Descargas/saa modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
CC [M] /home/jam/Descargas/saa/video-buf.o
/home/jam/Descargas/saa/video-buf.c:46: error: expected ')' before string constant
make[2]: *** [/home/jam/Descargas/saa/video-buf.o] Error 1
make[1]: *** [_module_/home/jam/Descargas/saa] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [default] Error 2

i dnt now help pls

---

