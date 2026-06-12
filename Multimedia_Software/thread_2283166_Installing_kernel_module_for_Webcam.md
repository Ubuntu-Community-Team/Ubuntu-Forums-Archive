---
title: "Installing kernel module for Webcam"
date: 2015-06-19
forum: Multimedia Software
---

### Post by kjetil-fleten on 2015-06-19
Hi 
I have a USB webcam, that requires the Sonix SN9C1xx PC camera controller, [SIZE=1]available here:
[/SIZE]http://www.linux-projects.org/modules/mydownloads/viewcat.php?cid=2

Is the module a part of any known package, or do I need to make the module from the tarball ?
I tried that, but got this error, when running make:
```
*************************************************************************
* Building Video4Linux2 driver v1.50 for SN9C1xx PC Camera Controllers...*
* Official Linux 2.6.19 is the minimum version for this driver.          *
* Read the documentation "sn9c102.txt" for more informations.            *
* Type "make help" for a list of available targets.                      *
**************************************************************************


make -C /lib/modules/`uname -r`/build M=/home/kjetil/Data/Webcam/sn9c1xx-1.50 modules
make[1]: Går til katalog '/usr/src/linux-headers-3.13.0-53-generic'
  CC [M]  /home/kjetil/Data/Webcam/sn9c1xx-1.50/sn9c102_core.o
In file included from include/linux/module.h:17:0,
                 from /home/kjetil/Data/Webcam/sn9c1xx-1.50/sn9c102_core.c:21:
/home/kjetil/Data/Webcam/sn9c1xx-1.50/sn9c102_core.c: In function ‘__check_max_opens’:
include/linux/moduleparam.h:349:45: warning: return from incompatible pointer type [enabled by default]
  static inline type *__check_##name(void) { return(p); }
                                             ^
include/linux/moduleparam.h:374:35: note: in expansion of macro ‘__param_check’
 #define param_check_uint(name, p) __param_check(name, p, unsigned int)
                                   ^
include/linux/moduleparam.h:436:2: note: in expansion of macro ‘param_check_uint’
  param_check_##type(name, &(array)[0]);    \
  ^
include/linux/moduleparam.h:422:2: note: in expansion of macro ‘module_param_array_named’
  module_param_array_named(name, name, type, nump, perm)
  ^
/home/kjetil/Data/Webcam/sn9c1xx-1.50/sn9c102_core.c:79:1: note: in expansion of macro ‘module_param_array’
 module_param_array(max_opens, uint, NULL, 0644);
 ^
/home/kjetil/Data/Webcam/sn9c1xx-1.50/sn9c102_core.c: In function ‘__check_force_munmap’:
include/linux/moduleparam.h:349:45: warning: return from incompatible pointer type [enabled by default]
  static inline type *__check_##name(void) { return(p); }
                                             ^
include/linux/moduleparam.h:395:35: note: in expansion of macro ‘__param_check’
 #define param_check_bool(name, p) __param_check(name, p, bool)
                                   ^
include/linux/moduleparam.h:436:2: note: in expansion of macro ‘param_check_bool’
  param_check_##type(name, &(array)[0]);    \
  ^
include/linux/moduleparam.h:422:2: note: in expansion of macro ‘module_param_array_named’
  module_param_array_named(name, name, type, nump, perm)
  ^
/home/kjetil/Data/Webcam/sn9c1xx-1.50/sn9c102_core.c:89:1: note: in expansion of macro ‘module_param_array’
 module_param_array(force_munmap, bool, NULL, 0644);
 ^
/home/kjetil/Data/Webcam/sn9c1xx-1.50/sn9c102_core.c: In function ‘sn9c102_create_sysfs’:
/home/kjetil/Data/Webcam/sn9c1xx-1.50/sn9c102_core.c:1437:41: error: ‘struct video_device’ has no member named ‘class_dev’
  struct device *classdev = &(cam->v4ldev->class_dev);
                                         ^
/home/kjetil/Data/Webcam/sn9c1xx-1.50/sn9c102_core.c: In function ‘sn9c102_mmap’:
/home/kjetil/Data/Webcam/sn9c1xx-1.50/sn9c102_core.c:2152:19: error: ‘VM_RESERVED’ undeclared (first use in this function)
  vma->vm_flags |= VM_RESERVED;
                   ^
/home/kjetil/Data/Webcam/sn9c1xx-1.50/sn9c102_core.c:2152:19: note: each undeclared identifier is reported only once for each function it appears in
/home/kjetil/Data/Webcam/sn9c1xx-1.50/sn9c102_core.c: In function ‘sn9c102_vidioc_querycap’:
/home/kjetil/Data/Webcam/sn9c1xx-1.50/sn9c102_core.c:2188:41: error: ‘struct device’ has no member named ‘bus_id’
   strlcpy(cap.bus_info, cam->usbdev->dev.bus_id,
                                         ^
/home/kjetil/Data/Webcam/sn9c1xx-1.50/sn9c102_core.c: In function ‘sn9c102_ioctl’:
/home/kjetil/Data/Webcam/sn9c1xx-1.50/sn9c102_core.c:3253:2: error: implicit declaration of function ‘v4l_print_ioctl’ [-Werror=implicit-function-declaration]
  V4LDBG(3, "sn9c102", cmd);
  ^
/home/kjetil/Data/Webcam/sn9c1xx-1.50/sn9c102_core.c: At top level:
/home/kjetil/Data/Webcam/sn9c1xx-1.50/sn9c102_core.c:3289:2: error: unknown field ‘ioctl’ specified in initializer
  .ioctl = sn9c102_ioctl,
  ^
/home/kjetil/Data/Webcam/sn9c1xx-1.50/sn9c102_core.c:3289:2: warning: initialization from incompatible pointer type [enabled by default]
/home/kjetil/Data/Webcam/sn9c1xx-1.50/sn9c102_core.c:3289:2: warning: (near initialization for ‘sn9c102_fops.fsync’) [enabled by default]
/home/kjetil/Data/Webcam/sn9c1xx-1.50/sn9c102_core.c:3291:18: error: ‘v4l_compat_ioctl32’ undeclared here (not in a function)
  .compat_ioctl = v4l_compat_ioctl32,
                  ^
/home/kjetil/Data/Webcam/sn9c1xx-1.50/sn9c102_core.c: In function ‘sn9c102_usb_probe’:
/home/kjetil/Data/Webcam/sn9c1xx-1.50/sn9c102_core.c:3389:13: error: ‘struct video_device’ has no member named ‘owner’
  cam->v4ldev->owner = THIS_MODULE;
             ^
/home/kjetil/Data/Webcam/sn9c1xx-1.50/sn9c102_core.c:3390:13: error: ‘struct video_device’ has no member named ‘type’
  cam->v4ldev->type = VID_TYPE_CAPTURE | VID_TYPE_SCALES;
             ^
/home/kjetil/Data/Webcam/sn9c1xx-1.50/sn9c102_core.c:3390:22: error: ‘VID_TYPE_CAPTURE’ undeclared (first use in this function)
  cam->v4ldev->type = VID_TYPE_CAPTURE | VID_TYPE_SCALES;
                      ^
/home/kjetil/Data/Webcam/sn9c1xx-1.50/sn9c102_core.c:3390:41: error: ‘VID_TYPE_SCALES’ undeclared (first use in this function)
  cam->v4ldev->type = VID_TYPE_CAPTURE | VID_TYPE_SCALES;
                                         ^
/home/kjetil/Data/Webcam/sn9c1xx-1.50/sn9c102_core.c:3391:13: error: ‘struct video_device’ has no member named ‘hardware’
  cam->v4ldev->hardware = 0;
             ^
/home/kjetil/Data/Webcam/sn9c1xx-1.50/sn9c102_core.c:3392:20: warning: assignment from incompatible pointer type [enabled by default]
  cam->v4ldev->fops = &sn9c102_fops;
                    ^
/home/kjetil/Data/Webcam/sn9c1xx-1.50/sn9c102_core.c:3395:19: error: incompatible types when assigning to type ‘struct device’ from type ‘struct device *’
  cam->v4ldev->dev = &udev->dev;
                   ^
cc1: some warnings being treated as errors
make[2]: *** [/home/kjetil/Data/Webcam/sn9c1xx-1.50/sn9c102_core.o] Fejl 1
make[1]: *** [_module_/home/kjetil/Data/Webcam/sn9c1xx-1.50] Fejl 2
make[1]: Forlader katalog '/usr/src/linux-headers-3.13.0-53-generic'
make: *** [modules] Fejl 2



```

