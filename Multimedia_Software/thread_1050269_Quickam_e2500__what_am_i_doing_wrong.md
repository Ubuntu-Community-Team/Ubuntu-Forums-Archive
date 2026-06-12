---
title: "Quickam e2500  what am i doing wrong?"
date: 2009-01-25
forum: Multimedia Software
---

### Post by cash34 on 2009-01-25
i have the quickam e2500 webcam
and after doing a bit of looking around i downloaded gspcav1-20071224

after i run 
Sudo ./gspca_build 

i get this 


make -C /lib/modules/`uname -r`/build SUBDIRS=/home/abbas/gspcav1-20071224 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /home/abbas/gspcav1-20071224/gspca_core.o
/home/abbas/gspcav1-20071224/gspca_core.c:54:27: error: asm/semaphore.h: No such file or directory
/home/abbas/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_ioctl’:
/home/abbas/gspcav1-20071224/gspca_core.c:2463: error: implicit declaration of function ‘video_usercopy’
/home/abbas/gspcav1-20071224/gspca_core.c: At top level:
/home/abbas/gspcav1-20071224/gspca_core.c:2609: error: unknown field ‘owner’ specified in initializer
/home/abbas/gspcav1-20071224/gspca_core.c:2609: warning: initialization from incompatible pointer type
/home/abbas/gspcav1-20071224/gspca_core.c:2611: error: unknown field ‘type’ specified in initializer
/home/abbas/gspcav1-20071224/gspca_core.c: In function ‘spca50x_create_sysfs’:
/home/abbas/gspcav1-20071224/gspca_core.c:2769: error: implicit declaration of function ‘video_device_create_file’
/home/abbas/gspcav1-20071224/gspca_core.c:2780: error: implicit declaration of function ‘video_device_remove_file’
/home/abbas/gspcav1-20071224/gspca_core.c: In function ‘spca5xx_probe’:
/home/abbas/gspcav1-20071224/gspca_core.c:4301: error: incompatible types in assignment
make[2]: *** [/home/abbas/gspcav1-20071224/gspca_core.o] Error 1
make[1]: *** [_module_/home/abbas/gspcav1-20071224] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [default] Error 2

---

### Post by wolfen69 on 2009-01-25
here is an easier way.

```
sudo apt-get install module-assistant
```
then
```
sudo m-a a-i gspca
```
and let it do it's thing.
reboot.

---

### Post by cariboo on 2009-01-25
None of the versions will build with the 2.6.27, If you are running Intrepid, the driver should be automagically installed.

To check if the drivers are loaded, open a terminal and type:

```
lsmod | grep spca
```

The output should look something like this:

```
lsmod | grep spca
gspca_zc3xx            59392  0 
gspca_main             34560  1 gspca_zc3xx
compat_ioctl32         18304  2 saa7134,gspca_main
videodev               45184  4 tuner,saa7134,gspca_main,compat_ioctl32
```

For testing  purposes, install xawtv. it is in the repositories, then open a terminal and type:

```
xawtv -c /dev/video0
```  

You should be able to see yourself.

Jim

---

