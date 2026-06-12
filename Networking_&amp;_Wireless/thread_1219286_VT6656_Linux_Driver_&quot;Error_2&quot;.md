---
title: "VT6656 Linux Driver &quot;Error 2&quot;"
date: 2009-07-21
forum: Networking &amp; Wireless
---

### Post by gamgee911 on 2009-07-21
I am installing ubuntu on my new mobo (zotac 9300-itx).  Everything works great, except the VT6656 wifi card.  Following directions from [http://www.logicsupply.com/blog/2008/01/02/building-the-vt6656-linux-driver-for-ubuntu/](http://www.logicsupply.com/blog/2008/01/02/building-the-vt6656-linux-driver-for-ubuntu/)  I get as far as running "make" but I get the following in reply:

```

samuelgrund@cl0ud:~/vt6656/VT6656-Linux-x86-src-v113/driver$ make
make -C /lib/modules/2.6.28-13-generic/build SUBDIRS=/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-13-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-13-generic'
make: *** [default] Error 2

```

I've attempted running the patch to see if that fixes the problem, but no avail.  any input would be much appreciated, I'm not sure what error 2 means :)

---

### Post by chili555 on 2009-07-21
You might try running:```
KBUILD_NOPEDANTIC=1 make
```Please let us and the searchers know.

---

### Post by gamgee911 on 2009-07-21
here's what I got
```

samuelgrund@cl0ud:~/vt6656/VT6656-Linux-x86-src-v113/driver$ KBUILD_NOPEDANTIC=1 make
make -C /lib/modules/2.6.28-13-generic/build SUBDIRS=/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-13-generic'
  CC [M]  /home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.o
In file included from /home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:49:
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/device.h:93:24: error: device_cfg.h: No such file or directory
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:79:19: error: iocmd.h: No such file or directory
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:148: error: expected ‘,’ or ‘;’ before ‘DEVICE_FULL_DRV_NAM’
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:166: error: ‘MAX_UINTS’ undeclared here (not in a function)
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:166: error: ‘OPTION_DEFAULT’ undeclared here (not in a function)
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:166: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:166: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:166: error: size of array ‘type name’ is negative
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:172: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:172: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:172: error: size of array ‘type name’ is negative
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:179: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:179: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:179: error: size of array ‘type name’ is negative
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:189: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:189: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:189: error: size of array ‘type name’ is negative
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:196: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:196: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:196: error: size of array ‘type name’ is negative
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:203: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:203: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:203: error: size of array ‘type name’ is negative
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:226: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:226: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:226: error: size of array ‘type name’ is negative
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:232: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:232: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:232: error: size of array ‘type name’ is negative
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:248: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:248: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:248: error: size of array ‘type name’ is negative
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:256: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:256: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:256: error: size of array ‘type name’ is negative
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:263: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:263: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:263: error: size of array ‘type name’ is negative
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:275: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:275: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:275: error: size of array ‘type name’ is negative
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:286: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:286: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:286: error: size of array ‘type name’ is negative
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c: In function ‘vntwusb_found1’:
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:759: error: ‘DEVICE_FULL_DRV_NAM’ undeclared (first use in this function)
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:759: error: (Each undeclared identifier is reported only once
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:759: error: for each function it appears in.)
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:759: error: ‘DEVICE_VERSION’ undeclared (first use in this function)
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:764: error: expected ‘)’ before ‘DEVICE_NAME’
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:776: error: expected ‘)’ before ‘DEVICE_NAME’
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:784: error: implicit declaration of function ‘SET_MODULE_OWNER’
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:790: error: ‘struct __device_info’ has no member named ‘tx_80211’
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:813: error: expected ‘)’ before ‘DEVICE_NAME’
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c: In function ‘device_alloc_frag_buf’:
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:1032: error: implicit declaration of function ‘ASSERT’
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c: In function ‘device_open’:
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:1045: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘wpa_Result’
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:1045: error: ‘wpa_Result’ undeclared (first use in this function)
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c: In function ‘device_ioctl’:
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:1401: error: ‘PSCmdRequest’ undeclared (first use in this function)
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:1401: error: expected ‘;’ before ‘pReq’
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:1404: warning: ISO C90 forbids mixed declarations and code
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:1710: error: ‘IOCTL_CMD_TEST’ undeclared (first use in this function)
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:1718: error: ‘pReq’ undeclared (first use in this function)
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:1718: error: expected ‘;’ before ‘rq’
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:1719: error: ‘MAGIC_CODE’ undeclared (first use in this function)
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:1722: error: ‘IOCTL_CMD_SET’ undeclared (first use in this function)
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:1738: error: ‘IOCTL_CMD_HOSTAPD’ undeclared (first use in this function)
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:1754: error: ‘IOCTL_CMD_WPA’ undeclared (first use in this function)
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c: In function ‘ethtool_ioctl’:
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:1818: error: ‘DEVICE_NAME’ undeclared (first use in this function)
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:1819: error: ‘DEVICE_VERSION’ undeclared (first use in this function)
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c: At top level:
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:1843: error: ‘DEVICE_NAME’ undeclared here (not in a function)
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c: In function ‘vntwusb_init_module’:
/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.c:1862: error: expected ‘)’ before ‘DEVICE_FULL_DRV_NAM’
make[2]: *** [/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver/main_usb.o] Error 1
make[1]: *** [_module_/home/samuelgrund/vt6656/VT6656-Linux-x86-src-v113/driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-13-generic'
make: *** [default] Error 2

```

