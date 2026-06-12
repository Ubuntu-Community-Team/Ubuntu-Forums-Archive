---
title: "Bipac-7000 Adsl USB Modem - can not install driver"
date: 2006-05-05
forum: Networking &amp; Wireless
---

### Post by coolinen on 2006-05-05
I have downloaded standard Linux Drivers for my Bipac-7000 Adsl Modem. After I connect the modem, device manager shows it just fine. But on #make step I get the following error. 

ln: `/lib/modules/2.6.12-9-386/build': File exists
gcc -O2 -fomit-frame-pointer -fno-strict-aliasing -pipe -fno-strength-reduce -DCPU=686 -march=i686  -DMODULE -D__KERNEL__ -DLINUX  -I/lib/modules/`uname -r`/build/include -c usbsndcm.c -o usbsndcm.o
In file included from usbsndcm.c:20:
hasbani.h:28:24: error: linux/slab.h: No such file or directory
In file included from /usr/include/linux/sched.h:16,
                 from /usr/include/linux/smp_lock.h:4,
                 from hasbani.h:30,
                 from usbsndcm.c:20:
/usr/include/linux/signal.h:2:2: warning: #warning "You should include <signal.h>. This time I will do it for you."
In file included from /usr/include/linux/resource.h:4,
                 from /usr/include/linux/sched.h:79,
                 from /usr/include/linux/smp_lock.h:4,
                 from hasbani.h:30,
                 from usbsndcm.c:20:
/usr/include/linux/time.h:9: error: redefinition of ‘struct timespec’
/usr/include/linux/time.h:15: error: redefinition of ‘struct timeval’
/usr/include/linux/time.h:20: error: redefinition of ‘struct timezone’
/usr/include/linux/time.h:47: error: redefinition of ‘struct itimerval’
In file included from hasbani.h:31,
                 from usbsndcm.c:20:
/usr/include/linux/module.h:41: error: field ‘attr’ has incomplete type
/usr/include/linux/module.h:49: error: field ‘kobj’ has incomplete type
In file included from hasbani.h:32,
                 from usbsndcm.c:20:
/usr/include/linux/skbuff.h:24:26: error: net/checksum.h: No such file or directory
In file included from hasbani.h:32,
                 from usbsndcm.c:20:
/usr/include/linux/skbuff.h:115: error: syntax error before ‘spinlock_t’
/usr/include/linux/skbuff.h:135: error: syntax error before ‘atomic_t’
/usr/include/linux/skbuff.h:140: error: variable-size type declared outside of any function
/usr/include/linux/skbuff.h:141: error: syntax error before ‘}’ token
/usr/include/linux/skbuff.h:272: error: syntax error before ‘atomic_t’
/usr/include/linux/skbuff.h:277: error: syntax error before ‘}’ token
In file included from usbsndcm.c:20:
hasbani.h:37:32: error: linux/etherdevice.h: No such file or directory
hasbani.h:39:25: error: asm/uaccess.h: No such file or directory
In file included from usbsndcm.c:20:
hasbani.h:69: error: field ‘send_queue_head’ has incomplete type
hasbani.h:69: error: field ‘recv_queue_head’ has incomplete type
hasbani.h:71: error: syntax error before ‘spinlock_t’
hasbani.h:71: warning: no semicolon at end of struct or union
hasbani.h:72: warning: data definition has no type or storage class
hasbani.h:73: error: syntax error before ‘cmdrecvqlock’
hasbani.h:73: warning: data definition has no type or storage class
hasbani.h:81: error: syntax error before ‘iscomplete’
hasbani.h:81: warning: data definition has no type or storage class
hasbani.h:93: error: syntax error before ‘}’ token
In file included from usbsndcm.c:25:
usbsndcm.h:204: error: syntax error before ‘usb_complete_t’
usbsndcm.h:213: error: syntax error before ‘usb_complete_t’
usbsndcm.c:139: error: syntax error before ‘usb_complete_t’
usbsndcm.c: In function ‘CmCommandRcv’:
usbsndcm.c:166: warning: incompatible implicit declaration of built-in function ‘memset’
usbsndcm.c:179: error: ‘usb_complete_t’ undeclared (first use in this function)
usbsndcm.c:179: error: (Each undeclared identifier is reported only once
usbsndcm.c:179: error: for each function it appears in.)
usbsndcm.c:179: error: syntax error before ‘BlReadTransactionComplete’
usbsndcm.c:184: error: dereferencing pointer to incomplete type
usbsndcm.c: In function ‘CmCommandSend’:
usbsndcm.c:233: error: dereferencing pointer to incomplete type
usbsndcm.c:242: warning: incompatible implicit declaration of built-in function ‘memset’
usbsndcm.c:252: error: ‘usb_complete_t’ undeclared (first use in this function)
usbsndcm.c:252: error: syntax error before ‘BlTransactionComplete’
usbsndcm.c:259: error: dereferencing pointer to incomplete type
usbsndcm.c: In function ‘CmPacketSend’:
usbsndcm.c:300: error: dereferencing pointer to incomplete type
usbsndcm.c:321: error: ‘usb_complete_t’ undeclared (first use in this function)
usbsndcm.c:321: error: syntax error before ‘BlTransactionComplete’
usbsndcm.c:327: error: dereferencing pointer to incomplete type
usbsndcm.c: At top level:
usbsndcm.c:345: error: syntax error before ‘usb_complete_t’
usbsndcm.c: In function ‘CmConfigParamSend’:
usbsndcm.c:376: error: ‘GFP_KERNEL’ undeclared (first use in this function)
usbsndcm.c:376: warning: assignment makes pointer from integer without a cast
usbsndcm.c:384: warning: incompatible implicit declaration of built-in function ‘memset’
usbsndcm.c:407: error: ‘eCommand’ undeclared (first use in this function)
usbsndcm.c:411: error: ‘KERN_DEBUG’ undeclared (first use in this function)
usbsndcm.c:411: error: syntax error before string constant
usbsndcm.c:416: error: ‘DeviceObject’ undeclared (first use in this function)
make: *** [usbsndcm.o] Error 1

Any help to install this modem and have it running will be greatly appreciated. 

I am a complete Newbie installing Ubuntu or Linux for that matter, first time in my life. 

Thanks

---

