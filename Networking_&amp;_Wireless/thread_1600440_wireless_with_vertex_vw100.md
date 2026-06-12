---
title: "wireless with vertex vw100"
date: 2010-10-19
forum: Networking &amp; Wireless
---

### Post by qes on 2010-10-19
Hello,
I am trying to connect to internet with a wireless vertex adapter. I followed the steps of the installation disc, but when I give the command 'make' I get this error:

quate@quate-HP-Compaq-6715s-KE068ET-ABH:~/Bureaublad/Linux$ make
make -C /lib/modules/2.6.35-22-generic/build M=/home/quate/Bureaublad/Linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /home/quate/Bureaublad/Linux/vwmfdiag.o
/home/quate/Bureaublad/Linux/vwmfdiag.c:111: error: unknown field ‘shutdown’ specified in initializer
/home/quate/Bureaublad/Linux/vwmfdiag.c:111: warning: missing braces around initializer
/home/quate/Bureaublad/Linux/vwmfdiag.c:111: warning: (near initialization for ‘vwmfdiag_device.driver_list’)
/home/quate/Bureaublad/Linux/vwmfdiag.c:111: warning: initialization from incompatible pointer type
make[2]: *** [/home/quate/Bureaublad/Linux/vwmfdiag.o] Error 1
make[1]: *** [_module_/home/quate/Bureaublad/Linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [all] Error 2
quate@quate-HP-Compaq-6715s-KE068ET-ABH:~/Bureaublad/Linux$ ls
COPYING        load_vwmfdiag_debug  README.txt    VERSION.txt
load_vwmfdiag  Makefile             usb-serial.h  vwmfdiag.c

The files in 'Linux' were copied from the installation cd. 

Also,  Wireless Networks says:
device not ready (firmware missing)

I have no idea how to solve this.

---

### Post by ibogi on 2011-01-18
Same problem with me, though I am using the Ubuntu 10.04 and the recommended version is 8.10.

Could some expert take a look at this because driver is really small, around 15 kB of source code.

---

### Post by lob_OE on 2011-03-01
Has anybody solve this problem, I have the same. Please...

---

### Post by Fly.Dimos on 2012-02-28
Me too... any solution yet?!

---

