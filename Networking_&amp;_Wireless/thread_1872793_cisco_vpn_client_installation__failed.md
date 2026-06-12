---
title: "cisco vpn client installation  failed"
date: 2011-10-31
forum: Networking &amp; Wireless
---

### Post by abdulameer84 on 2011-10-31
Hi ,

I am trying to install cisco vpn client on my system. I get below error:

+++++++++++++++++++++++++++
Making module
make -C /lib/modules/2.6.38-8-generic/build SUBDIRS=/home/ameer/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CC [M]  /home/ameer/vpnclient/linuxcniapi.o
/home/ameer/vpnclient/linuxcniapi.c:14:28: fatal error: linux/autoconf.h: No such file or directory
compilation terminated.
make[2]: *** [/home/ameer/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/ameer/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
ameer@ameer-ubuntu:~/vpnclient$ 
ameer@ameer-ubuntu:~/vpnclient$ 

+++++++++++++++++++++++++++

I am very new to ubunto. I have applied linux-headers-2.6.38-8-generic, autoconf, automake, and libtool using package manager. 

VPN client is downloaded is "vpnclient-linux-x86_64-4.8.02.0030-k9.tar.gz"

Any help is really appreciated.

Thanks
Ameer

---

