---
title: "modinfo: could not find module"
date: 2009-07-30
forum: Networking &amp; Wireless
---

### Post by rippo on 2009-07-30
hi all...
i'm sorry for my english..

i try  to install [snoop module]("https://sourceforge.net/projects/bsnoop/") to improve TCP performance over wireless. but the installation progress did not succesfull as the instruction.

this is the copy of my terminal :

```

**root@rippo-desktop:/usr/local/src/snoop-0.3_rc6# make**
make -C /lib/modules/2.6.24-24-generic/build M=/usr/local/src/snoop-0.3_rc6 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-24-generic'
  CC [M]  /usr/local/src/snoop-0.3_rc6/snoop.o
/usr/local/src/snoop-0.3_rc6/snoop.c:974: warning: initialization from incompatible pointer type
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /usr/local/src/snoop-0.3_rc6/snoop.mod.o
  LD [M]  /usr/local/src/snoop-0.3_rc6/snoop.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-24-generic'

**root@rippo-desktop:/usr/local/src/snoop-0.3_rc6# su -c 'make install'**
install snoop.ko /lib/modules/2.6.24-24-generic/extra 

[B]root@rippo-desktop:/usr/local/src/snoop-0.3_rc6# su -c '/sbin/depmod -a'
[/B] 
** root@rippo-desktop:/usr/local/src/snoop-0.3_rc6# su -c '/sbin/modinfo snoop'**
modinfo: could not find module snoop
```the 'make' and 'make install' is successful, but there is a modinfo message that tell it can not find module snoop so that the module can't be loaded. 
what should i do to fix it..?
thank you..

---

