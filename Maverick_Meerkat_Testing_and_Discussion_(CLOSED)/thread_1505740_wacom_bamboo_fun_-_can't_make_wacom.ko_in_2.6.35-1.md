---
title: "wacom bamboo fun - can't make wacom.ko in 2.6.35-1"
date: 2010-06-09
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by ubername on 2010-06-09
Hi

When I try to make wacom.ko using linuxwacom-0.8.8 under kernel 2.6.35-1 I get
```
john@MaverickUSB:~/Desktop/linuxwacom-0.8.8/src/2.6.30$ make
    Building linuxwacom drivers for 2.6 kernel.
***Note: Drivers not enabled as modules in your kernel config but requested through configure are NOT built
make -C /lib/modules/2.6.35-1-generic/build M=/home/john/Desktop/linuxwacom-0.8.8/src/2.6.30
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-1-generic'
  CC [M]  /home/john/Desktop/linuxwacom-0.8.8/src/2.6.30/wacom_sys.o
/home/john/Desktop/linuxwacom-0.8.8/src/2.6.30/wacom_sys.c: In function ‘wacom_probe’:
/home/john/Desktop/linuxwacom-0.8.8/src/2.6.30/wacom_sys.c:490: error: implicit declaration of function ‘usb_buffer_alloc’
/home/john/Desktop/linuxwacom-0.8.8/src/2.6.30/wacom_sys.c:491: warning: assignment makes pointer from integer without a cast
/home/john/Desktop/linuxwacom-0.8.8/src/2.6.30/wacom_sys.c:561: error: implicit declaration of function ‘usb_buffer_free’
make[2]: *** [/home/john/Desktop/linuxwacom-0.8.8/src/2.6.30/wacom_sys.o] Error 1
make[1]: *** [_module_/home/john/Desktop/linuxwacom-0.8.8/src/2.6.30] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-1-generic'
make: *** [all] Error 2
john@MaverickUSB:~/Desktop/linuxwacom-0.8.8/src/2.6.30$ 
```

The linux wacom page says 0.8.8 supports up to 2.6.35

Any clues?

---

### Post by ranch hand on 2010-06-09
I haven't tried our wacom out on 10.10.

I wonder if "up to 2.6.35" means just that.  It works through any version of 2.6.34.

I am sure that will be taken care of very soon in any case.

---

### Post by Favux on 2010-06-09
Hi ubername,

I agree with ranch hand.  For what you want shouldn't it read "Support kernels up to and including 2.6.35"?

It looks like you've already tried make in /Desktop/linuxwacom-0.8.8/src/2.6.30 and I presume /Desktop/linuxwacom-0.8.8.

---

### Post by ubername on 2010-06-09
Thanks both, maybe it does mean 'lower than 2.6.35'

The website says
```
Release 0.8.8 has been posted. It has the following new features:

Support kernels up to 2.6.35. Support X server up to 1.6.4. Support Cintiq 21UX2 and Intuos Wireless (USB Endpoint). Updated wacomcpl. Refer to ChangeLog for details.
Note: Support to this release is only backported to kernels 2.6.16 and later.

```

Anyone know where I might find the changelog mentioned?

---

### Post by nebosuke on 2010-06-09
The solution which gave me a functioning driver ist to change usb_buffer_alloc to usb_alloc_coherent and usb_buffer_free to usb_free_coherent respectively in wacom_sys.c
or simply run those two commands in src/2.5.30
```
sed -i 's/usb_buffer_alloc/usb_alloc_coherent/g' wacom_sys.c
sed -i 's/usb_buffer_free/usb_free_coherent/g' wacom_sys.c 
```
Then compile again.

---

### Post by ubername on 2010-06-09
> **nebosuke said:**
> The solution which gave me a functioning driver ist to change usb_buffer_alloc to usb_alloc_coherent and usb_buffer_free to usb_free_coherent respectively in wacom_sys.c
or simply run those two commands in src/2.5.30
```
sed -i 's/usb_buffer_alloc/usb_alloc_coherent/g' wacom_sys.c
sed -i 's/usb_buffer_free/usb_free_coherent/g' wacom_sys.c 
```
Then compile again.

