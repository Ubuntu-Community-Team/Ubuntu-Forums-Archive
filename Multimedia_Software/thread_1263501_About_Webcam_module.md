---
title: "About Webcam module"
date: 2009-09-11
forum: Multimedia Software
---

### Post by shariefbe on 2009-09-11
Hi friends,
   I have some doubts in video device driver. I have an Creative webcam with me. After inserting the webcam i have seen the following modules installed
```

Module              Size       Used by
gspca_zc3xx         55936      0 
gspca_main          29312      1   gspca_zc3xx
videodev            41344      1   gspca_main
v4l1_compat         22404      1   videodev
```
  
I dont know which module is exactly for my webcam? i am seeing 5 extra module installed after inserting my webcam. I am confused. Can anyone help me?

---

### Post by ahbart on 2009-09-11
Why do you want to know what module it is using? Probably more than one I suspect. Is the cam not working?

---

### Post by shariefbe on 2009-09-11
my cam is working fine. Just i want to do some research on it. Thats why....

---

### Post by ahbart on 2009-09-11
Okay. gspca_zc3xx is probably the module for video in you cam.

---

### Post by shariefbe on 2009-09-11
ok finally you mean this is the module for my device....right?

---

### Post by shariefbe on 2009-09-14
Here i am facing a new problem. I tried to compile and install the gspca_main and gspca_zc3xx modules separately. I compiled them successfully. but i am getting error when inserting that modules

```

root@sharief-desktop:/home/sharief/Desktop/video/gspca# insmod gspca_zc3xx.ko 
insmod: error inserting 'gspca_zc3xx.ko': -1 Unknown symbol in module
root@sharief-desktop:/home/sharief/Desktop/video/gspca# insmod gspca_main.ko 
insmod: error inserting 'gspca_main.ko': -1 Unknown symbol in module

```
I think this both modules what some other modules to get insert in to kernel...But i am sure about that modules. Can anyone help me?

---

### Post by shariefbe on 2009-09-15
I cam to know that i need the other two modules to be installed to work this module..ie "videodev" and "v4l1-compat"...so i copiled that modules too...but i am getting the following error..
I compiled all the required modules...ie gspca_main, gspca_zc3xx, v4l1-compat. But i am not getting this "videodev" module..I dont know why...

My Makefile

```

obj-m += gspca_main.o
obj-m += gspca_zc3xx.o
obj-m += v4l1-compat.o
obj-m += v4l2-dev.o
obj-m += v4l2-ioctl.o
obj-m += v4l2-device.o
 
gspca_main-objs := gspca.o
gspca_zc3xx-objs := zc3xx.o
videodev-objs := v4l2-dev.o v4l2-ioctl.o v4l2-device.o

all:
make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean
```

if i compile i am getting the the modules as

```

sharief@sharief-desktop:~/Desktop/video/gspca$ make
make -C /lib/modules/2.6.30/build M=/home/sharief/Desktop/video/gspca modules
make[1]: Entering directory `/home/sharief/Desktop/kernelroot/linux-2.6.30'
CC [M] /home/sharief/Desktop/video/gspca/gspca.o
CC [M] /home/sharief/Desktop/video/gspca/zc3xx.o
LD [M] /home/sharief/Desktop/video/gspca/gspca_main.o
LD [M] /home/sharief/Desktop/video/gspca/gspca_zc3xx.o
CC [M] /home/sharief/Desktop/video/gspca/v4l1-compat.o
CC [M] /home/sharief/Desktop/video/gspca/v4l2-dev.o
CC [M] /home/sharief/Desktop/video/gspca/v4l2-ioctl.o
CC [M] /home/sharief/Desktop/video/gspca/v4l2-device.o
Building modules, stage 2.
MODPOST 6 modules
CC /home/sharief/Desktop/video/gspca/gspca_main.mod.o
LD [M] /home/sharief/Desktop/video/gspca/gspca_main.ko
CC /home/sharief/Desktop/video/gspca/gspca_zc3xx.mod.o
LD [M] /home/sharief/Desktop/video/gspca/gspca_zc3xx.ko
CC /home/sharief/Desktop/video/gspca/v4l1-compat.mod.o
LD [M] /home/sharief/Desktop/video/gspca/v4l1-compat.ko
CC /home/sharief/Desktop/video/gspca/v4l2-dev.mod.o
LD [M] /home/sharief/Desktop/video/gspca/v4l2-dev.ko
CC /home/sharief/Desktop/video/gspca/v4l2-device.mod.o
LD [M] /home/sharief/Desktop/video/gspca/v4l2-device.ko
CC /home/sharief/Desktop/video/gspca/v4l2-ioctl.mod.o
LD [M] /home/sharief/Desktop/video/gspca/v4l2-ioctl.ko

  I dont know why i am getting like this...?Please help me 
```

I am not getting the exact videodev module....please help me

---

### Post by shariefbe on 2009-09-16
Insmod is working fine. But modprobe is not working properly..I know modprobe will install all necessary dependent modules. But in this case all dependent modules are already installed...But i dont know why its happening here..Please help me..see below
```

root@sharief-desktop:/home/sharief/Desktop/video/gspca# modprobe v4l1_compat
root@sharief-desktop:/home/sharief/Desktop/video/gspca# modprobe videodev
root@sharief-desktop:/home/sharief/Desktop/video/gspca# modprobe gspca_main
FATAL: Module gspca_main not found.
root@sharief-desktop:/home/sharief/Desktop/video/gspca# modprobe gspca_zc3xx
FATAL: Module gspca_zc3xx not found.
root@sharief-desktop:/home/sharief/Desktop/video/gspca# insmod gspca_main.ko
root@sharief-desktop:/home/sharief/Desktop/video/gspca# insmod gspca_zc3xx.ko
root@sharief-desktop:/home/sharief/Desktop/video/gspca#
```

 Please help me....what will be the error

---

