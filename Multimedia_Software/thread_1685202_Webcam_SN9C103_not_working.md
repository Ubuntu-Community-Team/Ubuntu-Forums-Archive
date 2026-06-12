---
title: "Webcam SN9C103 not working"
date: 2011-02-10
forum: Multimedia Software
---

### Post by highmighty on 2011-02-10
Hi all,

My usb webcam (SN9C103 chipset) seems to be "detected" properly in latest Ubuntu 10.10 but it doesn't actually work at all :(

For example I don't see it as an option in IM applications.

Here's the output of lsusb:

```
lab@lab-linux:~$ lsusb
Bus 002 Device 002: ID 0c45:60af Microdia VideoCAM Look
```

I then installed a virtual machine of WinXP (w/ VMware player) inside of Ubuntu to make it work but whenever I "connect" this USB device to the virtual machine, Ubuntu hangs, which is worst :(

I suspect that it has to do with the fact that it's still not recognized properly in Ubuntu at first...

Please help. I guess I need to load a driver for this webcam to work but which one? And how would I do that? modprobing?

Thank you all for your time and support,

highmighty

---

### Post by highmighty on 2011-02-12
Any ideas anyone?

Thank you for your time and support,

highmighty

---

### Post by HeroKing on 2011-02-12
a good way to test that it's working properly is to download Cheese Webcam Booth from the Software Center. it should detect your webcam and work flawlessly if it's configured correctly. i've also just found a faq page on downloading a driver, but it may be experimental. you can follow the instructions [here.](http://groups.google.com/group/microdia/web/testing-microdia-driver-draft)

---

### Post by MODYSAMA on 2011-02-13
I have you problem with Facecam 312    have more than month aago searching and trying no new. laptop HP
But my cam is driverless.
I you find any solution I will try it on parallel.

---

### Post by highmighty on 2011-02-13
> **HeroKing said:**
> a good way to test that it's working properly is to download Cheese Webcam Booth from the Software Center. it should detect your webcam and work flawlessly if it's configured correctly. i've also just found a faq page on downloading a driver, but it may be experimental. you can follow the instructions [here.](http://groups.google.com/group/microdia/web/testing-microdia-driver-draft)

I tested it with Cheese and it didn't detected any webcam installed, I'll try soon with the above driver and we'll see if it helps... thanks a bunch!

highmighty

---

### Post by highmighty on 2011-02-16
Unfortunately, I was unable of installing the webcam driver follwing these steps ([http://ubuntuforums.org/showthread.php?p=4831129]("http://ubuntuforums.org/showthread.php?p=4831129")), the "build" didn't went fine and here's the output of the build command, could someone tell me what's missing?

```
lab@lab-linux:~/Downloads/gspcav1-20071224$ sudo ./gspca_build

 REMOVE the old module if present
ERROR: Module gspca does not exist in /proc/modules

 CLEAN gspca source tree
rm -r -f *.o decoder/.gspcadecoder.o.cmd decoder/*.o \
	.gspca.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i \
	*.symvers *.err

 COMPILE gspca Please Wait ....!!

 INSTALL gspca in the kernel binary tree
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/media/video/gspca.ko
install -c -m 0644 gspca.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
install: cannot stat `gspca.ko': No such file or directory
make: *** [install] Error 1

 LOAD gspca in memory 
FATAL: Module gspca not found.

 PRINT COMPILATION MESSAGES if ERRORS look kgspca.err 
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/lab/Downloads/gspcav1-20071224 CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-25-generic'
  CC [M]  /home/lab/Downloads/gspcav1-20071224/gspca_core.o
/home/lab/Downloads/gspcav1-20071224/gspca_core.c:54: fatal error: asm/semaphore.h: No such file or directory
compilation terminated.
make[2]: *** [/home/lab/Downloads/gspcav1-20071224/gspca_core.o] Error 1
make[1]: *** [_module_/home/lab/Downloads/gspcav1-20071224] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-25-generic'
make: *** [default] Error 2
lab@lab-linux:~/Downloads/gspcav1-20071224$ 

```

Thank you all for your time and support,

highmighty

---

### Post by no2498 on 2011-02-17
gspca should be in the kernel now days from 804 up
put this in a terminal dmesg click enter
should load a grabber for the cam

see if your cams listed here

[http://www.danielogawa.com/webcam.html](http://www.danielogawa.com/webcam.html)

---

