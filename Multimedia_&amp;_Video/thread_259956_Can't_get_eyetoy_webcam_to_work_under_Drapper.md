---
title: "Can't get eyetoy webcam to work under Drapper"
date: 2006-09-18
forum: Multimedia &amp; Video
---

### Post by perl105 on 2006-09-18
Hi

Ive been searched around these forums and on google.  I've mainly been following this thread on the forums:

[http://ubuntuforums.org/showthread.php?t=12079&highlight=eyetoy](http://ubuntuforums.org/showthread.php?t=12079&highlight=eyetoy)

but no matter what I try I get problems installing the driver and just can't seem to get it to work.



I have tried the Dapper guide at foolish.home.insightbb.com and I get the following errors.

```
gil@gc-desktop:~/Downloads/ov51x-jpeg-0.5.2$ sudo rmmod ov511
ERROR: Module ov511 does not exist in /proc/modules
gil@gc-desktop:~/Downloads/ov51x-jpeg-0.5.2$ sudo modprobe videodev
gil@gc-desktop:~/Downloads/ov51x-jpeg-0.5.2$
gil@gc-desktop:~/Downloads/ov51x-jpeg-0.5.2$ sudo modprobe i2c_core
gil@gc-desktop:~/Downloads/ov51x-jpeg-0.5.2$ sudo insmod /lib/modules/`uname -r`/extra/ov51x.ko
insmod: error inserting '/lib/modules/2.6.15-26-386/extra/ov51x.ko': -1 File exists
gil@gc-desktop:~/Downloads/ov51x-jpeg-0.5.2$ sudo insmod /lib/modules/`uname -r`/extra/ov519_decomp.ko
insmod: error inserting '/lib/modules/2.6.15-26-386/extra/ov519_decomp.ko': -1 Unknown symbol in module
gil@gc-desktop:~/Downloads/ov51x-jpeg-0.5.2$

```

Im completely new to Linux and being able to use a webcam will stop my frequent swicthing back to Windows everytime I need to chat with someone and use it at the same time.

Any ideas would be great.  Also I am planning to use the webcam with MSN Messenger service primarily and I believe that aMSN is the client to use.  Are there any others that support webcams?  Or any plugins for other clients such as GAIM/Jabber/Skype?


I am on Ubuntu 6.06 (Dapper Drake) btw.

---

### Post by perl105 on 2006-09-18
I found this on the rasatgeeks website 


When I modprobe ov519_decomp it complains about unknown symbols. What's wrong?

If you're getting similar messages in dmesg:

ov519_decomp: disagrees about version of symbol ov511_deregister_decomp_module
ov519_decomp: Unknown symbol ov511_deregister_decomp_module
ov519_decomp: disagrees about version of symbol ov511_register_decomp_module
ov519_decomp: Unknown symbol ov511_register_decomp_module

It's likely that the ov511 driver included in the 2.6 kernel is getting in the way. Move it someplace and try again:

# mv /lib/modules/`uname -r`/kernel/drivers/usb/media/ov511.ko \
     /lib/modules/`uname -r`/kernel/drivers/usb/media/ov511.ko.orig
# depmod -a
# modprobe ov519_decomp

but still no luck

This is the output I get from the above:

```
gil@gc-desktop:~/Downloads/ov51x-jpeg-0.5.2$ mv /lib/modules/`uname -r`/kernel/drivers/usb/media/ov511.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/ov511.ko.orig
mv: cannot stat `/lib/modules/2.6.15-26-386/kernel/drivers/usb/media/ov511.ko': No such file or directory
gil@gc-desktop:~/Downloads/ov51x-jpeg-0.5.2$ sudo depmod -a gil@gc-desktop:~/Downloads/ov51x-jpeg-0.5.2$ sudo modprobe ov519_decomp FATAL: Error inserting ov519_decomp (/lib/modules/2.6.15-26-386/extra/ov519_decomp.ko): Unknown symbol in module, or unknown parameter (see dmesg)
gil@gc-desktop:~/Downloads/ov51x-jpeg-0.5.2$

```

---

