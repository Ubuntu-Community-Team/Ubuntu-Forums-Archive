---
title: "Uninstalled ndiswrapper, now i cant install it!"
date: 2009-11-17
forum: Networking &amp; Wireless
---

### Post by Jezzick on 2009-11-17
Hi, total linux newb here. was fiddling around with ndiswrapper to try and get my DWA-142 USB wireless device working, and i uninstalled ndiswrapper to try and reinstall from source. now i cant install it! when i try to do 
```
sudo make
```
it give me this
```
make -C driver
make[1]: Entering directory `/home/jezzick/Desktop/ndiswrapper-1.55/driver'
make -C /usr/src/linux-headers-2.6.31-14-generic M=/home/jezzick/Desktop/ndiswrapper-1.55/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  LD      /home/jezzick/Desktop/ndiswrapper-1.55/driver/built-in.o
  MKEXPORT /home/jezzick/Desktop/ndiswrapper-1.55/driver/crt_exports.h
  MKEXPORT /home/jezzick/Desktop/ndiswrapper-1.55/driver/hal_exports.h
  MKEXPORT /home/jezzick/Desktop/ndiswrapper-1.55/driver/ndis_exports.h
  MKEXPORT /home/jezzick/Desktop/ndiswrapper-1.55/driver/ntoskernel_exports.h
  MKEXPORT /home/jezzick/Desktop/ndiswrapper-1.55/driver/ntoskernel_io_exports.h
  MKEXPORT /home/jezzick/Desktop/ndiswrapper-1.55/driver/rtl_exports.h
  MKEXPORT /home/jezzick/Desktop/ndiswrapper-1.55/driver/usb_exports.h
  CC [M]  /home/jezzick/Desktop/ndiswrapper-1.55/driver/crt.o
In file included from /home/jezzick/Desktop/ndiswrapper-1.55/driver/crt.c:16:
/home/jezzick/Desktop/ndiswrapper-1.55/driver/ntoskernel.h: In function ‘PushEntrySList’:
/home/jezzick/Desktop/ndiswrapper-1.55/driver/ntoskernel.h:905: error: implicit declaration of function ‘cmpxchg8b’
make[3]: *** [/home/jezzick/Desktop/ndiswrapper-1.55/driver/crt.o] Error 1
make[2]: *** [_module_/home/jezzick/Desktop/ndiswrapper-1.55/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/jezzick/Desktop/ndiswrapper-1.55/driver'
make: *** [all] Error 2
```
what can i do? when i tried to reinstall from synaptic, it didnt install. it said it couldnt find ndiswrapper.ko

---

### Post by phoenix97532004 on 2009-11-18
im having the same exact problem so any help would be great ive tried using ndisgtk and it didn't work right

---

### Post by gumshore on 2009-11-23
same here I reallly need this resolved

---

### Post by seoirse on 2009-11-23
Hi all,

You might try the solution described here:

[http://www.unixboard.de/vb3/showpost.php?p=342688&postcount=4](http://www.unixboard.de/vb3/showpost.php?p=342688&postcount=4)

The forum is German, but the patch should be understandable in any language;).

You can apply the patch as described there, or just change 878 
(saying ```
if LINUX_VERSION_CODE < KERNEL_VERSION(2,6,31)
```) in the file driver/ntoskernel.h to

```
if LINUX_VERSION_CODE < KERNEL_VERSION(2,6,32)
```
WARNING: This is a "Works-for-me" solution, so YMMV. It did, however, work for me;).

---

### Post by cariboo on 2009-11-23
Have you gone into the source directory and tried make uninstall?

---

### Post by SpaceFuzz on 2009-12-26
Thanks for the tip.  Modifying line 878 of the ntoskernel.h file to include kernel version 2.6.32 worked for me.

_BEFORE:_
*Line 878 of ndiswrapper-1.55/driver/ntoskernel.h:*
#if LINUX_VERSION_CODE < KERNEL_VERSION(2,6,31)

*Results of make:*
...
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-16-generic'
...
  CC [M]  /home/dan/ndiswrapper-1.55/driver/crt.o
In file included from /home/dan/ndiswrapper-1.55/driver/crt.c:16:
/home/dan/ndiswrapper-1.55/driver/ntoskernel.h: In function ‘PushEntrySList’:
/home/dan/ndiswrapper-1.55/driver/ntoskernel.h:905: error: implicit declaration of function ‘cmpxchg8b’
...

_AFTER_:
*Line 878 of ndiswrapper-1.55/driver/ntoskernel.h:*
#if LINUX_VERSION_CODE < KERNEL_VERSION(2,6,32)

*Results of make:*
...
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-16-generic'
  CC [M]  /home/dan/ndiswrapper-1.55/driver/crt.o
  CC [M]  /home/dan/ndiswrapper-1.55/driver/hal.o
...
*(success)*

Now...to get my wireless driver recognized...

<<< SpaceFuzz >>>

---

