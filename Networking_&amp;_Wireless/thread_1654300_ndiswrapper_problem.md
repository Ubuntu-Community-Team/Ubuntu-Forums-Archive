---
title: "ndiswrapper problem"
date: 2010-12-28
forum: Networking &amp; Wireless
---

### Post by gjerdej on 2010-12-28
Ok so I have tried absolutely everything. Here's the problem:

In ndisgtk I get an error that says ndiswrapper.ko not found. I searched for this file and found it was in the right directory, but for the previous version of my kernel. I then uninstalled the old kernel and ndiswrapper through synaptic and reinstalled ndiswrapper, but still got the same error.

I then tried to install from source and got back many errors:

> dirty@Dirty:~/ndiswrapper-1.56$ make
make -C driver
make[1]: Entering directory `/home/dirty/ndiswrapper-1.56/driver'
make -C /usr/src/linux-headers-2.6.35-23-generic M=/home/dirty/ndiswrapper-1.56/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-23-generic'
  CC [M]  /home/dirty/ndiswrapper-1.56/driver/wrapndis.o
/home/dirty/ndiswrapper-1.56/driver/wrapndis.c: In function ‘set_multicast_list’:
/home/dirty/ndiswrapper-1.56/driver/wrapndis.c:953: error: ‘struct net_device’ has no member named ‘mc_count’
/home/dirty/ndiswrapper-1.56/driver/wrapndis.c:956: error: ‘struct net_device’ has no member named ‘mc_count’
/home/dirty/ndiswrapper-1.56/driver/wrapndis.c:960: error: ‘struct net_device’ has no member named ‘mc_count’
/home/dirty/ndiswrapper-1.56/driver/wrapndis.c:960: warning: type defaults to ‘int’ in declaration of ‘_min2’
/home/dirty/ndiswrapper-1.56/driver/wrapndis.c:960: error: ‘struct net_device’ has no member named ‘mc_count’
/home/dirty/ndiswrapper-1.56/driver/wrapndis.c:967: error: ‘struct net_device’ has no member named ‘mc_list’
/home/dirty/ndiswrapper-1.56/driver/wrapndis.c:968: error: dereferencing pointer to incomplete type
/home/dirty/ndiswrapper-1.56/driver/wrapndis.c:969: error: dereferencing pointer to incomplete type
/home/dirty/ndiswrapper-1.56/driver/wrapndis.c:971: error: dereferencing pointer to incomplete type
make[3]: *** [/home/dirty/ndiswrapper-1.56/driver/wrapndis.o] Error 1
make[2]: *** [_module_/home/dirty/ndiswrapper-1.56/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-23-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/dirty/ndiswrapper-1.56/driver'
make: *** [all] Error 2Not sure if any of these errors are relevant to the problem at hand since I was able to install ndiswrapper through synaptic, but now I'm hopelessly stuck. :KS

---

### Post by kevdog on 2010-12-28
Ok -- just need some background info -- did you install the linux headers for your kernel version and the build essential package?

---

### Post by gjerdej on 2010-12-28
No I haven't done any of those things.

---

### Post by gjerdej on 2010-12-28
Ok so I went and did those things. I even logged in as root to remove the old headers. For some reason it's still not working. Now when I search for ndiswrapper.ko it is nowhere to be found.

---

### Post by laikolosse on 2010-12-30
Gjerdej, to fix the errors which are coming up, you might try following the instructions in reply 4 in [this thread.]("http://ubuntuforums.org/showthread.php?t=1621859")  It applies a patch to the ndiswrapper code which lets it compile in an up-to-date Ubuntu 10.10.  Once you've done that, it seems to put ndiswrapper.ko in /lib/modules/misc/ as well as in the ndiswrapper-1.56/driver/ directory.

Hope this helps.

---

