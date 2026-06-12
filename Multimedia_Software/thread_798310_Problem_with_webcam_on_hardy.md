---
title: "Problem with webcam on hardy"
date: 2008-05-18
forum: Multimedia Software
---

### Post by chazz-bg on 2008-05-18
i have a problem with installing of this webcam ```
Bus 001 Device 009: ID 0c45:6001 Microdia Genius VideoCAM NB
``` , i installed from synaptic the gspca-source package , then i run 
```
m-a prepare
  m-a a-i gspca
``` like it said in /usr/share/doc/gspca-source/README.Debian
but on m-a a-i gspca i get these errors  ```
# Build the module
/usr/bin/make -C /usr/src/modules/gspca KERNEL_VERSION=2.6.24-17-generic KERNELDIR=/usr/src/linux-headers-2.6.24-17-generic
make[2]: Entering directory `/usr/src/modules/gspca'
/usr/bin/make -C /usr/src/linux-headers-2.6.24-17-generic SUBDIRS=/usr/src/modules/gspca CC=gcc modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.24-17-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/usr/src/modules/gspca/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[3]: *** [_module_/usr/src/modules/gspca] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.24-17-generic'
make[2]: *** [default] Error 2
make[2]: Leaving directory `/usr/src/modules/gspca'
make[1]: *** [binary-modules] Error 2
make[1]: Leaving directory `/usr/src/modules/gspca'
make: *** [kdist_build] Error 2


```
what can cause this errors, and if this not works is there a way to install my webcam because i need it :confused:

ps. really sorry for my poor english

---

### Post by linuxwizard on 2008-05-18
For Microdia webcams you need this driver > [http://www.linux-projects.org/modules/news/](http://www.linux-projects.org/modules/news/)

Your cam is listed as supported > [http://www.linux-projects.org/modules/sections/index.php?op=viewarticle&artid=6](http://www.linux-projects.org/modules/sections/index.php?op=viewarticle&artid=6)

---

### Post by chazz-bg on 2008-05-19
first - there isn't a binary for my kernel (hardy heron's kernel) , and seccond - i have to pay for it , omg . i dont want to pay for software ,that why use linux , if a have enough money for software i will use winbooze :mad:

---

### Post by linuxwizard on 2008-05-19
That is the only driver I know that will work for your webcam > Bus 001 Device 009: ID 0c45:6001 Microdia Genius VideoCAM NB > the only other thing you can do is buy another webcam.

---

### Post by intel on 2008-05-31
Kindly post your problem here
https://groups.google.com/group/microdia

---

