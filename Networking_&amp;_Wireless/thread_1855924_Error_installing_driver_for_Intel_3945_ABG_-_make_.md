---
title: "Error installing driver for Intel 3945 ABG - make SHELL=/bin/bash"
date: 2011-10-07
forum: Networking &amp; Wireless
---

### Post by Torre92 on 2011-10-07
Hi all,
it's the firt time i write in this site well please try to understand my basic english...

I'm trying to install wireless driver for my notebook to make possible to Inject packet (I'm trying to do a fragmentation attack).
```
wget http://dl.aircrack-ng.org/drivers/ipwraw-ng-2.3.4-04022008.tar.bz2
tar -xjf ipwraw-ng*
cd ipwraw-ng
```

Here there aren't any problem.
But when i do the
```
Make
```

I got some errors:
```
WARNING: $SHELL not set to bash.
If you experience build errors, try
'make SHELL=/bin/bash'.

make -C /lib/modules/2.6.38-11-generic/build M=/home/giacomo/ipwraw-ng modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-11-generic'

WARNING: $SHELL not set to bash.
If you experience build errors, try
'make SHELL=/bin/bash'.

  CC [M]  /home/giacomo/ipwraw-ng/ipwraw.o
/home/giacomo/ipwraw-ng/ipwraw.c:43:27: fatal error: net/ieee80211.h: No such file or directory
compilation terminated.
make[2]: *** [/home/giacomo/ipwraw-ng/ipwraw.o] Error 1
make[1]: *** [_module_/home/giacomo/ipwraw-ng] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-11-generic'
make: *** [modules] Error 2

```

WTF 'make SHELL=/bin/bash' is?
I tried to type this command and the result was that:
```
giacomo@giacomo-HP-Pavilion-dv5000-RG937EA-ABZ:~/ipwraw-ng$ sudo make SHELL=/bin/bash
make -C /lib/modules/2.6.38-11-generic/build M=/home/giacomo/ipwraw-ng modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-11-generic'
  CC [M]  /home/giacomo/ipwraw-ng/ipwraw.o
/home/giacomo/ipwraw-ng/ipwraw.c:43:27: fatal error: net/ieee80211.h: No such file or directory
compilation terminated.
make[2]: *** [/home/giacomo/ipwraw-ng/ipwraw.o] Error 1
make[1]: *** [_module_/home/giacomo/ipwraw-ng] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-11-generic'
make: *** [modules] Error 2

```

Obv Make Install doesn't work.
What should I do? 
ahah, please help me, i'm going crazy.

(How is my english? ahah) Thanks...

---

### Post by swooshgt on 2011-11-09
please help, I have the exact same problem and can't figure out the problem after searching for the problem I only find this kind of unsolved threads.

---

