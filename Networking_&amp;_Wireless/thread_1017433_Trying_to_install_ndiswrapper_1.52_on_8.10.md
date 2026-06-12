---
title: "Trying to install ndiswrapper 1.52 on 8.10"
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by corn29 on 2008-12-21
Hello:

Sorry for yet another ndiswrapper question.  I've searched the Networking & Wireless forum for a while now and cannot find a similar problem.  I did find this thread: [http://ubuntuforums.org/showthread.php?t=998339](http://ubuntuforums.org/showthread.php?t=998339) but the link for the "fix" throws a 404 error.  arrrrggghhhh! 

I have a Belkin N Wireless ExpressCard Adapter.  A while ago, I had this working with 6.06 and ndiswrapper 1.47.

I just recently performed a clean install of 8.10.  The wireless lights on the adapter lit up after boot but I couldn't connect to my network so I assumed I needed to go down the ndiswrapper route again.

I downloaded the recommended file (from another computer), ndiswrapper_1.52.orig.tar.gz and unpacked it.

The problem I'm having is make doesn't appear to do anything.  Here's the output from the terminal:

dogzilla@dogzilla-laptop:/home/dogzilla/ndiswrapper-1.52$ make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
dogzilla@dogzilla-laptop:/home/dogzilla/ndiswrapper-1.52$ make
make -C driver
make[1]: Entering directory `/home/dogzilla/ndiswrapper-1.52/driver'
make -C /usr/src/linux-headers-2.6.27-7-generic SUBDIRS=/home/dogzilla/ndiswrapper-1.52/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /home/dogzilla/ndiswrapper-1.52/driver/iw_ndis.o
/home/dogzilla/ndiswrapper-1.52/driver/iw_ndis.c: In function ndis_translate_scan:
/home/dogzilla/ndiswrapper-1.52/driver/iw_ndis.c:1039: warning: passing argument 1 of iwe_stream_add_event from incompatible pointer type
/home/dogzilla/ndiswrapper-1.52/driver/iw_ndis.c:1039: warning: passing argument 3 of iwe_stream_add_event from incompatible pointer type
/home/dogzilla/ndiswrapper-1.52/driver/iw_ndis.c:1039: warning: passing argument 4 of iwe_stream_add_event makes pointer from integer without a cast
/home/dogzilla/ndiswrapper-1.52/driver/iw_ndis.c:1039: error: too few arguments to function iwe_stream_add_event
/home/dogzilla/ndiswrapper-1.52/driver/iw_ndis.c:1049: warning: passing argument 1 of iwe_stream_add_point from incompatible pointer type
/home/dogzilla/ndiswrapper-1.52/driver/iw_ndis.c:1049: warning: passing argument 3 of iwe_stream_add_point from incompatible pointer type
/home/dogzilla/ndiswrapper-1.52/driver/iw_ndis.c:1049: warning: passing argument 4 of iwe_stream_add_point from incompatible pointer type
/home/dogzilla/ndiswrapper-1.52/driver/iw_ndis.c:1049: error: too few arguments to function iwe_stream_add_point
/home/dogzilla/ndiswrapper-1.52/driver/iw_ndis.c:1055: warning: passing argument 1 of iwe_stream_add_event from incompatible pointer type
/home/dogzilla/ndiswrapper-1.52/driver/iw_ndis.c:1055: warning: passing argument 3 of iwe_stream_add_event from incompatible pointer type
/home/dogzilla/ndiswrapper-1.52/driver/iw_ndis.c:1055: warning: passing argument 4 of iwe_stream_add_event makes pointer from integer without a cast
/home/dogzilla/ndiswrapper-1.52/driver/iw_ndis.c:1055: error: too few arguments to function iwe_stream_add_event
/home/dogzilla/ndiswrapper-1.52/driver/iw_ndis.c:1066: warning: passing argument 1 of iwe_stream_add_event from incompatible pointer type
/home/dogzilla/ndiswrapper-1.52/driver/iw_ndis.c:1066: warning: passing argument 3 of iwe_stream_add_event from incompatible pointer type
/home/dogzilla/ndiswrapper-1.52/driver/iw_ndis.c:1066: warning: passing argument 4 of iwe_stream_add_event makes pointer from integer without a cast
/home/dogzilla/ndiswrapper-1.52/driver/iw_ndis.c:1066: error: too few arguments to function iwe_stream_add_event
/home/dogzilla/ndiswrapper-1.52/driver/iw_ndis.c:1081: warning: passing argument 1 of iwe_stream_add_event from incompatible pointer type
/home/dogzilla/ndiswrapper-1.52/driver/iw_ndis.c:1081: warning: passing argument 3 of iwe_stream_add_event from incompatible pointer type
/home/dogzilla/ndiswrapper-1.52/driver/iw_ndis.c:1081: warning: passing argument 4 of iwe_stream_add_event makes pointer from integer without a cast
/home/dogzilla/ndiswrapper-1.52/driver/iw_ndis.c:1081: error: too few arguments to function iwe_stream_add_event
/home/dogzilla/ndiswrapper-1.52/driver/iw_ndis.c:1095: warning: passing argument 1 of iwe_stream_add_event from incompatible pointer type
/home/dogzilla/ndiswrapper-1.52/driver/iw_ndis.c:1095: warning: passing argument 3 of iwe_stream_add_event from incompatible pointer type
/home/dogzilla/ndiswrapper-1.52/driver/iw_ndis.c:1095: warning: passing argument 4 of iwe_stream_add_event makes pointer from integer without a cast
/home/dogzilla/ndiswrapper-1.52/driver/iw_ndis.c:1095: error: too few arguments to function iwe_stream_add_event
/home/dogzilla/ndiswrapper-1.52/driver/iw_ndis.c:1106: warning: passing argument 1 of iwe_stream_add_point from incompatible pointer type
/home/dogzilla/ndiswrapper-1.52/driver/iw_ndis.c:1106: warning: passing argument 3 of iwe_stream_add_point from incompatible pointer type
/home/dogzilla/ndiswrapper-1.52/driver/iw_ndis.c:1106: warning: passing argument 4 of iwe_stream_add_point from incompatible pointer type
/home/dogzilla/ndiswrapper-1.52/driver/iw_ndis.c:1106: error: too few arguments to function iwe_stream_add_point
/home/dogzilla/ndiswrapper-1.52/driver/iw_ndis.c:1122: warning: passing argument 1 of iwe_stream_add_value from incompatible pointer type
/home/dogzilla/ndiswrapper-1.52/driver/iw_ndis.c:1122: warning: passing argument 4 of iwe_stream_add_value from incompatible pointer type
/home/dogzilla/ndiswrapper-1.52/driver/iw_ndis.c:1122: warning: passing argument 5 of iwe_stream_add_value makes pointer from integer without a cast
/home/dogzilla/ndiswrapper-1.52/driver/iw_ndis.c:1122: error: too few arguments to function iwe_stream_add_value
/home/dogzilla/ndiswrapper-1.52/driver/iw_ndis.c:1133: warning: passing argument 1 of iwe_stream_add_point from incompatible pointer type
/home/dogzilla/ndiswrapper-1.52/driver/iw_ndis.c:1133: warning: passing argument 3 of iwe_stream_add_point from incompatible pointer type
/home/dogzilla/ndiswrapper-1.52/driver/iw_ndis.c:1133: warning: passing argument 4 of iwe_stream_add_point from incompatible pointer type
/home/dogzilla/ndiswrapper-1.52/driver/iw_ndis.c:1133: error: too few arguments to function iwe_stream_add_point
/home/dogzilla/ndiswrapper-1.52/driver/iw_ndis.c:1139: warning: passing argument 1 of iwe_stream_add_point from incompatible pointer type
/home/dogzilla/ndiswrapper-1.52/driver/iw_ndis.c:1139: warning: passing argument 3 of iwe_stream_add_point from incompatible pointer type
/home/dogzilla/ndiswrapper-1.52/driver/iw_ndis.c:1139: warning: passing argument 4 of iwe_stream_add_point from incompatible pointer type
/home/dogzilla/ndiswrapper-1.52/driver/iw_ndis.c:1139: error: too few arguments to function iwe_stream_add_point
/home/dogzilla/ndiswrapper-1.52/driver/iw_ndis.c:1162: warning: passing argument 1 of iwe_stream_add_point from incompatible pointer type
/home/dogzilla/ndiswrapper-1.52/driver/iw_ndis.c:1162: warning: passing argument 3 of iwe_stream_add_point from incompatible pointer type
/home/dogzilla/ndiswrapper-1.52/driver/iw_ndis.c:1162: warning: passing argument 4 of iwe_stream_add_point from incompatible pointer type
/home/dogzilla/ndiswrapper-1.52/driver/iw_ndis.c:1162: error: too few arguments to function iwe_stream_add_point
make[3]: *** [/home/dogzilla/ndiswrapper-1.52/driver/iw_ndis.o] Error 1
make[2]: *** [_module_/home/dogzilla/ndiswrapper-1.52/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/dogzilla/ndiswrapper-1.52/driver'
make: *** [all] Error 2
dogzilla@dogzilla-laptop:/home/dogzilla/ndiswrapper-1.52$ 

Suggestions are greatly appreciated.  Thanks!

---

