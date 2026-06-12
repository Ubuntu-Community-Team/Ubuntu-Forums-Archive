---
title: ": DVD Xpress DX2"
date: 2010-01-20
forum: Multimedia Software
---

### Post by X-Seti on 2010-01-20
Driver support needed for the DVD Xpress DX2

2 Years now I have been trying to get the wis-go7007-linux-0.9.8 driver to work with 7.04, 8.04, 8.10, and now 9.10.

It seems the driver released was only meant to be for kernel 2.6.10+

This was around the time Ubuntu 5.04 was released and looking around the net there doesn't seem to be any up to date links to follow to get this device working.

I am on Ubuntu9.10, and there doesn't seem to be a way to get this video capture/ video grabber to work.

When compiling the device a get a ton of errors;

 ```
k@mdev:~/wis-go7007-linux-0.9.8$ make

***** Using kernel source in /usr/src/linux-headers-2.6.31-17-generic-pae *****

make modules -C /usr/src/linux-headers-2.6.31-17-generic-pae M=/home/k/wis-go7007-linux-0.9.8/kernel
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-17-generic-pae'
  CC [M]  /home/k/wis-go7007-linux-0.9.8/kernel/go7007-v4l2.o
/home/k/wis-go7007-linux-0.9.8/kernel/go7007-v4l2.c:33:33: error: linux/video_decoder.h: No such file or directory
/home/k/wis-go7007-linux-0.9.8/kernel/go7007-v4l2.c:41:27: error: asm/semaphore.h: No such file or directory
/home/k/wis-go7007-linux-0.9.8/kernel/go7007-v4l2.c: In function &#8216;go7007_do_ioctl&#8217;:
/home/k/wis-go7007-linux-0.9.8/kernel/go7007-v4l2.c:797: error: implicit declaration of function &#8216;v4l2_video_std_construct&#8217;
/home/k/wis-go7007-linux-0.9.8/kernel/go7007-v4l2.c:878: error: &#8216;DECODER_SET_NORM&#8217; undeclared (first use in this function)
/home/k/wis-go7007-linux-0.9.8/kernel/go7007-v4l2.c:878: error: (Each undeclared identifier is reported only once
/home/k/wis-go7007-linux-0.9.8/kernel/go7007-v4l2.c:878: error: for each function it appears in.)
/home/k/wis-go7007-linux-0.9.8/kernel/go7007-v4l2.c:942: error: &#8216;DECODER_SET_INPUT&#8217; undeclared (first use in this function)
/home/k/wis-go7007-linux-0.9.8/kernel/go7007-v4l2.c: In function &#8216;go7007_ioctl&#8217;:
/home/k/wis-go7007-linux-0.9.8/kernel/go7007-v4l2.c:1350: error: implicit declaration of function &#8216;video_usercopy&#8217;
/home/k/wis-go7007-linux-0.9.8/kernel/go7007-v4l2.c: In function &#8216;go7007_vm_nopage&#8217;:
/home/k/wis-go7007-linux-0.9.8/kernel/go7007-v4l2.c:1386: error: &#8216;NOPAGE_SIGBUS&#8217; undeclared (first use in this function)
/home/k/wis-go7007-linux-0.9.8/kernel/go7007-v4l2.c:1389: error: &#8216;NOPAGE_OOM&#8217; undeclared (first use in this function)
/home/k/wis-go7007-linux-0.9.8/kernel/go7007-v4l2.c: At top level:
/home/k/wis-go7007-linux-0.9.8/kernel/go7007-v4l2.c:1399: error: unknown field &#8216;nopage&#8217; specified in initializer
/home/k/wis-go7007-linux-0.9.8/kernel/go7007-v4l2.c:1399: warning: initialization from incompatible pointer type
/home/k/wis-go7007-linux-0.9.8/kernel/go7007-v4l2.c:1473: error: unknown field &#8216;type&#8217; specified in initializer
/home/k/wis-go7007-linux-0.9.8/kernel/go7007-v4l2.c:1474: warning: initialization from incompatible pointer type
/home/k/wis-go7007-linux-0.9.8/kernel/go7007-v4l2.c: In function &#8216;go7007_v4l2_init&#8217;:
/home/k/wis-go7007-linux-0.9.8/kernel/go7007-v4l2.c:1487: error: incompatible types when assigning to type &#8216;struct device&#8217; from type &#8216;struct device *&#8217;
make[2]: *** [/home/k/wis-go7007-linux-0.9.8/kernel/go7007-v4l2.o] Error 1
make[1]: *** [_module_/home/k/wis-go7007-linux-0.9.8/kernel] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-17-generic-pae'
make: *** [all] Error 2
k@mdev:~/wis-go7007-linux-0.9.8$ 
```

There seems to be DIR issues, and file issues with the latest Kernel changes

I have also tried other Kernels and get almost the same output.

Make install -i forces the install progress to move on.

Typing dmesg I get his;

```
[46184.141433] go7007: module is from the staging directory, the quality is unknown, you have been warned.
[46184.145624] go7007_usb: Unknown symbol __down_failed
[46184.145770] go7007_usb: disagrees about version of symbol go7007_read_addr
[46184.145773] go7007_usb: Unknown symbol go7007_read_addr
[46184.145885] go7007_usb: Unknown symbol __up_wakeup
[46184.146124] go7007_usb: Unknown symbol init_waitqueue_head
[46184.146214] go7007_usb: disagrees about version of symbol go7007_remove
[46184.146217] go7007_usb: Unknown symbol go7007_remove
[46184.146583] go7007_usb: disagrees about version of symbol go7007_boot_encoder
[46184.146586] go7007_usb: Unknown symbol go7007_boot_encoder
[46184.146762] go7007_usb: disagrees about version of symbol go7007_parse_video_stream
[46184.146765] go7007_usb: Unknown symbol go7007_parse_video_stream
[46184.147097] go7007_usb: disagrees about version of symbol go7007_register_encoder
[46184.147100] go7007_usb: Unknown symbol go7007_register_encoder
[46184.147193] go7007_usb: disagrees about version of symbol go7007_alloc
[46184.147196] go7007_usb: Unknown symbol go7007_alloc
[46184.147330] go7007_usb: Unknown symbol malloc_sizes
[46184.147420] go7007_usb: disagrees about version of symbol go7007_read_interrupt
[46184.147423] go7007_usb: Unknown symbol go7007_read_interrupt

```

The device can be seen from lsusb
```
Bus 001 Device 018: ID 06e1:0709 ADS Technologies, Inc. 

```

I am considering trashing this device, for something that is supported by Ubuntu 9.10, but what video capture is supported?

Edit; blundering on to the point where I might need to reinstall the box.

I tried something from another thread that I found on here posted around 2007.

[http://ubuntuforums.org/showthread.php?t=552996&page=2](http://ubuntuforums.org/showthread.php?t=552996&page=2)

This does not work for 9.10, so I am reinstalled the box.

---

### Post by Seagoat on 2010-02-18
I am experiencing the same problem with the ADS DVDXpress DX2 under Ubuntu. This is a bit of a surprise since my slide and flatbed scanners work seamlessly using [www.hamrick.com]("http://www.hamrick.com") Vuescan. Is there any move afoot to provide Ubuntu support for the ADS DVDXpress DX2 ? If not can anyone recommend a similar video capture device that is supported?

---

