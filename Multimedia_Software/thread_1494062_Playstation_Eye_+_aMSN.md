---
title: "Playstation Eye + aMSN"
date: 2010-05-26
forum: Multimedia Software
---

### Post by Ferrat on 2010-05-26
Well I got an Playstation Eye and wanna use it as a webcam, works great out of the box with both Skype and Cheese, however Camorama can't handle it (is that because of V4L2? 
and also aMSN is having troubles, aMSN almost looks like it can't handle the size of the output (640x480) which seems weird, is there anyway I can limit it to 320x240 (which the Eye also can do)? 

Meaning I get a picture but it jumps around, splits in two etc. 

Also if anyone has a Playstation Eye working with aMSN please let me know :)

---

### Post by Ferrat on 2010-05-26
okej, some progress, seems that there is a alternative version of gspca_ov534 just for the PS3 Eye, however I can't get it to work with Ubuntu 9.10 or 10.4 and the stock version doesn't recognice the option videomode for the module.

Anyone got any ideas? =)


Linux to info about driver / installing etc.
[http://blog.10100111001.com/2009/02/playstation-3-eye-web-cam-working-on.html](http://blog.10100111001.com/2009/02/playstation-3-eye-web-cam-working-on.html)


EDIT;
OUTPUT when trying to build it.
```
icebreaker@iceblock:~/gspca-ps3eyeMT$ make
make -C /home/icebreaker/gspca-ps3eyeMT/v4l 
make[1]: Entering directory `/home/icebreaker/gspca-ps3eyeMT/v4l'
perl scripts/make_config_compat.pl /lib/modules/2.6.31-21-generic/build ./.myconfig ./config-compat.h
creating symbolic links...
Kernel build directory is /lib/modules/2.6.31-21-generic/build
make -C /lib/modules/2.6.31-21-generic/build SUBDIRS=/home/icebreaker/gspca-ps3eyeMT/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-21-generic'
  CC [M]  /home/icebreaker/gspca-ps3eyeMT/v4l/tuner-xc2028.o
/home/icebreaker/gspca-ps3eyeMT/v4l/tuner-xc2028.c:55: error: 'FIRMWARE_NAME_MAX' undeclared here (not in a function)
make[3]: *** [/home/icebreaker/gspca-ps3eyeMT/v4l/tuner-xc2028.o] Error 1
make[2]: *** [_module_/home/icebreaker/gspca-ps3eyeMT/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-21-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/icebreaker/gspca-ps3eyeMT/v4l'
make: *** [all] Error 2

```

---

### Post by Ferrat on 2010-05-26
found this and got it working :) 

[http://bear24rw.blogspot.com/2009/11/ps3-eye-driver-patch.html](http://bear24rw.blogspot.com/2009/11/ps3-eye-driver-patch.html)

---

