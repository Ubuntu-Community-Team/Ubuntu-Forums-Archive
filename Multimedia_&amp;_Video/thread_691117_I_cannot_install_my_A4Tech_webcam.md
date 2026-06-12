---
title: "I cannot install my A4Tech webcam"
date: 2008-02-08
forum: Multimedia &amp; Video
---

### Post by DaDiablo on 2008-02-08
Hello.
I am using Ubuntu Gutsy and webcam A4Tech PK-935 and I cannot install it.
I've read a few topics, tired with Ekiga and there is working, but when i tried in Skype .. there is a green screen.
```
dadiablo@hell:~# lsusb
Bus 008 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 WebCam

```
I've tried with spca5xx drivers too, but I get error when try to compile it.
```
root@hell:/usr/src/modules/spca5xx# make clean
rm -r -f drivers/usb/*.o drivers/usb/.spcadecoder.o.cmd \
        drivers/usb/.spca5xx.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i
root@hell:/usr/src/modules/spca5xx# make
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/src/modules/spca5xx CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /usr/src/modules/spca5xx/drivers/usb/spca5xx.o
/usr/src/modules/spca5xx/drivers/usb/spca5xx.c:39:26: error: linux/config.h: No such file or directory
/usr/src/modules/spca5xx/drivers/usb/spca5xx.c: In function ‘spca50x_init_isoc’:
/usr/src/modules/spca5xx/drivers/usb/spca5xx.c:1681: warning: assignment from incompatible pointer type
make[2]: *** [/usr/src/modules/spca5xx/drivers/usb/spca5xx.o] Error 1
make[1]: *** [_module_/usr/src/modules/spca5xx] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [default] Error 2

```

---

### Post by linuxwizard on 2008-02-08
If the webcam is working in Ekiga your system has detected your webcam and using the driver you need. The spca5xx driver is included in the Ubuntu kernel you do not need to install it. I don't see your cam listed here > [https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams) > I do see another model of > Z-Star Microelectronics Corp which does not. This list may not be a complete list. I don't use Skype, but have you tried working with the setting within Skype ? I would say this is a Skype issue not a Ubuntu issue. You may not get it working.

---

### Post by DaDiablo on 2008-02-09
> **linuxwizard said:**
> If the webcam is working in Ekiga your system has detected your webcam and using the driver you need. The spca5xx driver is included in the Ubuntu kernel you do not need to install it. I don't see your cam listed here > [https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams) > I do see another model of > Z-Star Microelectronics Corp which does not. This list may not be a complete list. I don't use Skype, but have you tried working with the setting within Skype ? I would say this is a Skype issue not a Ubuntu issue. You may not get it working.

There isn't any setting within Skype. When I go to Video Device my webcam is the device which is chosen, but when I press Test, it appears green screen.

---

