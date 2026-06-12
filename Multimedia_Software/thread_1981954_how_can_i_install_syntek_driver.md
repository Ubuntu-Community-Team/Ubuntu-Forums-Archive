---
title: "how can i install syntek driver?"
date: 2012-05-17
forum: Multimedia Software
---

### Post by michaelibre on 2012-05-17
i have problem with my integrated webcam of compaq mini 110c and i try to install the syntek drivers but i have this problems: 

yasmich@yasmich:~/Descargas/stk11xx-2.1.0$ make -f Makefile-syntekdriver
Makefile-syntekdriver:1: *** falta un separador.  Alto.

thanks for any help

---

### Post by enigma32 on 2012-05-17
Why are you running "make -f Makefile-syntekdriver" ?

I downloaded the source from here: [http://sourceforge.net/projects/syntekdriver/files/syntekdriver/Release%202.1.0/](http://sourceforge.net/projects/syntekdriver/files/syntekdriver/Release%202.1.0/)

And I run this, as indicated in the README:
```
make -f Makefile.standalone
```

Mine doesn't compile, but I believe that's because I don't have the v4l dev package installed. I am definitely getting a compiler error, not a makefile error (which is what I believe you're receiving)

-Matt

---

### Post by michaelibre on 2012-05-17
thanks for helping, now i have this:

yasmich@yasmich:~/Descargas/stk11xx-2.1.0$ make -f Makefile.standalone
make -C /lib/modules/3.2.0-24-generic-pae/build SUBDIRS=/home/yasmich/Descargas/stk11xx-2.1.0 modules
make[1]: se ingresa al directorio «/usr/src/linux-headers-3.2.0-24-generic-pae»
  CC [M]  /home/yasmich/Descargas/stk11xx-2.1.0/stk11xx-usb.o
/home/yasmich/Descargas/stk11xx-2.1.0/stk11xx-usb.c: En la función ‘usb_stk11xx_probe’:
/home/yasmich/Descargas/stk11xx-2.1.0/stk11xx-usb.c:793:2: error: declaración implícita de la función ‘init_MUTEX’ [-Werror=implicit-function-declaration]
cc1: some warnings being treated as errors
make[2]: *** [/home/yasmich/Descargas/stk11xx-2.1.0/stk11xx-usb.o] Error 1
make[1]: *** [_module_/home/yasmich/Descargas/stk11xx-2.1.0] Error 2
make[1]: se sale del directorio «/usr/src/linux-headers-3.2.0-24-generic-pae»
make: *** [driver] Error 2
yasmich@yasmich:~/Descargas/stk11xx-2.1.0$ sudo make -f Makefile.standalone
make -C /lib/modules/3.2.0-24-generic-pae/build SUBDIRS= modules
make[1]: se ingresa al directorio «/usr/src/linux-headers-3.2.0-24-generic-pae»
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/kconfig/conf.o
  HOSTCC  scripts/kconfig/zconf.tab.o
  HOSTLD  scripts/kconfig/conf
scripts/kconfig/conf --silentoldconfig Kconfig
make[1]: se sale del directorio «/usr/src/linux-headers-3.2.0-24-generic-pae»
make[1]: se ingresa al directorio «/usr/src/linux-headers-3.2.0-24-generic-pae»
  CHK     include/linux/version.h
  CHK     include/generated/utsrelease.h
  UPD     include/generated/utsrelease.h
make[2]: *** No hay ninguna regla para construir el objetivo «kernel/bounds.c», necesario para «kernel/bounds.s».  Alto.
make[1]: *** [prepare0] Error 2
make[1]: se sale del directorio «/usr/src/linux-headers-3.2.0-24-generic-pae»
make: *** [driver] Error 2

---

### Post by enigma32 on 2012-05-17
What ubuntu release are you using? And what kernel version (*uname -r*)

I'm not entirely sure I'm understand those messages correctly, but if Google Translate is doing a good job, I think the solution might lie in one of these two threads:

[http://ubuntuforums.org/showthread.php?t=1047374](http://ubuntuforums.org/showthread.php?t=1047374)
[http://www.linuxquestions.org/questions/blog/frandalla-68463/patching-802-11-linux-sta-driver-for-kernel-2-6-37-3558/](http://www.linuxquestions.org/questions/blog/frandalla-68463/patching-802-11-linux-sta-driver-for-kernel-2-6-37-3558/)

You shouldn't need to run make with sudo, so probably the most immediate problem is the error about init_MUTEX, which that second thread deals with. (I'm assuming you're running a kernel new enough to have that problem.)

---

### Post by michaelibre on 2012-05-18
im using last 12.04
im following this instructions:
[http://www.ubuntu-es.org/node/117666](http://www.ubuntu-es.org/node/117666)
it is in spanish but the command lines are same than english.

i have no idea of what is been told there, could you help me in just giving me the commands to execute in the terminal! 
i cannot edit wl_linux.c because in src i don't have anything!

i have at least some little idea of the terminal using and it is a shame that ubuntu is not accesible if any driver problem like this happen for people they have really litlle litlle understanding of reprogramming.

thank you

---

### Post by michaelibre on 2012-05-18
i have following message

yasmich@yasmich:~$ edit src/wl/sys/wl_linux.c
Error: no write permission for file "src/wl/sys/wl_linux.c"
yasmich@yasmich:~$ sudo edit src/wl/sys/wl_linux.c
[sudo] password for yasmich: 
Error: no write permission for file "src/wl/sys/wl_linux.c"

---

### Post by michaelibre on 2012-05-18
please help!

---

### Post by enigma32 on 2012-05-21
I *think* you don't have the kernel source installed.

Try this:

```
sudo apt-get update
sudo apt-get install linux-source
```
(You'll probably have to confirm that you want to install some packages)

I'm not 100% sure that will work on 12.04, but I think it will.

Then try running make again.

---

