---
title: "ndiswrapper error at installation"
date: 2009-02-22
forum: Networking &amp; Wireless
---

### Post by Meados on 2009-02-22
I get this error when I try to install ndiswrapper in my machine with ubuntu:

> home@home-laptop:~/ndiswrapper-1.51$ sudo make install
make -C driver install
make[1]: Entering directory `/home/home/ndiswrapper-1.51/driver'
make -C /usr/src/linux-headers-2.6.27-11-generic SUBDIRS=/home/home/ndiswrapper-1.51/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /home/home/ndiswrapper-1.51/driver/iw_ndis.o
/home/home/ndiswrapper-1.51/driver/iw_ndis.c: In function â€˜ndis_translate_scanâ€™:
/home/home/ndiswrapper-1.51/driver/iw_ndis.c:1039: warning: passing argument 1 of â€˜iwe_stream_add_eventâ€™ from incompatible pointer type
/home/home/ndiswrapper-1.51/driver/iw_ndis.c:1039: warning: passing argument 3 of â€˜iwe_stream_add_eventâ€™ from incompatible pointer type
/home/home/ndiswrapper-1.51/driver/iw_ndis.c:1039: warning: passing argument 4 of â€˜iwe_stream_add_eventâ€™ makes pointer from integer without a cast
/home/home/ndiswrapper-1.51/driver/iw_ndis.c:1039: error: too few arguments to function â€˜iwe_stream_add_eventâ€™
/home/home/ndiswrapper-1.51/driver/iw_ndis.c:1049: warning: passing argument 1 of â€˜iwe_stream_add_pointâ€™ from incompatible pointer type
/home/home/ndiswrapper-1.51/driver/iw_ndis.c:1049: warning: passing argument 3 of â€˜iwe_stream_add_pointâ€™ from incompatible pointer type
/home/home/ndiswrapper-1.51/driver/iw_ndis.c:1049: warning: passing argument 4 of â€˜iwe_stream_add_pointâ€™ from incompatible pointer type
/home/home/ndiswrapper-1.51/driver/iw_ndis.c:1049: error: too few arguments to function â€˜iwe_stream_add_pointâ€™
/home/home/ndiswrapper-1.51/driver/iw_ndis.c:1055: warning: passing argument 1 of â€˜iwe_stream_add_eventâ€™ from incompatible pointer type
/home/home/ndiswrapper-1.51/driver/iw_ndis.c:1055: warning: passing argument 3 of â€˜iwe_stream_add_eventâ€™ from incompatible pointer type
/home/home/ndiswrapper-1.51/driver/iw_ndis.c:1055: warning: passing argument 4 of â€˜iwe_stream_add_eventâ€™ makes pointer from integer without a cast
/home/home/ndiswrapper-1.51/driver/iw_ndis.c:1055: error: too few arguments to function â€˜iwe_stream_add_eventâ€™
/home/home/ndiswrapper-1.51/driver/iw_ndis.c:1066: warning: passing argument 1 of â€˜iwe_stream_add_eventâ€™ from incompatible pointer type
/home/home/ndiswrapper-1.51/driver/iw_ndis.c:1066: warning: passing argument 3 of â€˜iwe_stream_add_eventâ€™ from incompatible pointer type
/home/home/ndiswrapper-1.51/driver/iw_ndis.c:1066: warning: passing argument 4 of â€˜iwe_stream_add_eventâ€™ makes pointer from integer without a cast
/home/home/ndiswrapper-1.51/driver/iw_ndis.c:1066: error: too few arguments to function â€˜iwe_stream_add_eventâ€™
/home/home/ndiswrapper-1.51/driver/iw_ndis.c:1081: warning: passing argument 1 of â€˜iwe_stream_add_eventâ€™ from incompatible pointer type
/home/home/ndiswrapper-1.51/driver/iw_ndis.c:1081: warning: passing argument 3 of â€˜iwe_stream_add_eventâ€™ from incompatible pointer type
/home/home/ndiswrapper-1.51/driver/iw_ndis.c:1081: warning: passing argument 4 of â€˜iwe_stream_add_eventâ€™ makes pointer from integer without a cast
/home/home/ndiswrapper-1.51/driver/iw_ndis.c:1081: error: too few arguments to function â€˜iwe_stream_add_eventâ€™
/home/home/ndiswrapper-1.51/driver/iw_ndis.c:1095: warning: passing argument 1 of â€˜iwe_stream_add_eventâ€™ from incompatible pointer type
/home/home/ndiswrapper-1.51/driver/iw_ndis.c:1095: warning: passing argument 3 of â€˜iwe_stream_add_eventâ€™ from incompatible pointer type
/home/home/ndiswrapper-1.51/driver/iw_ndis.c:1095: warning: passing argument 4 of â€˜iwe_stream_add_eventâ€™ makes pointer from integer without a cast
/home/home/ndiswrapper-1.51/driver/iw_ndis.c:1095: error: too few arguments to function â€˜iwe_stream_add_eventâ€™
/home/home/ndiswrapper-1.51/driver/iw_ndis.c:1106: warning: passing argument 1 of â€˜iwe_stream_add_pointâ€™ from incompatible pointer type
/home/home/ndiswrapper-1.51/driver/iw_ndis.c:1106: warning: passing argument 3 of â€˜iwe_stream_add_pointâ€™ from incompatible pointer type
/home/home/ndiswrapper-1.51/driver/iw_ndis.c:1106: warning: passing argument 4 of â€˜iwe_stream_add_pointâ€™ from incompatible pointer type
/home/home/ndiswrapper-1.51/driver/iw_ndis.c:1106: error: too few arguments to function â€˜iwe_stream_add_pointâ€™
/home/home/ndiswrapper-1.51/driver/iw_ndis.c:1122: warning: passing argument 1 of â€˜iwe_stream_add_valueâ€™ from incompatible pointer type
/home/home/ndiswrapper-1.51/driver/iw_ndis.c:1122: warning: passing argument 4 of â€˜iwe_stream_add_valueâ€™ from incompatible pointer type
/home/home/ndiswrapper-1.51/driver/iw_ndis.c:1122: warning: passing argument 5 of â€˜iwe_stream_add_valueâ€™ makes pointer from integer without a cast
/home/home/ndiswrapper-1.51/driver/iw_ndis.c:1122: error: too few arguments to function â€˜iwe_stream_add_valueâ€™
/home/home/ndiswrapper-1.51/driver/iw_ndis.c:1133: warning: passing argument 1 of â€˜iwe_stream_add_pointâ€™ from incompatible pointer type
/home/home/ndiswrapper-1.51/driver/iw_ndis.c:1133: warning: passing argument 3 of â€˜iwe_stream_add_pointâ€™ from incompatible pointer type
/home/home/ndiswrapper-1.51/driver/iw_ndis.c:1133: warning: passing argument 4 of â€˜iwe_stream_add_pointâ€™ from incompatible pointer type
/home/home/ndiswrapper-1.51/driver/iw_ndis.c:1133: error: too few arguments to function â€˜iwe_stream_add_pointâ€™
/home/home/ndiswrapper-1.51/driver/iw_ndis.c:1139: warning: passing argument 1 of â€˜iwe_stream_add_pointâ€™ from incompatible pointer type
/home/home/ndiswrapper-1.51/driver/iw_ndis.c:1139: warning: passing argument 3 of â€˜iwe_stream_add_pointâ€™ from incompatible pointer type
/home/home/ndiswrapper-1.51/driver/iw_ndis.c:1139: warning: passing argument 4 of â€˜iwe_stream_add_pointâ€™ from incompatible pointer type
/home/home/ndiswrapper-1.51/driver/iw_ndis.c:1139: error: too few arguments to function â€˜iwe_stream_add_pointâ€™
/home/home/ndiswrapper-1.51/driver/iw_ndis.c:1162: warning: passing argument 1 of â€˜iwe_stream_add_pointâ€™ from incompatible pointer type
/home/home/ndiswrapper-1.51/driver/iw_ndis.c:1162: warning: passing argument 3 of â€˜iwe_stream_add_pointâ€™ from incompatible pointer type
/home/home/ndiswrapper-1.51/driver/iw_ndis.c:1162: warning: passing argument 4 of â€˜iwe_stream_add_pointâ€™ from incompatible pointer type
/home/home/ndiswrapper-1.51/driver/iw_ndis.c:1162: error: too few arguments to function â€˜iwe_stream_add_pointâ€™
make[3]: *** [/home/home/ndiswrapper-1.51/driver/iw_ndis.o] Error 1
make[2]: *** [_module_/home/home/ndiswrapper-1.51/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/home/ndiswrapper-1.51/driver'
make: *** [install] Error 2



Sorry for some characters, I am posting this with windows and seems that wordpad don't recognize right some characters of the .txt file created in ubuntu.

Can someone tell me what I need to do to fix it?

Thanks.

---

### Post by Meados on 2009-02-22
Just to say that I fixed it with newest version and with help of synaptic package installer.

---

