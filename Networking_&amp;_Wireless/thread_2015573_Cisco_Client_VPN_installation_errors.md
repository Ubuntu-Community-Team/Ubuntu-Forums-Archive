---
title: "Cisco Client VPN installation errors"
date: 2012-07-03
forum: Networking &amp; Wireless
---

### Post by BurlEarl on 2012-07-03
Hi,

I am using Ubuntu 12.04 and trying to install the cisco VPN client.  I keep getting errors like this:

Making module
In file included from /lib/modules/3.2.0-23-generic/build/include/linux/kernel.h:13:0,
                 from /lib/modules/3.2.0-23-generic/build/include/linux/skbuff.h:17,
                 from /lib/modules/3.2.0-23-generic/build/include/linux/if_ether.h:133,
                 from /lib/modules/3.2.0-23-generic/build/include/linux/netdevice.h:29,
                 from linuxcniapi.c:18:
/lib/modules/3.2.0-23-generic/build/include/linux/linkage.h:5:25: fatal error: asm/linkage.h: No such file or directory
compilation terminated.

All of the appropriate *.h files seem to be in the adjacent directory, /build/include.

The only instructions Cisco has given me is this: 
   To install the VPN Client, you must have the kernel source that was used to build the kernel that is running on the system. If the system is using a kernel that came as part of the Linux distribution, or a custom built kernel, the kernel code can be obtained in different ways:
• For users running kernels that came with their distribution—You must install the corresponding kernel-source rpm. The vpn_install script should be able to automatically find the kernel source.  

I have found some stuff on Google and this forum, but they seem like nasty workarounds...and I am very much a noobie):P

Any help would be greatly appreciated.

Earl

---

### Post by Sergius14 on 2012-07-03
You can use VPNC for Cisco VPNs with native network applet suppor....

---

### Post by BurlEarl on 2012-07-03
Oh, that was easy.

Thank you.

---

