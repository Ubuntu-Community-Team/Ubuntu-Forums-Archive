---
title: "Trouble Compiling a Sierra Wireless Driver"
date: 2009-04-18
forum: Networking &amp; Wireless
---

### Post by richardq on 2009-04-18
Hi,

I'm trying to compile a driver for a Sierra 597 Wireless USB thingy.. I downloaded the source package from Sierra's site but I seem to be having a problem compiling it.

I've got build-essentials and the linux-headers package installed. I've compiled other things without problems. I'm getting a strange message when I compile. Strange because it really sounds like a problem with their source. Obviously I've done some checks here and it appears lots of other people have successfully compiled the drivers in Ubuntu before, so it's got to be something on my end.

Here's the start of the compile:

```
richard@midge:~/downloads/sierra$ make
make -C /lib/modules/2.6.27-9-generic/build SUBDIRS=/home/richard/downloads/sierra modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /home/richard/downloads/sierra/sierra.o
/home/richard/downloads/sierra/sierra.c: In function ‘sierra_send_setup’:
/home/richard/downloads/sierra/sierra.c:198: error: ‘struct usb_serial_port’ has no member named ‘tty’
/home/richard/downloads/sierra/sierra.c: In function ‘sierra_set_termios’:
/home/richard/downloads/sierra/sierra.c:233: error: ‘struct usb_serial_port’ has no member named ‘tty’
```

Any idea why I'm getting this series of errors? From there it just cascades and the compile fails very shortly thereafter.

---

### Post by chili555 on 2009-04-18
First, I think your kernel includes a *sierra.ko* module. When you plug in your modem, does it fail to attach the sierra module? Can you modprobe it?

Second, can you give us a link to where you downloaded the package from Sierra's site? I found downloads specific to each kernel version. I downloaded mine, 2.6.28 in my case, and 'make' ran perfectly.

---

