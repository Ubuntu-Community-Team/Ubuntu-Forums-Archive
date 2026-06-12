---
title: "cisco vpn error can anyone assist"
date: 2009-12-17
forum: Networking &amp; Wireless
---

### Post by crazysexycool on 2009-12-17
Hi i am really sorry for posting this as i am sure this has been asked before but all the solutions on the net are not working for me i am trying to install the cisco VPN client in 9.10 and i get the following error 

f3091236@f3091236-laptop:~$ cd Desktop/
f3091236@f3091236-laptop:~/Desktop$ cd vpnclient2
bash: cd: vpnclient2: No such file or directory
f3091236@f3091236-laptop:~/Desktop$ cd vpnclient 2
f3091236@f3091236-laptop:~/Desktop/vpnclient$ sudo ./vpn_install
Cisco Systems VPN Client Version 4.8.01 (0640) Linux Installer
Copyright (C) 1998-2006 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]n

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.31-16-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.31-16-generic/CiscoVPN".
* The VPN service will *NOT* be started automatically at boot time.
* Kernel source from "/lib/modules/2.6.31-16-generic/build" will be used to build the module.

Is the above correct [y]y

Making module
make -C /lib/modules/2.6.31-16-generic/build SUBDIRS=/home/f3091236/Desktop/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-16-generic'
  CC [M]  /home/f3091236/Desktop/vpnclient/linuxcniapi.o
In file included from /home/f3091236/Desktop/vpnclient/Cniapi.h:15,
                 from /home/f3091236/Desktop/vpnclient/linuxcniapi.c:31:
/home/f3091236/Desktop/vpnclient/GenDefs.h:113: error: conflicting types for ‘uintptr_t’
include/linux/types.h:41: note: previous declaration of ‘uintptr_t’ was here
make[2]: *** [/home/f3091236/Desktop/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/f3091236/Desktop/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
f3091236@f3091236-laptop:~/Desktop/vpnclient$ 

___________

can anyone help thanks

---

