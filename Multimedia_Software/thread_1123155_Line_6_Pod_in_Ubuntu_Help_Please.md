---
title: "Line 6 Pod in Ubuntu Help Please"
date: 2009-04-11
forum: Multimedia Software
---

### Post by TennSeven on 2009-04-11
I am running Ubuntu Hardy and trying to install a driver for my Line 6 Pod XT as described here (Source Installation):

[http://www.tanzband-scream.at/line6/INSTALL](http://www.tanzband-scream.at/line6/INSTALL)

I am getting the following output, and I don't know what I should do to fix it (I am a little new to Linux).  I have tried the few "fixes" I found in the forums but nothing has helped.  Does anyone have any ideas?

```
./set_revision.sh
make -f Makefile -C /lib/modules/2.6.24-21-generic/build CONFIG_LINE6_USB=m SUBDIRS=/opt/line6usb-0.8.1 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-21-generic'
  CC [M]  /opt/line6usb-0.8.1/audio.o
In file included from /opt/line6usb-0.8.1/driver.h:21,
                 from /opt/line6usb-0.8.1/audio.c:12:
include/sound/core.h:281: error: ‘SNDRV_CARDS’ undeclared here (not in a function)
/opt/line6usb-0.8.1/audio.c:19: error: array index in initializer not of integer type
/opt/line6usb-0.8.1/audio.c:19: error: (near initialization for ‘line6_index’)
/opt/line6usb-0.8.1/audio.c:20: error: array index in initializer not of integer type
/opt/line6usb-0.8.1/audio.c:20: error: (near initialization for ‘line6_id’)
/opt/line6usb-0.8.1/audio.c: In function ‘line6_init_audio’:
/opt/line6usb-0.8.1/audio.c:41: error: implicit declaration of function ‘dev_name’
/opt/line6usb-0.8.1/audio.c:41: warning: format ‘%s’ expects type ‘char *’, but argument 4 has type ‘int’
make[2]: *** [/opt/line6usb-0.8.1/audio.o] Error 1
make[1]: *** [_module_/opt/line6usb-0.8.1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-21-generic'
make: *** [default] Error 2
```

---

### Post by jerry85 on 2010-12-29
I'm having exactly the same problem.  
how did you install the driver?

---

