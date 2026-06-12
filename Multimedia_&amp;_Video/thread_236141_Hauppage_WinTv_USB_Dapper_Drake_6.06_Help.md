---
title: "Hauppage WinTv USB Dapper Drake 6.06 Help"
date: 2006-08-14
forum: Multimedia &amp; Video
---

### Post by dcotruta on 2006-08-14
I'm a relative newcomer to the Linux scene, but this is the only thing that's really got me stumped.

I'm running 2.6.15-26-686 (for HT support). I want to try and get my WinTV USB card working, but I just can't seem to do it. I tried following the various tutorials for the Hoary release, but when I tried the first step (**make** in the driver folder) this happened:

```
root@catmando-desktop:/home/catmando/Desktop/usbvision-0.9.8.2/src# make
make -C /lib/modules/2.6.15-26-686/build SUBDIRS=/home/catmando/Desktop/usbvision-0.9.8.2/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-686'
  CC [M]  /home/catmando/Desktop/usbvision-0.9.8.2/src/i2c-algo-usb.o
/home/catmando/Desktop/usbvision-0.9.8.2/src/i2c-algo-usb.c:208: error: unknown field ‘name’ specified in initializer
/home/catmando/Desktop/usbvision-0.9.8.2/src/i2c-algo-usb.c:208: warning: initialization from incompatible pointer type
/home/catmando/Desktop/usbvision-0.9.8.2/src/i2c-algo-usb.c:209: error: unknown field ‘id’ specified in initializer
/home/catmando/Desktop/usbvision-0.9.8.2/src/i2c-algo-usb.c:209: error: ‘I2C_ALGO_BIT’ undeclared here (not in a function)
/home/catmando/Desktop/usbvision-0.9.8.2/src/i2c-algo-usb.c: In function ‘i2c_usb_add_bus’:
/home/catmando/Desktop/usbvision-0.9.8.2/src/i2c-algo-usb.c:226: error: ‘struct i2c_algorithm’ has no member named ‘id’
make[2]: *** [/home/catmando/Desktop/usbvision-0.9.8.2/src/i2c-algo-usb.o] Error 1
make[1]: *** [_module_/home/catmando/Desktop/usbvision-0.9.8.2/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-686'
make: *** [default] Error 2

```

This seemed like a **bad thing**, so I got the next driver (0.9.8.3) and tried that. *Make*, *make install* and *modprobe usbvision* all seemed to work fine, but I don't know where to go from here. 

Zapping crashes out with 
```
VBI initialization failed.
Cannot open '/dev/vbi0': 16, Device or resource busy.
```

XawTv gives me a pretty but useless blue screen with three question marks (???) for the title of the window. 

What I want to know is - has anyone solved this or is this even possible at this point in time.

If not, is there any way (or should I?) "uninstall the usbvision driver?

Thanks in advance for all the help.

---

