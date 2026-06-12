---
title: "AODV make errors"
date: 2010-04-23
forum: Networking &amp; Wireless
---

### Post by zabi1001 on 2010-04-23
hi, i m using ubuntu 9.10 and wants to load AODV,
but i m facing these errors while i make it..


 
zabi@zabi:~/aodv-uu-0.9.5$ sudo make
make -C /home/zabi/aodv-uu-0.9.5/lnx KERNEL_DIR=/lib/modules/2.6.31-21-generic/build KCC=gcc XDEFS=-DDEBUG
make[1]: Entering directory `/home/zabi/aodv-uu-0.9.5/lnx'
make -C /lib/modules/2.6.31-21-generic/build SUBDIRS=/home/zabi/aodv-uu-0.9.5/lnx modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-21-generic'
  CC [M]  /home/zabi/aodv-uu-0.9.5/lnx/kaodv-mod.o
/home/zabi/aodv-uu-0.9.5/lnx/kaodv-mod.c: In function ‘kaodv_hook’:
/home/zabi/aodv-uu-0.9.5/lnx/kaodv-mod.c:273: warning: passing argument 1 of ‘ip_route_me_harder’ from incompatible pointer type
include/linux/netfilter_ipv4.h:77: note: expected ‘struct sk_buff *’ but argument is of type ‘struct sk_buff **’
/home/zabi/aodv-uu-0.9.5/lnx/kaodv-mod.c: At top level:
/home/zabi/aodv-uu-0.9.5/lnx/kaodv-mod.c:321: warning: initialization from incompatible pointer type
/home/zabi/aodv-uu-0.9.5/lnx/kaodv-mod.c:330: warning: initialization from incompatible pointer type
/home/zabi/aodv-uu-0.9.5/lnx/kaodv-mod.c:339: warning: initialization from incompatible pointer type
/home/zabi/aodv-uu-0.9.5/lnx/kaodv-mod.c: In function ‘kaodv_init’:
/home/zabi/aodv-uu-0.9.5/lnx/kaodv-mod.c:391: warning: passing argument 1 of ‘dev_get_by_name’ from incompatible pointer type
include/linux/netdevice.h:1099: note: expected ‘struct net *’ but argument is of type ‘char *’
/home/zabi/aodv-uu-0.9.5/lnx/kaodv-mod.c:391: error: too few arguments to function ‘dev_get_by_name’
/home/zabi/aodv-uu-0.9.5/lnx/kaodv-mod.c:402: error: implicit declaration of function ‘proc_net_create’
/home/zabi/aodv-uu-0.9.5/lnx/kaodv-mod.c: In function ‘kaodv_exit’:
/home/zabi/aodv-uu-0.9.5/lnx/kaodv-mod.c:432: warning: passing argument 1 of ‘proc_net_remove’ from incompatible pointer type
include/linux/proc_fs.h:163: note: expected ‘struct net *’ but argument is of type ‘char *’
/home/zabi/aodv-uu-0.9.5/lnx/kaodv-mod.c:432: error: too few arguments to function ‘proc_net_remove’
make[3]: *** [/home/zabi/aodv-uu-0.9.5/lnx/kaodv-mod.o] Error 1
make[2]: *** [_module_/home/zabi/aodv-uu-0.9.5/lnx] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-21-generic'
make[1]: *** [kaodv.ko] Error 2
make[1]: Leaving directory `/home/zabi/aodv-uu-0.9.5/lnx'
make: *** [kaodv] Error 2


plz help me to remove them...

---

