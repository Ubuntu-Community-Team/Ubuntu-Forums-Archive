---
title: "compiling driver for Hermes wireless card"
date: 2009-01-29
forum: Networking &amp; Wireless
---

### Post by trundlenut on 2009-01-29
I have been running Intrepid on an old toshiba satellite pro 6000 I was given which has a Toshiba minipci wireless card from Lucent (Hermes I), I managed to get it working using WPA encryption using the wlags driver that was helpfully posted [here]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/66696") but that only works with the 2.6.27-9 kernel.

I wasn't paying much attention yesterday and let the update manager upgrade the kernel to 2.6.27-11 and now the wireless doesn't work.  I have tried to compile the driver using the files and instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=304217&page=11") but I can't get it to compile I get a whole load of errors when I try "make" and I can't get as far as "make install".

Here are the errors I get (there was one previous to this but I just needed to comment out a line refering to a file which didn't actually exist)

```
make -C /lib/modules/2.6.27-11-generic/build M=/home/simon/wlags/wlags49-h1-cs modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /home/simon/wlags/wlags49-h1-cs/wl_wext.o
/home/simon/wlags/wlags49-h1-cs/wl_wext.c: In function ‘wl_giwscan’:
/home/simon/wlags/wlags49-h1-cs/wl_wext.c:1557: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/simon/wlags/wlags49-h1-cs/wl_wext.c:1557: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/simon/wlags/wlags49-h1-cs/wl_wext.c:1557: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/simon/wlags/wlags49-h1-cs/wl_wext.c:1557: error: too few arguments to function ‘iwe_stream_add_event’
/home/simon/wlags/wlags49-h1-cs/wl_wext.c:1568: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/simon/wlags/wlags49-h1-cs/wl_wext.c:1568: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/simon/wlags/wlags49-h1-cs/wl_wext.c:1568: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/simon/wlags/wlags49-h1-cs/wl_wext.c:1568: error: too few arguments to function ‘iwe_stream_add_event’
/home/simon/wlags/wlags49-h1-cs/wl_wext.c:1578: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/simon/wlags/wlags49-h1-cs/wl_wext.c:1578: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/simon/wlags/wlags49-h1-cs/wl_wext.c:1578: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/simon/wlags/wlags49-h1-cs/wl_wext.c:1578: error: too few arguments to function ‘iwe_stream_add_event’
/home/simon/wlags/wlags49-h1-cs/wl_wext.c:1586: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/simon/wlags/wlags49-h1-cs/wl_wext.c:1586: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/simon/wlags/wlags49-h1-cs/wl_wext.c:1586: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/simon/wlags/wlags49-h1-cs/wl_wext.c:1586: error: too few arguments to function ‘iwe_stream_add_point’
/home/simon/wlags/wlags49-h1-cs/wl_wext.c:1599: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/simon/wlags/wlags49-h1-cs/wl_wext.c:1599: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/simon/wlags/wlags49-h1-cs/wl_wext.c:1599: error: too few arguments to function ‘iwe_stream_add_point’
/home/simon/wlags/wlags49-h1-cs/wl_wext.c:1607: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/simon/wlags/wlags49-h1-cs/wl_wext.c:1607: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/simon/wlags/wlags49-h1-cs/wl_wext.c:1607: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/simon/wlags/wlags49-h1-cs/wl_wext.c:1607: error: too few arguments to function ‘iwe_stream_add_event’
/home/simon/wlags/wlags49-h1-cs/wl_wext.c:1617: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/simon/wlags/wlags49-h1-cs/wl_wext.c:1617: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/simon/wlags/wlags49-h1-cs/wl_wext.c:1617: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/simon/wlags/wlags49-h1-cs/wl_wext.c:1617: error: too few arguments to function ‘iwe_stream_add_point’
/home/simon/wlags/wlags49-h1-cs/wl_wext.c:1630: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/simon/wlags/wlags49-h1-cs/wl_wext.c:1630: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/simon/wlags/wlags49-h1-cs/wl_wext.c:1630: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/simon/wlags/wlags49-h1-cs/wl_wext.c:1630: error: too few arguments to function ‘iwe_stream_add_point’
make[2]: *** [/home/simon/wlags/wlags49-h1-cs/wl_wext.o] Error 1
make[1]: *** [_module_/home/simon/wlags/wlags49-h1-cs] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: *** [default] Error 2
```

This has now surpassed my rather limited knowledge.  Can anyone help or even better compile the driver into a deb package ;)

---

