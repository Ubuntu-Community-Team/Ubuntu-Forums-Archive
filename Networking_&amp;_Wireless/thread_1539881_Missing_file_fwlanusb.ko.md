---
title: "Missing file? fwlanusb.ko"
date: 2010-07-27
forum: Networking &amp; Wireless
---

### Post by mojo risin on 2010-07-27
Hi , I am using the latest Wubi lynx version and I have trouble to install my Fritz wlan usb stick.

I did download the AVM driver for linux and did what was in the read me file but if I want to install it tells me that it can't find this file ( fwlanusb.ko) and there fore it is closing the process. Is that the fault of the AVM site not including he file or is there a different error(like no compatibility to lynx?) Or is the error of a totally different nature?

```
make: Entering directory `/home/bianca/Downloads/fritz/src'
rm -f main.o driver.o tools.o lib.o buffers.o wext.o 
rm -f fwlanusb.o fwlanusb.ko 
make: Leaving directory `/home/bianca/Downloads/fritz/src'
make: Entering directory `/home/bianca/Downloads/fritz/src'
make -C /lib/modules/2.6.32-23-generic/build SUBDIRS=/home/bianca/Downloads/fritz/src modules 
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-23-generic'
  CC [M]  /home/bianca/Downloads/fritz/src/main.o
In file included from /home/bianca/Downloads/fritz/src/tools.h:30,
                 from /home/bianca/Downloads/fritz/src/main.c:31:
/home/bianca/Downloads/fritz/src/defs.h:63: error: redefinition of typedef ‘uintptr_t’
include/linux/types.h:41: note: previous declaration of ‘uintptr_t’ was here
make[2]: *** [/home/bianca/Downloads/fritz/src/main.o] Error 1
make[1]: *** [_module_/home/bianca/Downloads/fritz/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-23-generic'
make: *** [fwlanusb.o] Error 2
make: Leaving directory `/home/bianca/Downloads/fritz/src'
make: Entering directory `/home/bianca/Downloads/fritz/src'
cp: cannot stat `fwlanusb.ko': No such file or directory
make: *** [install] Error 1
make: Leaving directory `/home/bianca/Downloads/fritz/src'
bianca@ubuntu:~/Downloads/fritz$ 


```

---

### Post by wojox on 2010-07-27
```

make: Entering directory `/home/bianca/Downloads/fritz/src'
rm -f main.o driver.o tools.o lib.o buffers.o wext.o 
rm -f [COLOR="Red"]fwlanusb.o fwlanusb.ko [/COLOR]
make: Leaving directory `/home/bianca/Downloads/fritz/src'
make: Entering directory `/home/bianca/Downloads/fritz/src'
make -C /lib/modules/2.6.32-23-generic/build SUBDIRS=/home/bianca/Downloads/fritz/src modules 
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-23-generic'
  CC [M]  /home/bianca/Downloads/fritz/src/main.o
In file included from /home/bianca/Downloads/fritz/src/tools.h:30,
                 from /home/bianca/Downloads/fritz/src/main.c:31:
/home/bianca/Downloads/fritz/src/defs.h:63: error: redefinition of typedef ‘uintptr_t’
include/linux/types.h:41: note: previous declaration of ‘uintptr_t’ was here
make[2]: *** [/home/bianca/Downloads/fritz/src/main.o] Error 1
make[1]: *** [_module_/home/bianca/Downloads/fritz/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-23-generic'
make: *** [fwlanusb.o] Error 2
make: Leaving directory `/home/bianca/Downloads/fritz/src'
make: Entering directory `/home/bianca/Downloads/fritz/src'
cp: cannot stat `fwlanusb.ko': No such file or directory
make: *** [install] Error 1
make: Leaving directory `/home/bianca/Downloads/fritz/src'
bianca@ubuntu:~/Downloads/fritz$

```

It's right there in red. you removed it.

---

### Post by mojo risin on 2010-07-27
well I did not remove it, it is the install that removed it then. but why would it remove something it needs?

---

### Post by iponeverything on 2010-07-27
> **wojox said:**
> ```

make: Entering directory `/home/bianca/Downloads/fritz/src'
rm -f main.o driver.o tools.o lib.o buffers.o wext.o 
rm -f [COLOR="Red"]fwlanusb.o fwlanusb.ko [/COLOR]
make: Leaving directory `/home/bianca/Downloads/fritz/src'
make: Entering directory `/home/bianca/Downloads/fritz/src'
make -C /lib/modules/2.6.32-23-generic/build SUBDIRS=/home/bianca/Downloads/fritz/src modules 
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-23-generic'
  CC [M]  /home/bianca/Downloads/fritz/src/main.o
In file included from /home/bianca/Downloads/fritz/src/tools.h:30,
                 from /home/bianca/Downloads/fritz/src/main.c:31:
/home/bianca/Downloads/fritz/src/defs.h:63: error: redefinition of typedef &#8216;uintptr_t&#8217;
include/linux/types.h:41: note: previous declaration of &#8216;uintptr_t&#8217; was here
make[2]: *** [/home/bianca/Downloads/fritz/src/main.o] Error 1
make[1]: *** [_module_/home/bianca/Downloads/fritz/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-23-generic'
make: *** [fwlanusb.o] Error 2
make: Leaving directory `/home/bianca/Downloads/fritz/src'
make: Entering directory `/home/bianca/Downloads/fritz/src'
cp: cannot stat `fwlanusb.ko': No such file or directory
make: *** [install] Error 1
make: Leaving directory `/home/bianca/Downloads/fritz/src'
bianca@ubuntu:~/Downloads/fritz$

```

It's right there in red. you removed it.

He didn't remove it, that is just the "make clean".  If he never had a successful build, it was never there remove. 

You are trying to build it on 2.6.32-23 that driver is for 2.6.18.2-34. 

From the Readme for fwlanusb driver:

[B]Operating system: Linux - Kernel 2.6.18.2-34-default; SUSE 10.2 and other 
[/B]

The Atheros Linux wireless drivers should work:

[http://linuxwireless.org/en/users/Drivers/ar9170](http://linuxwireless.org/en/users/Drivers/ar9170)

---

### Post by mojo risin on 2010-07-27
Thanks for the links and info :), will try that later :)

---

### Post by mojo risin on 2010-07-28
I must have downloaded the wrong kind of driver...i installed bluetooth. (and I don't even have a bluetooth device.. well next try..)

---

### Post by mojo risin on 2010-07-28
hm at the end of the terminal session it said the drivers are loaded. How do I know get it working?

---

