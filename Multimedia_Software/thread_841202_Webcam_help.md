---
title: "Webcam help"
date: 2008-06-26
forum: Multimedia Software
---

### Post by KeeneMaverick on 2008-06-26
I have an Orange Micro Ibot2 USB webcam. I've been trying to get it to work for a while now but I've run up on some dead ends.

I was going through this howto:
[http://www.linux.com/base/ldp/howto/Webcam-HOWTO/hardware.html](http://www.linux.com/base/ldp/howto/Webcam-HOWTO/hardware.html)

And found this to say about my webcam:
[http://www.qbik.ch/usb/devices/showdev.php?id=1417](http://www.qbik.ch/usb/devices/showdev.php?id=1417)
> This uses a Cypress FX2 chip with OmniVision-designed firmware, and an OV7620 image sensor. ov511-2.17 will support this camera. Email me for the current beta driver.

So, I went to check out the ov511 project site:
[http://alpha.dyndns.org/ov511/](http://alpha.dyndns.org/ov511/)

And went through the installation instructions:
[http://alpha.dyndns.org/ov511/install.html](http://alpha.dyndns.org/ov511/install.html)

I started by doing a "modprobe ov511" and didn't get any errors, so it seems I already have the driver.

But when I got to the section on loading and using the driver, I got no errors, but the instructions say that "dmesg" is supposed to tell me the bridge and chipset of my camera, but all I get is:
```
[ 1920.156363] Linux video capture interface: v2.00
[ 1920.184320] usbcore: registered new interface driver ov511
[ 1920.184327] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/bui
ld-generic/media/ov511/ov511.c: v1.64 for Linux 2.5 : ov511 USB Camera Driver
[ 4998.975182] USB Universal Host Controller Interface driver v3.0

```

I can also see the other USB devices I have plugged in are being detected in dmesg (keyboard, mouse, and joystick) but nothing about my camera.

I created /dev/video0 with "mknod /dev/video0 c 81 0" anyway. Then I did "chmod 666 /dev/video0"

Still no video, though.

I thought maybe it was the driver version, since the one built in is 1.65, and the qbik.ch page says v.2.17 will work. So, I downloaded the kernel sources, and the latest version of ov511 from [http://alpha.dyndns.org/ov511/download.html](http://alpha.dyndns.org/ov511/download.html)

but when I did "make" I got:

```
root@wallaby:/home/keene/Downloads/ov511-2.32# make
    Building OVCam drivers for 2.6 kernel.
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/keene/Downloads/ov511-2.32 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/keene/Downloads/ov511-2.32/ov511_core.o
/home/keene/Downloads/ov511-2.32/ov511_core.c:29:26: error: linux/config.h: No such file or directory
/home/keene/Downloads/ov511-2.32/ov511_core.c:1701: error: unknown field ‘algo_control’ specified in initializer
/home/keene/Downloads/ov511-2.32/ov511_core.c:1701: warning: initialization from incompatible pointer type
/home/keene/Downloads/ov511-2.32/ov511_core.c:1711: error: unknown field ‘algo_control’ specified in initializer
/home/keene/Downloads/ov511-2.32/ov511_core.c:1711: warning: initialization from incompatible pointer type
/home/keene/Downloads/ov511-2.32/ov511_core.c: In function ‘ov51x_init_isoc’:
/home/keene/Downloads/ov511-2.32/ov511_core.c:3566: warning: assignment from incompatible pointer type
/home/keene/Downloads/ov511-2.32/ov511_core.c: In function ‘ov51x_open’:
/home/keene/Downloads/ov511-2.32/ov511_core.c:3818: error: implicit declaration of function ‘video_devdata’
/home/keene/Downloads/ov511-2.32/ov511_core.c:3818: warning: initialization makes pointer from integer without a cast
/home/keene/Downloads/ov511-2.32/ov511_core.c:3819: error: implicit declaration of function ‘video_get_drvdata’
/home/keene/Downloads/ov511-2.32/ov511_core.c:3819: warning: initialization makes pointer from integer without a cast
/home/keene/Downloads/ov511-2.32/ov511_core.c: In function ‘ov51x_release’:
/home/keene/Downloads/ov511-2.32/ov511_core.c:3885: warning: initialization makes pointer from integer without a cast
/home/keene/Downloads/ov511-2.32/ov511_core.c: In function ‘ov51x_do_ioctl’:
/home/keene/Downloads/ov511-2.32/ov511_core.c:3924: warning: initialization makes pointer from integer without a cast
/home/keene/Downloads/ov511-2.32/ov511_core.c:3944: error: implicit declaration of function ‘v4l_print_ioctl’
/home/keene/Downloads/ov511-2.32/ov511_core.c:4303: error: dereferencing pointer to incomplete type
/home/keene/Downloads/ov511-2.32/ov511_core.c: In function ‘ov51x_ioctl’:
/home/keene/Downloads/ov511-2.32/ov511_core.c:4743: warning: initialization makes pointer from integer without a cast
/home/keene/Downloads/ov511-2.32/ov511_core.c:4749: error: implicit declaration of function ‘video_usercopy’
/home/keene/Downloads/ov511-2.32/ov511_core.c: In function ‘ov51x_read’:
/home/keene/Downloads/ov511-2.32/ov511_core.c:4765: warning: initialization makes pointer from integer without a cast
/home/keene/Downloads/ov511-2.32/ov511_core.c: In function ‘ov51x_mmap’:
/home/keene/Downloads/ov511-2.32/ov511_core.c:4920: warning: initialization makes pointer from integer without a cast
/home/keene/Downloads/ov511-2.32/ov511_core.c: At top level:
/home/keene/Downloads/ov511-2.32/ov511_core.c:4974: error: ‘v4l_compat_ioctl32’ undeclared here (not in a function)
/home/keene/Downloads/ov511-2.32/ov511_core.c:4979: error: variable ‘vdev_template’ has initializer but incomplete type
/home/keene/Downloads/ov511-2.32/ov511_core.c:4980: error: unknown field ‘owner’ specified in initializer
/home/keene/Downloads/ov511-2.32/ov511_core.c:4980: warning: excess elements in struct initializer
/home/keene/Downloads/ov511-2.32/ov511_core.c:4980: warning: (near initialization for ‘vdev_template’)
/home/keene/Downloads/ov511-2.32/ov511_core.c:4981: error: unknown field ‘name’ specified in initializer
/home/keene/Downloads/ov511-2.32/ov511_core.c:4981: warning: excess elements in struct initializer
/home/keene/Downloads/ov511-2.32/ov511_core.c:4981: warning: (near initialization for ‘vdev_template’)
/home/keene/Downloads/ov511-2.32/ov511_core.c:4982: error: unknown field ‘type’ specified in initializer
/home/keene/Downloads/ov511-2.32/ov511_core.c:4982: warning: excess elements in struct initializer
/home/keene/Downloads/ov511-2.32/ov511_core.c:4982: warning: (near initialization for ‘vdev_template’)
/home/keene/Downloads/ov511-2.32/ov511_core.c:4983: error: unknown field ‘hardware’ specified in initializer
/home/keene/Downloads/ov511-2.32/ov511_core.c:4983: error: ‘VID_HARDWARE_OV511’ undeclared here (not in a function)
/home/keene/Downloads/ov511-2.32/ov511_core.c:4983: warning: excess elements in struct initializer
/home/keene/Downloads/ov511-2.32/ov511_core.c:4983: warning: (near initialization for ‘vdev_template’)
/home/keene/Downloads/ov511-2.32/ov511_core.c:4984: error: unknown field ‘fops’ specified in initializer
/home/keene/Downloads/ov511-2.32/ov511_core.c:4984: warning: excess elements in struct initializer
/home/keene/Downloads/ov511-2.32/ov511_core.c:4984: warning: (near initialization for ‘vdev_template’)
/home/keene/Downloads/ov511-2.32/ov511_core.c:4986: error: unknown field ‘release’ specified in initializer
/home/keene/Downloads/ov511-2.32/ov511_core.c:4986: error: ‘video_device_release’ undeclared here (not in a function)
/home/keene/Downloads/ov511-2.32/ov511_core.c:4986: warning: excess elements in struct initializer
/home/keene/Downloads/ov511-2.32/ov511_core.c:4986: warning: (near initialization for ‘vdev_template’)
/home/keene/Downloads/ov511-2.32/ov511_core.c:4988: error: unknown field ‘minor’ specified in initializer
/home/keene/Downloads/ov511-2.32/ov511_core.c:4988: warning: excess elements in struct initializer
/home/keene/Downloads/ov511-2.32/ov511_core.c:4988: warning: (near initialization for ‘vdev_template’)
/home/keene/Downloads/ov511-2.32/ov511_core.c: In function ‘cd_to_ov’:
/home/keene/Downloads/ov511-2.32/ov511_core.c:5543: error: implicit declaration of function ‘to_video_device’
/home/keene/Downloads/ov511-2.32/ov511_core.c:5543: warning: initialization makes pointer from integer without a cast
/home/keene/Downloads/ov511-2.32/ov511_core.c:5544: warning: return makes pointer from integer without a cast
/home/keene/Downloads/ov511-2.32/ov511_core.c: In function ‘show_sensor’:
/home/keene/Downloads/ov511-2.32/ov511_core.c:5571: error: ‘senlist’ undeclared (first use in this function)
/home/keene/Downloads/ov511-2.32/ov511_core.c:5571: error: (Each undeclared identifier is reported only once
/home/keene/Downloads/ov511-2.32/ov511_core.c:5571: error: for each function it appears in.)
/home/keene/Downloads/ov511-2.32/ov511_core.c: In function ‘ov_create_sysfs’:
/home/keene/Downloads/ov511-2.32/ov511_core.c:5637: error: implicit declaration of function ‘video_device_create_file’
/home/keene/Downloads/ov511-2.32/ov511_core.c: In function ‘ov51x_probe’:
/home/keene/Downloads/ov511-2.32/ov511_core.c:5815: error: implicit declaration of function ‘video_device_alloc’
/home/keene/Downloads/ov511-2.32/ov511_core.c:5815: warning: assignment makes pointer from integer without a cast
/home/keene/Downloads/ov511-2.32/ov511_core.c:5819: error: dereferencing pointer to incomplete type
/home/keene/Downloads/ov511-2.32/ov511_core.c:5819: error: dereferencing pointer to incomplete type
/home/keene/Downloads/ov511-2.32/ov511_core.c:5821: error: dereferencing pointer to incomplete type
/home/keene/Downloads/ov511-2.32/ov511_core.c:5823: error: implicit declaration of function ‘video_set_drvdata’
/home/keene/Downloads/ov511-2.32/ov511_core.c:5829: error: implicit declaration of function ‘video_register_device’
/home/keene/Downloads/ov511-2.32/ov511_core.c:5829: error: ‘VFL_TYPE_GRABBER’ undeclared (first use in this function)
/home/keene/Downloads/ov511-2.32/ov511_core.c:5835: error: dereferencing pointer to incomplete type
/home/keene/Downloads/ov511-2.32/ov511_core.c:5850: error: dereferencing pointer to incomplete type
/home/keene/Downloads/ov511-2.32/ov511_core.c:5856: error: dereferencing pointer to incomplete type
/home/keene/Downloads/ov511-2.32/ov511_core.c:5860: error: dereferencing pointer to incomplete type
/home/keene/Downloads/ov511-2.32/ov511_core.c:5882: error: dereferencing pointer to incomplete type
/home/keene/Downloads/ov511-2.32/ov511_core.c:5883: error: implicit declaration of function ‘video_device_release’
/home/keene/Downloads/ov511-2.32/ov511_core.c:5885: error: implicit declaration of function ‘video_unregister_device’
make[2]: *** [/home/keene/Downloads/ov511-2.32/ov511_core.o] Error 1
make[1]: *** [_module_/home/keene/Downloads/ov511-2.32] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [default] Error 2

```

I tried editing the Makefile to point to different source directories, but I always got the same or similar errors. I also tried different versions of ov511 source as well, again with the same or similar errors.

So I ran into a dead end there.

The camera is listed as working on the ov511 project's camera list:
[http://alpha.dyndns.org/ov511/cameras.html](http://alpha.dyndns.org/ov511/cameras.html)

but it says it uses the ovfx2 driver.

I have no idea what else to try. Help?

---

