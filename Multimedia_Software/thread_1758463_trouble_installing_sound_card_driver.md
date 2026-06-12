---
title: "trouble installing sound card driver"
date: 2011-05-14
forum: Multimedia Software
---

### Post by tetsu7 on 2011-05-14
i have an asrock 890fx deluxe 3 mobo up until now ive been using on board audio im running ubuntu 10.10 and i just bought a creative x-fi titanium fatal1ty pro pcie sound card. i went to creative website [http://support.creative.com/downloads/download.aspx?nDownloadId=10792](http://support.creative.com/downloads/download.aspx?nDownloadId=10792) and downloaded the linux driver. i tried to install the driver as stated below from the readme file. 
Quick install

=============
In terminal,

1) Goto source directory
2) Execute make command as root
   make
   make install

however i have failed. below is what i got when attempting to install. anyone know what i need to do to get this installed? thanks for your advice in advance!


vaginasaretasty@vaginasaretasty-desktop:~/Desktop/XFiDrv_Linux_Public_US_1.00$ sudo make
[sudo] password for vaginasaretasty: 
make -C /lib/modules/2.6.35-28-generic/build M=/home/vaginasaretasty/Desktop/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic'
  CC [M]  /home/vaginasaretasty/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.o
/home/vaginasaretasty/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:14: fatal error: sound/driver.h: No such file or directory
compilation terminated.
make[2]: *** [/home/vaginasaretasty/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.o] Error 1
make[1]: *** [_module_/home/vaginasaretasty/Desktop/XFiDrv_Linux_Public_US_1.00] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
make: *** [all] Error 2
vaginasaretasty@vaginasaretasty-desktop:~/Desktop/XFiDrv_Linux_Public_US_1.00$ sudo make install
Copy module files...
cp: cannot stat `ctxfi.ko': No such file or directory
make: *** [install] Error 1

---

