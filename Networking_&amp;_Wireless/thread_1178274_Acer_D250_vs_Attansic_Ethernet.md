---
title: "Acer D250 vs Attansic Ethernet"
date: 2009-06-04
forum: Networking &amp; Wireless
---

### Post by AexChecker on 2009-06-04
I install on my new Acer D250
[http://www.ubuntu.com/getubuntu/download-netbook](http://www.ubuntu.com/getubuntu/download-netbook)

Read
[http://ubuntuforums.org/showthread.php?t=429845](http://ubuntuforums.org/showthread.php?t=429845)
[http://ubuntuforums.org/showthread.php?t=870123](http://ubuntuforums.org/showthread.php?t=870123)
[http://www.linuxquestions.org/questions/li...acflags-625753/]("http://www.linuxquestions.org/questions/linux-software-2/an-error-about-fix-it-to-use-extracflags-625753/")

Download
[http://ftp.pardus.org.tr/pub/pisi/source/2...2-2.0.5.tar.bz2]("http://ftp.pardus.org.tr/pub/pisi/source/2008/atl2-2.0.5.tar.bz2")


```
natasha@Natasha-Acer-D250:~/atl2/src$ sudo KBUILD_NOPEDANTIC=1 make install
make -C /lib/modules/2.6.28-11-generic/build SUBDIRS=/home/natasha/atl2/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /home/natasha/atl2/src/at_main.o
In file included from /home/natasha/atl2/src/at_hw.h:30,
                 from /home/natasha/atl2/src/at.h:44,
                 from /home/natasha/atl2/src/at_main.c:28:
/home/natasha/atl2/src/at_osdep.h:68:5: warning: "DBG" is not defined
In file included from /home/natasha/atl2/src/at_main.c:28:
/home/natasha/atl2/src/at.h:46:5: warning: "DBG" is not defined
/home/natasha/atl2/src/at_main.c: In function ‘at_probe’:
/home/natasha/atl2/src/at_main.c:326: error: implicit declaration of function ‘SET_MODULE_OWNER’
/home/natasha/atl2/src/at_main.c: In function ‘at_vlan_rx_kill_vid’:
/home/natasha/atl2/src/at_main.c:1488: error: ‘struct vlan_group’ has no member named ‘vlan_devices’
/home/natasha/atl2/src/at_main.c: In function ‘at_restore_vlan’:
/home/natasha/atl2/src/at_main.c:1507: error: ‘struct vlan_group’ has no member named ‘vlan_devices’
/home/natasha/atl2/src/at_main.c: In function ‘at_intr_rx’:
/home/natasha/atl2/src/at_main.c:2163: error: implicit declaration of function ‘eth_copy_and_sum’
make[2]: *** [/home/natasha/atl2/src/at_main.o] Error 1
make[1]: *** [_module_/home/natasha/atl2/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [default] Error 2

```Please, help me to install lan driver.

---

### Post by suomaf on 2009-07-04
Have a look at this thread.
[http://ubuntuforums.org/showthread.php?t=1141529&highlight=acer+d250](http://ubuntuforums.org/showthread.php?t=1141529&highlight=acer+d250)

suo

---

### Post by jpmeijers on 2009-07-12
I had problems getting the Atheros Ethernet working on my Aspire D250 as Atheros' new driver version 1.0.0.9 do not want to compile. I managed to find the old 1.0.0.8 version somewhere on the internet and mirrored it at [http://web.ee.sun.ac.za/~15312704/li...x-v1.0.0.8.tar](http://web.ee.sun.ac.za/~15312704/li...x-v1.0.0.8.tar)

Just download this one, untar and follow the steps in the readme.

---