---

### Post by chili555 on 2009-07-21
I noticed this is a blog posted in January of 2008, which is ancient in Linux terms. I also noticed this:> Please note: A new version of this driver is available that does not require patching. This driver is also GPL-licensed, making it suitable for eventual inclusion in the kernel. These instructions are now obsolete.  Download the updated driver source from Via Arena.I suggest trying the newer version.

Also, please be sure the prerequesite, *build-essential*, is installed on your system.```
sudo apt-get install build-essential.
```It won't solve the problem in this case, I can't build it either; I think it's too old.

---

### Post by chili555 on 2009-07-21
This one built perfectly for me. I don't have the device, so I can't test it.

[http://www.viaarena.com/Driver/VT6656_Linux_src_v1.19_12_x86.zip](http://www.viaarena.com/Driver/VT6656_Linux_src_v1.19_12_x86.zip)

---

### Post by gamgee911 on 2009-07-21
I didn't notice the date, argg.  I did get it to compile and i have vntwusb.ko.  however if I run make install I get more errors.  if I run sudo insmod vntwusb.ko it completes, but my computer freezes after a few seconds.

---

### Post by chili555 on 2009-07-21
I assume you meant *sudo make install*. Please do so and post the errors here. If you can't get *sudo make install* to complete without error, there is no reason to proceed further, so I don't doubt *insmod* didn't work.

---

### Post by gamgee911 on 2009-07-22
here's what I get after running sudo make install
```

samuelgrund@cl0ud:~/Desktop/VT6656_Linux_src_v1.19_12_x86/driver$ sudo make install
[sudo] password for samuelgrund: 
make -C /lib/modules/2.6.28-13-generic/build SUBDIRS=/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-13-generic'
  CC [M]  /home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.o
In file included from /home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:50:
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/device.h:112:24: error: device_cfg.h: No such file or directory
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:80:19: error: iocmd.h: No such file or directory
In file included from /home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:95:
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/wpactl.h:39:19: error: iowpa.h: No such file or directory
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:151: error: expected ‘,’ or ‘;’ before ‘DEVICE_FULL_DRV_NAM’
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:169: error: ‘MAX_UINTS’ undeclared here (not in a function)
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:169: error: ‘OPTION_DEFAULT’ undeclared here (not in a function)
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:169: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:169: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:169: error: size of array ‘type name’ is negative
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:175: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:175: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:175: error: size of array ‘type name’ is negative
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:182: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:182: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:182: error: size of array ‘type name’ is negative
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:192: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:192: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:192: error: size of array ‘type name’ is negative
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:199: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:199: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:199: error: size of array ‘type name’ is negative
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:206: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:206: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:206: error: size of array ‘type name’ is negative
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:229: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:229: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:229: error: size of array ‘type name’ is negative
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:235: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:235: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:235: error: size of array ‘type name’ is negative
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:251: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:251: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:251: error: size of array ‘type name’ is negative
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:259: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:259: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:259: error: size of array ‘type name’ is negative
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:266: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:266: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:266: error: size of array ‘type name’ is negative
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:278: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:278: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:278: error: size of array ‘type name’ is negative
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:289: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:289: warning: type defaults to ‘int’ in declaration of ‘type name’
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:289: error: size of array ‘type name’ is negative
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c: In function ‘device_init_registers’:
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:574: error: ‘ZoneType_Japan’ undeclared (first use in this function)
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:574: error: (Each undeclared identifier is reported only once
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:574: error: for each function it appears in.)
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:575: error: ‘ZoneType_Europe’ undeclared (first use in this function)
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:576: error: ‘ZoneType_USA’ undeclared (first use in this function)
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c: In function ‘device_release_WPADEV’:
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:770: error: ‘viawget_wpa_header’ undeclared (first use in this function)
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:770: error: ‘wpahdr’ undeclared (first use in this function)
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:771: warning: ISO C90 forbids mixed declarations and code
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:775: error: expected expression before ‘)’ token
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:776: error: ‘VIAWGET_DEVICECLOSE_MSG’ undeclared (first use in this function)
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:783: warning: assignment makes integer from pointer without a cast
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c: In function ‘vntwusb_found1’:
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:861: error: ‘DEVICE_FULL_DRV_NAM’ undeclared (first use in this function)
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:861: error: ‘DEVICE_VERSION’ undeclared (first use in this function)
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:871: error: expected ‘)’ before ‘DEVICE_NAME’
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:883: error: expected ‘)’ before ‘DEVICE_NAME’
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:935: error: expected ‘)’ before ‘DEVICE_NAME’
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c: In function ‘device_alloc_frag_buf’:
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:1198: error: implicit declaration of function ‘ASSERT’
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c: In function ‘device_open’:
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:1211: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘wpa_Result’
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:1211: error: ‘wpa_Result’ undeclared (first use in this function)
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c: In function ‘Config_FileOperation’:
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:1654: error: ‘CONFIG_PATH’ undeclared (first use in this function)
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c: In function ‘Read_config_file’:
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:1732: error: ‘ZoneType_USA’ undeclared (first use in this function)
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:1735: error: ‘ZoneType_Japan’ undeclared (first use in this function)
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:1738: error: ‘ZoneType_Europe’ undeclared (first use in this function)
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c: In function ‘device_ioctl’:
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:1840: error: ‘PSCmdRequest’ undeclared (first use in this function)
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:1840: error: expected ‘;’ before ‘pReq’
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:1843: warning: ISO C90 forbids mixed declarations and code
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:2210: error: ‘IOCTL_CMD_TEST’ undeclared (first use in this function)
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:2218: error: ‘pReq’ undeclared (first use in this function)
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:2218: error: expected ‘;’ before ‘rq’
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:2222: error: ‘MAGIC_CODE’ undeclared (first use in this function)
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:2228: error: ‘IOCTL_CMD_SET’ undeclared (first use in this function)
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:2230: error: expected ‘)’ before ‘rq’
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:2230: error: ‘WLAN_CMD_SET_WPA’ undeclared (first use in this function)
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:2245: error: ‘IOCTL_CMD_HOSTAPD’ undeclared (first use in this function)
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:2261: error: ‘IOCTL_CMD_WPA’ undeclared (first use in this function)
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c: In function ‘ethtool_ioctl’:
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:2336: error: ‘DEVICE_NAME’ undeclared (first use in this function)
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:2337: error: ‘DEVICE_VERSION’ undeclared (first use in this function)
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c: At top level:
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:2361: error: ‘DEVICE_NAME’ undeclared here (not in a function)
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c: In function ‘vntwusb_init_module’:
/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:2387: error: expected ‘)’ before ‘DEVICE_FULL_DRV_NAM’
make[2]: *** [/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.o] Error 1
make[1]: *** [_module_/home/samuelgrund/Desktop/VT6656_Linux_src_v1.19_12_x86/driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-13-generic'
make: *** [default] Error 2

```

thanks

---

### Post by gamgee911 on 2009-07-22
should also be mentioned this is 64 bit ubuntu, not 32

---

### Post by chili555 on 2009-07-22
> /Desktop/VT6656_Linux_src_v1.19_12_x86/driverI notice you are in the 'driver' directory. Why? I realize the installation instructions are vague to useless, however I suggest you do:```
cd ..
```This will bring you up one level. Then do:```
make clean
make
sudo make install
sudo modprobe vntwusb
```It worked perfectly for me, however, I don't have the device, so I can't test it.

---

### Post by gamgee911 on 2009-07-22
aha, now it compiles properly.  however after loading the driver gdm freezes.  apparently its a problem with the driver ?

for the record:
```

samuelgrund@cl0ud:~/VT6656_Linux_src_v1.19_12_x86$ make
set -e; for d in driver; do make -C $d ; done
make[1]: Entering directory `/home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver'
make -C /lib/modules/2.6.28-13-generic/build SUBDIRS=/home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.28-13-generic'
  CC [M]  /home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.o
/home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c: In function ‘device_release_WPADEV’:
/home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/main_usb.c:783: warning: assignment makes integer from pointer without a cast
  CC [M]  /home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/card.o
  CC [M]  /home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/mac.o
  CC [M]  /home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/baseband.o
  CC [M]  /home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/wctl.o
  CC [M]  /home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/80211mgr.o
  CC [M]  /home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/wcmd.o
  CC [M]  /home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/wmgr.o
/home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/wmgr.c: In function ‘s_vMgrRxAssocResponse’:
/home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/wmgr.c:1058: warning: assignment makes integer from pointer without a cast
/home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/wmgr.c: In function ‘s_vMgrRxDisassociation’:
/home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/wmgr.c:1702: warning: assignment makes integer from pointer without a cast
/home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/wmgr.c: In function ‘s_vMgrRxDeauthentication’:
/home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/wmgr.c:1810: warning: assignment makes integer from pointer without a cast
  CC [M]  /home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/bssdb.o
/home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/bssdb.c: In function ‘BSSvSecondCallBack’:
/home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/bssdb.c:1305: warning: assignment makes integer from pointer without a cast
/home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/bssdb.c:1349: warning: assignment makes integer from pointer without a cast
  CC [M]  /home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/rxtx.o
  CC [M]  /home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/dpc.o
/home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/dpc.c: In function ‘RXbBulkInProcessData’:
/home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/dpc.c:679: warning: assignment makes integer from pointer without a cast
/home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/dpc.c:841: warning: assignment makes integer from pointer without a cast
/home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/dpc.c:966: warning: assignment makes integer from pointer without a cast
  CC [M]  /home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/power.o
  CC [M]  /home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/datarate.o
  CC [M]  /home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/mib.o
  CC [M]  /home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/rc4.o
  CC [M]  /home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/tether.o
  CC [M]  /home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/tcrc.o
  CC [M]  /home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/ioctl.o
  CC [M]  /home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/hostap.o
  CC [M]  /home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/wpa.o
/home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/wpa.c: In function ‘WPA_ParseRSN’:
/home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/wpa.c:173: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
/home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/wpa.c:204: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
  CC [M]  /home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/key.o
  CC [M]  /home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/tkip.o
  CC [M]  /home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/michael.o
  CC [M]  /home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/rf.o
  CC [M]  /home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/iwctl.o
  CC [M]  /home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/wpactl.o
  CC [M]  /home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/wpa2.o
  CC [M]  /home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/aes_ccmp.o
  CC [M]  /home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/usbpipe.o
  CC [M]  /home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/channel.o
  CC [M]  /home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/control.o
  CC [M]  /home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/firmware.o
/home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/firmware.c: In function ‘FIRMWAREbDownload’:
/home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/firmware.c:815: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
  CC [M]  /home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/int.o
  LD [M]  /home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/vntwusb.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/vntwusb.mod.o
  LD [M]  /home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver/vntwusb.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.28-13-generic'
make[1]: Leaving directory `/home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver'
samuelgrund@cl0ud:~/VT6656_Linux_src_v1.19_12_x86$ sudo make install
set -e; for d in driver; do make -C $d install ; done
make[1]: Entering directory `/home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver'
make -C /lib/modules/2.6.28-13-generic/build SUBDIRS=/home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.28-13-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.28-13-generic'
mkdir -p /lib/modules/2.6.28-13-generic/kernel/drivers/net
install -m 644 -o root vntwusb.ko /lib/modules/2.6.28-13-generic/kernel/drivers/net
/sbin/depmod -a || true
make[1]: Leaving directory `/home/samuelgrund/VT6656_Linux_src_v1.19_12_x86/driver'
samuelgrund@cl0ud:~/VT6656_Linux_src_v1.19_12_x86$ 

```

---

### Post by chili555 on 2009-07-22
> after loading the driver gdm freezes. apparently its a problem with the driver ?Very hard to tell. It could be that it's a 32-bit driver and you are using it on a 64-bit system, or other unrelated issues. Let's have a look at the kernel messages:```
sudo cat /var/log/messages | grep vntwusb
```You can skip any repeats if there are any.

---

### Post by gamgee911 on 2009-07-23
no logs appear

---

### Post by chili555 on 2009-07-23
After googling quite a bit, I am convinced or at least very suspicious that this is a 64-bit issue. I have no more ideas.

---

### Post by gamgee911 on 2009-07-23
I really appreciate the help though dude, I'm kind of having some success with ndiswrapper so I'm going to persue that as a possible method

---

### Post by chili555 on 2009-07-23
It will be helpful to the searchers and noobs if you post a few notes if you get it going with ndiswrapper. Thanks!

---

### Post by titopagan on 2009-09-16
@gamgee911

Did you ever get it working with ndiwrapper?

---

