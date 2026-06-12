---
title: "Cisco VPN installation issues"
date: 2011-03-26
forum: Networking &amp; Wireless
---

### Post by tomster2300 on 2011-03-26
Hey guys.  I'm trying to install a Cisco VPN client and keep getting the error below.  I've made sure I have the latest headers for my kernel, but it shows the same error.  Does anyone know what's going on?  


Cisco Systems VPN Client Version 4.8.02 (0030) Linux Installer
Copyright (C) 1998-2006 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]no

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.35-28-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.35-28-generic/CiscoVPN".
* The VPN service will *NOT* be started automatically at boot time.
* Kernel source from "/lib/modules/2.6.35-28-generic/build" will be used to build the module.

Is the above correct [y]

Making module
make -C /lib/modules/2.6.35-28-generic/build SUBDIRS=/home/tmcgahee/Desktop/VPN for work/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic'
make[1]: *** No rule to make target `for'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

---

### Post by conneco on 2011-03-26
Hi 

I knew i needed the cisco VPN client sooner or later so when I seen your post I thought id give it a go, Im running 10.04 and I ran into the same error as you

In my effort to get it to work I apt-get installed the linux headers and source for my kernal(I dont know if this contributed to me finnaly getting it to work) so try without first
 

download these files


[http://www.2shared.com/file/Tjoq23r9/cisco_vpntar.html]("http://www.2shared.com/file/Tjoq23r9/cisco_vpntar.html")



download then
```
tar xvf cisco\ vpn.tar.gz
mv fixes.patch vpnclient
cd vpnclient/
patch < fixes.patch
sudo ./vpn_install
```

that worked for me :)

---

### Post by surfdog on 2011-04-09
That work fine for me to. But I recently installed the recommended upgrades and it broke the cisco vpnclient again. my kernal is now at 2.6.35-28. I tried uninstall and reinstall, but no luck. These vpn issues are driving me up the wall!

---

### Post by iguana007 on 2011-04-18
Hello,
I just received access to the company server which requires this Cisco client and I have same troubles. I tried to follow above liste instruction, but with no sucess:
```

igi@igi:~/Plocha/cisco vpn$ mv fixes.patch vpnclient
igi@igi:~/Plocha/cisco vpn$ cd vpnclient/
igi@igi:~/Plocha/cisco vpn/vpnclient$ patch < fixes.patch
patching file frag.c
patching file interceptor.c
patching file IPSecDrvOS_linux.c
patching file linuxcniapi.c
patching file linuxkernelapi.c
patching file Makefile
igi@igi:~/Plocha/cisco vpn/vpnclient$ sudo ./vpn
vpnclient       vpnclient_init  vpn_install     vpn_uninstall   
igi@igi:~/Plocha/cisco vpn/vpnclient$ sudo ./vpn_install 
Cisco Systems VPN Client Version 4.8.02 (0030) Linux Installer
Copyright (C) 1998-2006 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.35-28-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.35-28-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.35-28-generic/build" will be used to build the module.

Is the above correct [y]

Making module
make -C /lib/modules/2.6.35-28-generic/build SUBDIRS=/home/igi/Plocha/cisco vpn/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic'
make[1]: *** No rule to make target `vpn/vpnclient'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".


```

Anyone has an idea how to fix this please?
Thank you

---

