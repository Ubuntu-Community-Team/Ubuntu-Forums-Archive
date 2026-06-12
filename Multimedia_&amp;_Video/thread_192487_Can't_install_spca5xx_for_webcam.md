---
title: "Can't install spca5xx for webcam"
date: 2006-06-08
forum: Multimedia &amp; Video
---

### Post by MikkelMJ on 2006-06-08
Hi, I've followed evry guide on I could find to get this working, but no matter what I do I end up with this error:
mikkel@mikkel-laptop:~/spca5xx-20060501$ sudo modprobe spca5xx
FATAL: Error inserting spca5xx (/lib/modules/2.6.15-23-386/kernel/drivers/usb/media/spca5xx.ko): Invalid module format

I don't know what to do, I feel like I've tried everything. Here's a transcript of my last attempt:

sudo apt-get install linux-headers-2.6.15-23-386 linux-restricted-modules-2.6.15-23-386 build-essential gcc-3.4

Then I downloaded and unpacked the newest driver. Then I did this:
mikkel@mikkel-laptop:~/spca5xx-20060501$ sudo make CC=gcc-3.4
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/mikkel/spca5xx-20060501 CC=gcc-3.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-23-386'
  CC [M]  /home/mikkel/spca5xx-20060501/drivers/usb/spca5xx.o
  CC [M]  /home/mikkel/spca5xx-20060501/drivers/usb/spcadecoder.o
  LD [M]  /home/mikkel/spca5xx-20060501/spca5xx.o
  Building modules, stage 2.
  MODPOST
  CC      /home/mikkel/spca5xx-20060501/spca5xx.mod.o
  LD [M]  /home/mikkel/spca5xx-20060501/spca5xx.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-23-386'
mikkel@mikkel-laptop:~/spca5xx-20060501$ sudo modprobe -r spca5xx
mikkel@mikkel-laptop:~/spca5xx-20060501$ sudo rm -rf /lib/modules/2.6.15-23-386/kernel/drivers/usb/media/spca5xx*
mikkel@mikkel-laptop:~/spca5xx-20060501$ sudo make install
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca50x.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/et61x.ko
install -c -m 0644 spca5xx.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
/sbin/depmod -ae
mikkel@mikkel-laptop:~/spca5xx-20060501$ sudo modprobe spca5xx
FATAL: Error inserting spca5xx (/lib/modules/2.6.15-23-386/kernel/drivers/usb/media/spca5xx.ko): Invalid module format

Any good suggestions?

---

### Post by eqisow on 2007-01-24
Bump, exact same error

---

### Post by eqisow on 2007-01-24
Problem solved. the error was here:

```
sudo make CC=gcc-3.4
```

It should be gcc-4.0 or gcc-4.1 instead.

Now I have another problem, though. Kubuntu seems to recognize the device now, and the little orange light comes on. However, Kopete freezes when I try to access the webcam. Camerama also freezes whenever I open it. Any ideas?

Edit: My specific device is 0x0c45, 0x60c0, a Sangha Sn535

---

### Post by eqisow on 2007-01-24
Just tried compiling and installing the newer gspcav1-20070110.tar.gz package from mxhaard.free.fr with the same results.

---

### Post by eqisow on 2007-01-27
Just an update, I tried the same thing on a Kubuntu Feisty computer and got the same result.

---

