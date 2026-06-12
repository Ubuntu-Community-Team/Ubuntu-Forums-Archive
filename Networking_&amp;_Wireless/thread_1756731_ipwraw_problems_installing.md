---
title: "ipwraw problems installing"
date: 2011-05-12
forum: Networking &amp; Wireless
---

### Post by Pabx on 2011-05-12
I cannot make and sudo make install:

the output:

pepe@hplap:~/ipwraw-ng$ make

WARNING: $SHELL not set to bash.
If you experience build errors, try
'make SHELL=/bin/bash'.

make -C /lib/modules/2.6.38-8-generic/build M=/home/pepe/ipwraw-ng modules
make[1]: se ingresa al directorio «/usr/src/linux-headers-2.6.38-8-generic»

WARNING: $SHELL not set to bash.
If you experience build errors, try
'make SHELL=/bin/bash'.

  CC [M]  /home/pepe/ipwraw-ng/ipwraw.o
/home/pepe/ipwraw-ng/ipwraw.c:43:27: fatal error: net/ieee80211.h: No existe el fichero o el directorio
compilation terminated.
make[2]: *** [/home/pepe/ipwraw-ng/ipwraw.o] Error 1
make[1]: *** [_module_/home/pepe/ipwraw-ng] Error 2
make[1]: leaves directory  «/usr/src/linux-headers-2.6.38-8-generic»
make: *** [modules] Error 2 


ANY HELP?

---

### Post by Pabx on 2011-05-12
Tried 'make SHELL=/bin/bash'.

And nothing.

---

### Post by Pabx on 2011-05-13
I beg for some help!! pleaseeeeeeeee :confused:

---

### Post by Pabx on 2011-05-13
[http://ubuntuforums.org/showthread.php?t=1756731](http://ubuntuforums.org/showthread.php?t=1756731) so i think no one ever has helped with this. . .

---

