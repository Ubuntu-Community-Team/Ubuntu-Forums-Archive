---
title: "Cisco VPN install problem"
date: 2010-06-03
forum: Networking &amp; Wireless
---

### Post by terppe on 2010-06-03
[FONT=monospace]
Hi

I was about to install and try VPN but I got jammed to this error--
can anyone say how to proceed with this ?

I got linux headers installed and gcc.
Using latest ubuntu and Kernel version is 2.6.32-22.

Tried to follow this guide on installation:
[http://www.longren.org/2007/05/17/how-to-cisco-vpn-client-on-ubuntu-704-feisty-fawn/](http://www.longren.org/2007/05/17/how-to-cisco-vpn-client-on-ubuntu-704-feisty-fawn/)

After hitting enter on sudo ./vpn_install ---->

[LIST=1]
[*]Directory containing linux kernel source code  [/lib/modules/2.6.32-22-generic/build]
[*]* Binaries will be installed in  "/usr/local/bin".
[*]* Modules will be installed in  "/lib/modules/2.6.32-22-generic/CiscoVPN".
[*]* The VPN service will be started  AUTOMATICALLY at boot time.
[*]* Kernel source from  "/lib/modules/2.6.32-22-generic/build" will be used to build the module.
[*]Is the above correct [y]
[*]Making module
[*]make -C  /lib/modules/2.6.32-22-generic/build SUBDIRS=/home/fintel/vpnclient  modules
[*]make[1]: Entering directory  `/usr/src/linux-headers-2.6.32-22-generic'
[*]  CC [M]   /home/fintel/vpnclient/linuxcniapi.o
[*]/home/fintel/vpnclient/linuxcniapi.c:12:26:  error: linux/config.h: No such file or directory
[*]In file included from  /home/fintel/vpnclient/Cniapi.h:15,
[*]                 from  /home/fintel/vpnclient/linuxcniapi.c:27:
[*]/home/fintel/vpnclient/GenDefs.h:113:  error: conflicting types for ‘uintptr_t’
[*]include/linux/types.h:41: note:  previous declaration of ‘uintptr_t’ was here
[*]/home/fintel/vpnclient/linuxcniapi.c:  In function ‘CniInjectReceive’:
[*]/home/fintel/vpnclient/linuxcniapi.c:297:  error: implicit declaration of function ‘skb_set_timestamp’
[*]/home/fintel/vpnclient/linuxcniapi.c:331:  error: ‘struct sk_buff’ has no member named ‘nh’
[*]/home/fintel/vpnclient/linuxcniapi.c:332:  error: ‘struct sk_buff’ has no member named ‘mac’
[*]/home/fintel/vpnclient/linuxcniapi.c:  In function ‘CniInjectSend’:
[*]/home/fintel/vpnclient/linuxcniapi.c:454:  error: ‘struct sk_buff’ has no member named ‘mac’
[*]/home/fintel/vpnclient/linuxcniapi.c:455:  error: ‘struct sk_buff’ has no member named ‘nh’
[*]/home/fintel/vpnclient/linuxcniapi.c:458:  error: ‘struct sk_buff’ has no member named ‘h’
[*]/home/fintel/vpnclient/linuxcniapi.c:458:  error: ‘struct sk_buff’ has no member named ‘nh’
[*]make[2]: ***  [/home/fintel/vpnclient/linuxcniapi.o] Error 1
[*]make[1]: ***  [_module_/home/fintel/vpnclient] Error 2
[*]make[1]: Leaving directory  `/usr/src/linux-headers-2.6.32-22-generic'
[*]make: *** [default] Error 2
[*]Failed to make module "cisco_ipsec.ko".
[/LIST]
[/FONT]

---

### Post by terppe on 2010-06-03
Ok. I fetched the later version of this package but it throws still the same error.
Darn, can anyone tell how to fix this. Has anyone else been having this problem?


...
* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.32-22-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.32-22-generic/build" will be used to build the module.

Is the above correct [y]

Making module
make -C /lib/modules/2.6.32-22-generic/build SUBDIRS=/home/fintel/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  CC [M]  /home/fintel/vpnclient/linuxcniapi.o
  CC [M]  /home/fintel/vpnclient/frag.o
  CC [M]  /home/fintel/vpnclient/IPSecDrvOS_linux.o
  CC [M]  /home/fintel/vpnclient/interceptor.o
/home/fintel/vpnclient/interceptor.c: In function ‘interceptor_init’:
/home/fintel/vpnclient/interceptor.c:132: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/fintel/vpnclient/interceptor.c:133: error: ‘struct net_device’ has no member named ‘get_stats’
/home/fintel/vpnclient/interceptor.c:134: error: ‘struct net_device’ has no member named ‘do_ioctl’
/home/fintel/vpnclient/interceptor.c: In function ‘add_netdev’:
/home/fintel/vpnclient/interceptor.c:271: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/fintel/vpnclient/interceptor.c:272: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/fintel/vpnclient/interceptor.c: In function ‘remove_netdev’:
/home/fintel/vpnclient/interceptor.c:294: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
make[2]: *** [/home/fintel/vpnclient/interceptor.o] Error 1
make[1]: *** [_module_/home/fintel/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
...

---

