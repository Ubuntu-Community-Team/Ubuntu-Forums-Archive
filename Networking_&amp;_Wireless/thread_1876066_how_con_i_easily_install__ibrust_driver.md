---
title: "how con i easily install  ibrust driver"
date: 2011-11-05
forum: Networking &amp; Wireless
---

### Post by iissaa on 2011-11-05
hi every one   :D

how con i install easily ibrust driver in ubuntu 10.10

i shearch in  google & i find idea but it is very complicated 

any idea to do it easily

tanks :)

---

### Post by iissaa on 2011-11-05
when i try to do the explain here :
[https://help.ubuntu.com/community/Iburst](https://help.ubuntu.com/community/Iburst)

come this error :


```
ayub@ayub~/ibdriver-1.3.2-linux-2.6.24 $ make
make -C /lib/modules/2.6.35-22-generic/build SUBDIRS=/home/ayub/ibdriver-1.3.2-linux-2.6.24 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /home/ayub/ibdriver-1.3.2-linux-2.6.24/ib-net.o
/home/ayub/ibdriver-1.3.2-linux-2.6.24/ib-net.c: In function ‘ib_net_stats’:
/home/ayub/ibdriver-1.3.2-linux-2.6.24/ib-net.c:271: error: ‘struct net_device’ has no member named ‘priv’
/home/ayub/ibdriver-1.3.2-linux-2.6.24/ib-net.c: In function ‘ib_wireless_stats’:
/home/ayub/ibdriver-1.3.2-linux-2.6.24/ib-net.c:282: error: ‘struct net_device’ has no member named ‘priv’
/home/ayub/ibdriver-1.3.2-linux-2.6.24/ib-net.c: In function ‘ib_net_tx_timeout’:
/home/ayub/ibdriver-1.3.2-linux-2.6.24/ib-net.c:294: error: ‘struct net_device’ has no member named ‘priv’
/home/ayub/ibdriver-1.3.2-linux-2.6.24/ib-net.c: In function ‘ib_net_tx_start’:
/home/ayub/ibdriver-1.3.2-linux-2.6.24/ib-net.c:311: error: ‘struct net_device’ has no member named ‘priv’
/home/ayub/ibdriver-1.3.2-linux-2.6.24/ib-net.c: In function ‘ib_net_open’:
/home/ayub/ibdriver-1.3.2-linux-2.6.24/ib-net.c:343: error: ‘struct net_device’ has no member named ‘priv’
/home/ayub/ibdriver-1.3.2-linux-2.6.24/ib-net.c: In function ‘ib_net_close’:
/home/ayub/ibdriver-1.3.2-linux-2.6.24/ib-net.c:363: error: ‘struct net_device’ has no member named ‘priv’
/home/ayub/ibdriver-1.3.2-linux-2.6.24/ib-net.c: In function ‘ib_ioctl_getrate’:
/home/ayub/ibdriver-1.3.2-linux-2.6.24/ib-net.c:430: error: ‘struct net_device’ has no member named ‘priv’
/home/ayub/ibdriver-1.3.2-linux-2.6.24/ib-net.c: In function ‘ib_net_setup’:
/home/ayub/ibdriver-1.3.2-linux-2.6.24/ib-net.c:496: error: ‘struct net_device’ has no member named ‘get_stats’
/home/ayub/ibdriver-1.3.2-linux-2.6.24/ib-net.c:502: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/ayub/ibdriver-1.3.2-linux-2.6.24/ib-net.c:503: error: ‘struct net_device’ has no member named ‘open’
/home/ayub/ibdriver-1.3.2-linux-2.6.24/ib-net.c:504: error: ‘struct net_device’ has no member named ‘stop’
/home/ayub/ibdriver-1.3.2-linux-2.6.24/ib-net.c:506: error: ‘struct net_device’ has no 

member named ‘tx_timeout’
/home/ayub/ibdriver-1.3.2-linux-2.6.24/ib-net.c:508: error: ‘struct net_device’ has no member named ‘change_mtu’
/home/ayub/ibdriver-1.3.2-linux-2.6.24/ib-net.c:509: warning: statement with no effect
/home/ayub/ibdriver-1.3.2-linux-2.6.24/ib-net.c: In function ‘ib_net_register’:
/home/ayub/ibdriver-1.3.2-linux-2.6.24/ib-net.c:526: error: ‘struct net_device’ has no member named ‘priv’
make[2]: *** [/home/ayub/ibdriver-1.3.2-linux-2.6.24/ib-net.o] Error 1
make[1]: *** [_module_/home/ayub/ibdriver-1.3.2-linux-2.6.24] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [default] Error 2
ayub@ayub~/ibdriver-1.3.2-linux-2.6.24 $ sudo make install
cp *.ko /lib/modules/2.6.35-22-generic/kernel/drivers/net/
cp: cannot stat `*.ko': No such file or directory
make: *** [install] Error 1

```

---

### Post by iissaa on 2011-11-06
[QUOTE=iissaa;11428742]when i try to do the explain here :
[https://help.ubuntu.com/community/Iburst](https://help.ubuntu.com/community/Iburst)

come this error :


```
make -C /lib/modules/2.6.35-22-generic/build SUBDIRS=/home/ayub/Desktop/ibdriver-1.3.5-linux-2.6.36 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /home/ayub/Desktop/ibdriver-1.3.5-linux-2.6.36/ib-pcmcia.o
In file included from /home/ayub/Desktop/ibdriver-1.3.5-linux-2.6.36/ib-pcmcia.c:23:
include/pcmcia/cs.h:54: error: expected specifier-qualifier-list before ‘socket_t’
include/pcmcia/cs.h:149: error: expected specifier-qualifier-list before ‘page_t’
In file included from /home/ayub/Desktop/ibdriver-1.3.5-linux-2.6.36/ib-pcmcia.c:25:
include/pcmcia/cistpl.h:557: error: expected specifier-qualifier-list before ‘cisdata_t’
/home/ayub/Desktop/ibdriver-1.3.5-linux-2.6.36/ib-pcmcia.c: In function ‘ib_pcmcia_config’:
/home/ayub/Desktop/ibdriver-1.3.5-linux-2.6.36/ib-pcmcia.c:690: warning: assignment makes integer from pointer without a cast
make[2]: *** [/home/ayub/Desktop/ibdriver-1.3.5-linux-2.6.36/ib-pcmcia.o] Error 1
make[1]: *** [_module_/home/ayub/Desktop/ibdriver-1.3.5-linux-2.6.36] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [default] Error 2

```

---

### Post by lost.soul on 2011-11-20
Try downloading the latest drivers from here:

[http://sourceforge.net/projects/ibdriver/files/latest/download?source=files](http://sourceforge.net/projects/ibdriver/files/latest/download?source=files) 

Unpack them, then do a 
make && sudo make install

---

