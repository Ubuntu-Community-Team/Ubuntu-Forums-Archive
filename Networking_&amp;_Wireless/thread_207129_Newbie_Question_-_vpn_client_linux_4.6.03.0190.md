---
title: "Newbie Question - vpn client linux 4.6.03.0190"
date: 2006-07-01
forum: Networking &amp; Wireless
---

### Post by csk on 2006-07-01
hi all 
i am a newbie so please bear with me. i have just installed dapper 6.06. i have been trying to install ciso vpn 4.6.03.0190 client on my laptop. however everytime i run the ./vpn_install from the terminal window i get : -

"chetan@ubuntu:~/Desktop/vpnclient$ sudo ./vpn_install
Cisco Systems VPN Client Version 4.6.03 (0190) Linux Installer
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms.


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]y

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.

Directory containing linux kernel source code [/lib/modules/2.6.15-25-386/build]/usr/src/linux-headers-2.6.15-25

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.15-25-386/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/usr/src/linux-headers-2.6.15-25" will be used to build the module.

Is the above correct [y]y

Making module
make -C /usr/src/linux-headers-2.6.15-25 SUBDIRS=/home/chetan/Desktop/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-25'

  WARNING: Symbol version dump /usr/src/linux-headers-2.6.15-25/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /home/chetan/Desktop/vpnclient/linuxcniapi.o
/home/chetan/Desktop/vpnclient/linuxcniapi.c: In function ‘CniInjectReceive’:
/home/chetan/Desktop/vpnclient/linuxcniapi.c:292: error: ‘struct sk_buff’ has no member named ‘stamp’
/home/chetan/Desktop/vpnclient/linuxcniapi.c: In function ‘CniInjectSend’:
/home/chetan/Desktop/vpnclient/linuxcniapi.c:432: error: ‘struct sk_buff’ has no member named ‘stamp’
make[2]: *** [/home/chetan/Desktop/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/chetan/Desktop/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-25'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

i know that there are some threads that try to deal with similar problems over here: - 
[http://ubuntuforums.org/showthread.php?t=106663&highlight=struct+sk_buff](http://ubuntuforums.org/showthread.php?t=106663&highlight=struct+sk_buff)
[http://ubuntuforums.org/showthread.php?t=202870&highlight=vpn+client](http://ubuntuforums.org/showthread.php?t=202870&highlight=vpn+client)
[http://ubuntuforums.org/archive/index.php/t-21054.html](http://ubuntuforums.org/archive/index.php/t-21054.html)
[http://www.ces.clemson.edu/linux/interceptor.c](http://www.ces.clemson.edu/linux/interceptor.c)

i have tried to follow there instruction but havent got anywhere. i have downloaded the build-essientials, linux-headers and linux support (386). could someone please explain it to me in laymans terms how to solve this problem 

thanks heaps
csk

---

### Post by jordilin on 2006-07-12
I'm currently looking for the same question and I have found the following tutorial on how to install the cisco vpn client on Dapper [http://popey.com/node/62](http://popey.com/node/62)
but I haven't tried yet.

---

