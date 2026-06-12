---
title: "Help installing (non-supported?) Pixasrt webcam, please"
date: 2009-04-29
forum: Multimedia Software
---

### Post by jjalocha on 2009-04-29
Hi, I am trying to install the following webcam under Xubuntu Jaunty:
```
$ lsusb
Bus 003 Device 002: ID 093a:2461 Pixart Imaging, Inc.
```

No /dev/video* devices are visible.

From older forum threads, it looks as if the spca5xx should be installed. But this specific model (2461) is *not* listed in the [spca5xx's home page]("http://mxhaard.free.fr/spca5xx.html"), even though similar numbers such as 2460 and 2468 *are*.

Googling, I found something that looks like a [linux kernel driver]("http://cateee.net/lkddb/web-lkddb/USB_GSPCA_PAC207.html") for this specific model, but I have no idea how to install it.

I will truly appreciate any guidance or help with this.

EDIT: Sorry, forgot to mention, that it does not seem to be [UVC]("http://linux-uvc.berlios.de/") compatible.

---

### Post by jjalocha on 2009-04-29
OK, some new insight, but still not working...

The GSPCA PAC207 kernel driver seems to exist by default in Xubuntu Jaunty:

```
$ modprobe -l | grep pac207
kernel/drivers/media/video/gspca/gspca_pac207.ko
```

But lsmod doesn't show anything related to it:

```
$ sudo lsmod | grep gspca
```

I also installed camorama, but I get the following error at startup:

> Error (camorama)
Could not connect to video device (/dev/video0).
Please check connection.

As I explained in my first post, there aren't any video devices in /dev.

---

### Post by xc3RnbFO8P on 2009-04-29
Read this (kernel 2.6.29):
[http://patchwork.kernel.org/patch/14926/]("http://patchwork.kernel.org/patch/14926/")

---

### Post by jjalocha on 2009-04-29
:-k hmmm... sorry... but I really can't make anything out of that link...
This patch adds a new (010f) device to the 2.6.29 kernel, while I am trying to use the 2461 device on the default Jaunty kernel, which I believe, is 2.6.28. I think, I need more help... I am really not that knowledgeable!

---

### Post by xc3RnbFO8P on 2009-04-29
If you can wait til the next release of Ubuntu or you can try to compile V4L ( I not sure if it works).
[http://www.mail-archive.com/linuxtv-commits@linuxtv.org/msg02274.html]("http://www.mail-archive.com/linuxtv-commits@linuxtv.org/msg02274.html")

---

### Post by jjalocha on 2009-04-29
Ahh, OK, I understand now! But shouldn't I better stick with the [GSPCA PAC207]("http://cateee.net/lkddb/web-lkddb/USB_GSPCA_PAC207.html") driver which is already included in Jaunty, and according to the previous link *should* support my 2461 webcam?

The question, of course, is *why* doesn't it work on my computer? What am I missing?

---

### Post by xc3RnbFO8P on 2009-04-29
It could be this bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/255678]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/255678")

---

### Post by jjalocha on 2009-04-29
Thank you, Ringi, you are right, there seems to be a series of related bugs open right now, on webcams. I will try to search for a fix there.

Meanwhile, I figured out how to load the missing kernel module manually (no idea why it isn't loading automagically, though):

```
$ sudo modprobe -v gspca_pac207
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
insmod /lib/modules/2.6.28-11-generic/kernel/drivers/media/video/v4l1-compat.ko 
insmod /lib/modules/2.6.28-11-generic/kernel/drivers/media/video/videodev.ko 
insmod /lib/modules/2.6.28-11-generic/kernel/drivers/media/video/gspca/gspca_main.ko 
insmod /lib/modules/2.6.28-11-generic/kernel/drivers/media/video/gspca/gspca_pac207.ko 

```

And the modules seem to load correctly:

```
$ lsmod | grep gsp
gspca_pac207           14592  0 
gspca_main             29952  1 gspca_pac207
videodev               41600  1 gspca_main

```

Once loaded, the webcam stops showing up in USB, but after several times of unplugging/plugging, and waiting, it shows up again with lsusb.

The situation here is not exactly the same as in [Bug #255678]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/255678"), because here the device seems to be recognized, but not probed by gspca:

```
$ dmesg | tail
...
[27575.672039] usb 3-3: new full speed USB device using ohci_hcd and address 5
[27575.901649] usb 3-3: configuration #1 chosen from 1 choice
```

(There are no messages about gspca probing after that.)

---

