---
title: "ZTE MF180 Modem doesn't work in 64bit Ubuntu 11.10"
date: 2011-12-27
forum: Networking &amp; Wireless
---

### Post by sureshatt on 2011-12-27
Hi, I've been using the zte mf180 modem with ubuntu 10.04 32-bit and it worked fine with the linux drivers ship with the modem itself. But recently i moved to Ubuntu 11.10 64-bit computer and after i installed the same linux drivers on the machine and try to start Join_Air application (the GUI application for the modem), it gives the following error.  

"**./Join_Air: error while loading shared libraries: libusb-0.1.so.4: wrong ELF class: ELFCLASS64**"

I did some search on the above error and i figured out that it causes because either the application (Join_Air) or the drivers doesn't run on 64 bit architecture. 

One more thing to mention is that when i was installing the driver which ships with the mode itself, i got some errors too. given bellow is the screen output of the installation. 

........................................
........................................
ls: cannot access /usr/share/applications/desktop.*.cache: No such file or directory
udevadm is exist!
******Begin to /opt/Join_Air/driver
this is linux driver installtion
make -C /lib/modules/3.0.0-12-generic/build M=/tmp/ONDA_driver_install_V3.3 modules
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-12-generic'
  CC [M]  /tmp/ONDA_driver_install_V3.3/onda.o
**/tmp/ONDA_driver_install_V3.3/onda.c:18599:22: fatal error: usb-wwan.h: No such file or directory**
[B]compilation terminated.
make[2]: *** [/tmp/ONDA_driver_install_V3.3/onda.o] Error 1
make[1]: *** [_module_/tmp/ONDA_driver_install_V3.3] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic'[/B]
**make: *** [modules] Error 2**
this  is customized kernel ,kernel version is: 3.0.0-12-generic
enter customize_driver_install function
[B]cp: cannot stat `onda.ko': No such file or directory
FATAL: Module onda not found.[/B]
disselfirefox.pp driver_install.run nm.pp se End to /opt/Join_Air/driver
install completed!!!

---