How can I proceed ?

---

### Post by Bucky Ball on 2015-06-19
*Thread moved to **Multimedia**.*

Might have more luck here. What happens when you plug it in? 

Reboot the machine, get to a desktop, wait for things to get stable, plug the camera in, open a terminal and run:

```
dmesg
```

Show the last part of the output at the bottom which will be about what you just plugged in. If it's loading a driver, it will show it, but if it doesn't that doesn't necessarily mean the driver is not already in the kernel. :)

Please provide the make and model of the camera.

---

### Post by kjetil-fleten on 2015-06-20
Hmmm, output of dmesg does not look good:

```
65.384044] usb 6-1: new full-speed USB device number 2 using uhci_hcd
[   65.512048] usb 6-1: device descriptor read/64, error -71
[   65.740046] usb 6-1: device descriptor read/64, error -71
[   65.956048] usb 6-1: new full-speed USB device number 3 using uhci_hcd
[   66.080044] usb 6-1: device descriptor read/64, error -71
[   66.308049] usb 6-1: device descriptor read/64, error -71
[   66.524046] usb 6-1: new full-speed USB device number 4 using uhci_hcd
[   66.940023] usb 6-1: device not accepting address 4, error -71
[   67.052048] usb 6-1: new full-speed USB device number 5 using uhci_hcd
[   67.460036] usb 6-1: device not accepting address 5, error -71
[   67.460071] hub 6-0:1.0: unable to enumerate USB device on port 1
[   68.438954] vboxdrv: Found 4 processor cores.
[   68.439218] vboxdrv: fAsync=0 offMin=0x373 offMax=0x2ef1
[   68.439326] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   68.439328] vboxdrv: Successfully loaded version 4.3.10_Ubuntu (interface 0x001a0007).
[   68.468485] vboxpci: IOMMU not found (not registered)

```
It seems like the device will not be accepted at all. Could it be wrong USB tandard ?
The webcam is a Medion MD85081. But I found somewhere on the Internet, that it actually works with Sonix sn9c1xx module.
If I could only get the camera accepted by USB, and the kernel module installed ...

---