Star!

Now working. (Still no 'tap to click' though)

---

### Post by Favux on 2010-06-09
Nice one nebosuke.

ubername have you cloned the xf86-input-wacom git repository?  A new 2 FG touch/gestures patch was committed less than a week ago.  They did update to macros 1.8 but with luck Meekat has too and you won't run into the 1.5 macro limitation of Lucid.

---

### Post by ubername on 2010-06-09
Hi Favux

Thanks, no, I haven't done that yet. Still a noob at this so I will have to dig around a bit for the instructions. I've seen you name on loads of posts about wacom stuff though, so I'm sure I'll be able to track it down, unless you have a mind to post a quick 'how to' here!

---

### Post by Favux on 2010-06-09
Already done.  See Appendix 5 here:  [http://ubuntuforums.org/showpost.php?p=6546012&postcount=1](http://ubuntuforums.org/showpost.php?p=6546012&postcount=1)

---

### Post by ubername on 2010-06-17
Now struggling with 2.6.35-4

Seems to build OK (with the 'sed' commands upthread)
and sort of loads

but I'm getting this in system messages:
```
Jun 17 18:00:55 MaverickUSB kernel: [   19.267909] wacom: disagrees about version of symbol input_allocate_device
Jun 17 18:00:55 MaverickUSB kernel: [   19.267917] wacom: Unknown symbol input_allocate_device (err -22)
Jun 17 18:00:55 MaverickUSB kernel: [   19.268651] wacom: disagrees about version of symbol input_unregister_device
Jun 17 18:00:55 MaverickUSB kernel: [   19.268656] wacom: Unknown symbol input_unregister_device (err -22)
Jun 17 18:00:55 MaverickUSB kernel: [   19.268827] wacom: disagrees about version of symbol input_free_device
Jun 17 18:00:55 MaverickUSB kernel: [   19.268832] wacom: Unknown symbol input_free_device (err -22)
Jun 17 18:00:55 MaverickUSB kernel: [   19.268888] wacom: disagrees about version of symbol input_register_device
Jun 17 18:00:55 MaverickUSB kernel: [   19.268892] wacom: Unknown symbol input_register_device (err -22)
Jun 17 18:00:55 MaverickUSB kernel: [   19.269190] wacom: disagrees about version of symbol input_set_capability
Jun 17 18:00:55 MaverickUSB kernel: [   19.269194] wacom: Unknown symbol input_set_capability (err -22)
Jun 17 18:00:55 MaverickUSB kernel: [   19.269517] wacom: disagrees about version of symbol input_event
Jun 17 18:00:55 MaverickUSB kernel: [   19.269522] wacom: Unknown symbol input_event (err -22)
```

Any clues?

TIA

---

### Post by nebosuke on 2010-06-17
Just did compile for 2.6.35-4-generic without a problem.

I think you still compiled for the older kernel, resulting in a version mismatch. Just rerun the ```
./configure --enable-wacom
``` command or change the Makefile in src/2.6.30 to
```
WCM_KERNEL_DIR := /lib/modules/2.6.35-4-generic/build
``` or your respective kernel.
You can probably also do something like
```
WCM_KERNEL_DIR := /lib/modules/`uname -r`/build
```
to always build for the current running kernel.

---

### Post by ubername on 2010-06-17
> **nebosuke said:**
> Just did compile for 2.6.35-4-generic without a problem.

I think you still compiled for the older kernel, resulting in a version mismatch. Just rerun the ```
./configure --enable-wacom
``` command or change the Makefile in src/2.6.30 to
```
WCM_KERNEL_DIR := /lib/modules/2.6.35-4-generic/build
``` or your respective kernel.
You can probably also do something like
```
WCM_KERNEL_DIR := /lib/modules/`uname -r`/build
```
to always build for the current running kernel.

Sorted! Thanks again.

I must really start to get to grips with what I am actually doing, rather than just cutting and pasting commands!

---

