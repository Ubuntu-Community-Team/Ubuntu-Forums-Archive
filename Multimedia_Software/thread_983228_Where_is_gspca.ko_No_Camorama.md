---
title: "Where is gspca.ko? No Camorama"
date: 2008-11-15
forum: Multimedia Software
---

### Post by moomtaz on 2008-11-15
Ok my webcam seems to work in Cheese and I think it may work in kopete but in camorama I get no dice. Oh yeah it definetely doesn't work for youtube capture either. So I have been trying to install the gspca thing which is supposed to be all the rage but that isn't going so easy. Where and how do I get the gspca.ko file and how do I install it. Other methods do not seem to work. This is what it looks like when I do the ./gspca_build thing

[COLOR="Blue"] REMOVE the old module if present
ERROR: Module gspca does not exist in /proc/modules

 CLEAN gspca source tree
rm -r -f *.o decoder/.gspcadecoder.o.cmd decoder/*.o \
        .gspca.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i \
        *.symvers *.err

 COMPILE gspca Please Wait ....!!

 INSTALL gspca in the kernel binary tree
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/media/video/gspca.ko
install -c -m 0644 gspca.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
install: cannot stat `gspca.ko': No such file or directory
make: *** [install] Error 1

 LOAD gspca in memory
FATAL: Module gspca not found.

 PRINT COMPILATION MESSAGES if ERRORS look kgspca.err
make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/src/modules/gspca CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /usr/src/modules/gspca/gspca_core.o
/usr/src/modules/gspca/gspca_core.c:54:27: error: asm/semaphore.h: No such file or directory
/usr/src/modules/gspca/gspca_core.c: In function ‘spca5xx_ioctl’:
/usr/src/modules/gspca/gspca_core.c:2463: error: implicit declaration of function ‘video_usercopy’
/usr/src/modules/gspca/gspca_core.c: At top level:
/usr/src/modules/gspca/gspca_core.c:2604: error: ‘v4l_compat_ioctl32’ undeclared here (not in a function)
/usr/src/modules/gspca/gspca_core.c:2609: error: unknown field ‘owner’ specified in initializer
/usr/src/modules/gspca/gspca_core.c:2609: warning: initialization from incompatible pointer type
/usr/src/modules/gspca/gspca_core.c:2611: error: unknown field ‘type’ specified in initializer
/usr/src/modules/gspca/gspca_core.c: In function ‘spca50x_create_sysfs’:
/usr/src/modules/gspca/gspca_core.c:2769: error: implicit declaration of function ‘video_device_create_file’
/usr/src/modules/gspca/gspca_core.c:2780: error: implicit declaration of function ‘video_device_remove_file’
/usr/src/modules/gspca/gspca_core.c: In function ‘spca5xx_probe’:
/usr/src/modules/gspca/gspca_core.c:4301: error: incompatible types in assignment
make[2]: *** [/usr/src/modules/gspca/gspca_core.o] Error 1
make[1]: *** [_module_/usr/src/modules/gspca] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [default] Error 2[/COLOR]

So of course now what I would like to do is get camorama working. It seems to be an irritating point of my transfer over.

Thanks in advance!

---

### Post by cariboo on 2008-11-15
If your web cam is working in Cheese, then you are using the correct module. Trying to use a different module will not help things. You may want to look at what type of device Camorama is looking for input from. It's the program that is the problem, not the drivers.

Jim

---

### Post by moomtaz on 2008-11-16
I understand that, what I am trying to figure out is why does it work sometimes and not others. It works extremely badly for Youtube. Not at all in Ekiga and so far it works when I am trying to configure kopete, but I tried to chat with it and it didn't work. At least I need it to work in Kopete and Youtube which are probably the only two places that I will use it for.

---

### Post by xc3RnbFO8P on 2008-11-16
> Where is gspca.ko?
Did search:
Places> Search for Files> 
Name of the contains: **gspca.ko** and 
Look in folder: File System

---

### Post by moomtaz on 2008-11-18
Ok here it goes. My webcam only works some of the time and not all of the time. It works in cheese just fine, but it doesn't record. It works when I go into configure mode in Kopete and youtube, but when configure is closed it stops working. It only works some times and not when I want it to. I thought I did a clean install over 8.04 but when my files came up everything was still there just as I had left it. I thought I had formatted on install but I guess not. So I am wondering because my ATI radeon x1250 doesn't work either although the driver is there in the hardware menu. So I don't get all of the frilly 3D effects that Kubuntu can do.

So what I am asking is what is my camera using to make it work some of the time, but not all of the time and how can I change that. How can I make it work in Kopete in chat like I want it to? How can I make it work in YouTube for quick capture. Again it only works when a configure menu is up after you close the configure menu the camera goes off. WTF over.

If you are going to reply with a just do this or google that either please list the steps or include the links (let them be current). You weren't born a linux wizz that came through time and it will for me too. 

Thanks in advance.

---

### Post by moomtaz on 2008-11-24
Well that is not totally true it works when I am in the configure mode of Kopete and YouTube but when it is time to use it then it doesn't work at all. It works in Cheese. I suppose the microphone isn't working either. It doesn't work at all in Ekiga.

In Canorama I get the "Could Not connect to video device (/dev/video0) Please check connection" error.

Now what I think is going on here is this. I think that there are two drivers doing the same thing. I see the uvcvideo thing and also the video4linux thing I don't know what to grep in lsmod otherwise I would post it here or ls-whatever.

In the KDE-Hal-Device Manager (which is really only a viewer because you can't do anything with the Devices) I see two Chicony USB 2.0 Cameras. There is also two USB video interface nodes one with the two Chicony cameras in it and one without anything in it.

Chicony A. Has:
linux.device_file=/dev/input/event9
linux.hotpluge_type=2
linux.subsystem=input
linux.sysfs_path=/sys/devices/pci000.... blah blah blah

Chicony B. Has:
linux.device_file=/dev/video0
linux.hotpluge_type=2
linux.subsystem=video4linux
linux.sysfs_path=/sys/devices/pci000.... blah blah blah
video4linux.device=/dev/video0
video4linux.version=1

Then I tried Gstreamer properties and I noticed that the default camera was on v4l2 and the chicony camera was on v4l1 So I am assuming that there is a nasty configuration mess up somewhere. I assume I have to delete either the v4l2 or v4l1 drivers because there seems to be some kind of mix up. 

Is there anyone who knows all of the terminal stuff that I need to do to work through this problem? I have a Toshiba P205D-7454 AMD Turion 64 with ATI graphics card. 4Gigs of ram I don't know what else is pertinent for this problem. Running Kubuntu 8.10.

Thanks in advance.

---

