---
title: "Problem with installing UVC driver for notebook webcam."
date: 2010-07-22
forum: Multimedia Software
---

### Post by XM500 on 2010-07-22
Webcam hardware ID is: 5986:0241 and it should be supported: [http://www.ideasonboard.org/uvc](http://www.ideasonboard.org/uvc)

When I try to compile the newest uvcvideo driver ([http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)), then I get these errors:

> user@user-laptop ~/uvcvideo $ sudo make
[sudo] password for user: 
make -C /home/user/uvcvideo/v4l 
make[1]: Entering directory `/home/user/uvcvideo/v4l'
creating symbolic links...
make -C firmware prep
make[2]: Entering directory `/home/user/uvcvideo/v4l/firmware'
make[2]: Leaving directory `/home/user/uvcvideo/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/user/uvcvideo/v4l/firmware'
make[2]: Nothing to be done for `default'.
make[2]: Leaving directory `/home/user/uvcvideo/v4l/firmware'
Kernel build directory is /lib/modules/2.6.32-21-generic/build
make -C /lib/modules/2.6.32-21-generic/build SUBDIRS=/home/user/uvcvideo/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  CC [M]  /home/user/uvcvideo/v4l/firedtv-1394.o
/home/user/uvcvideo/v4l/firedtv-1394.c:22:17: error: dma.h: No such file or directory
/home/user/uvcvideo/v4l/firedtv-1394.c:23:21: error: csr1212.h: No such file or directory
/home/user/uvcvideo/v4l/firedtv-1394.c:24:23: error: highlevel.h: No such file or directory
/home/user/uvcvideo/v4l/firedtv-1394.c:25:19: error: hosts.h: No such file or directory
/home/user/uvcvideo/v4l/firedtv-1394.c:26:22: error: ieee1394.h: No such file or directory
/home/user/uvcvideo/v4l/firedtv-1394.c:27:17: error: iso.h: No such file or directory
/home/user/uvcvideo/v4l/firedtv-1394.c:28:21: error: nodemgr.h: No such file or directory
/home/user/uvcvideo/v4l/firedtv-1394.c:41: warning: 'struct hpsb_iso' declared inside parameter list
/home/user/uvcvideo/v4l/firedtv-1394.c:41: warning: its scope is only this definition or declaration, which is probably not what you want
/home/user/uvcvideo/v4l/firedtv-1394.c: In function 'rawiso_activity_cb':
/home/user/uvcvideo/v4l/firedtv-1394.c:57: error: dereferencing pointer to incomplete type
/home/user/uvcvideo/v4l/firedtv-1394.c:58: error: implicit declaration of function 'hpsb_iso_n_ready'
/home/user/uvcvideo/v4l/firedtv-1394.c:65: error: dereferencing pointer to incomplete type
/home/user/uvcvideo/v4l/firedtv-1394.c:66: error: implicit declaration of function 'dma_region_i'
/home/user/uvcvideo/v4l/firedtv-1394.c:66: error: dereferencing pointer to incomplete type
/home/user/uvcvideo/v4l/firedtv-1394.c:66: error: expected expression before 'unsigned'
/home/user/uvcvideo/v4l/firedtv-1394.c:68: error: dereferencing pointer to incomplete type
/home/user/uvcvideo/v4l/firedtv-1394.c:72: error: dereferencing pointer to incomplete type
/home/user/uvcvideo/v4l/firedtv-1394.c:86: error: implicit declaration of function 'hpsb_iso_recv_release_packets'
/home/user/uvcvideo/v4l/firedtv-1394.c: In function 'node_of':
/home/user/uvcvideo/v4l/firedtv-1394.c:91: error: dereferencing pointer to incomplete type
/home/user/uvcvideo/v4l/firedtv-1394.c:91: warning: type defaults to 'int' in declaration of '__mptr'
/home/user/uvcvideo/v4l/firedtv-1394.c:91: warning: initialization from incompatible pointer type
/home/user/uvcvideo/v4l/firedtv-1394.c:91: error: invalid use of undefined type 'struct unit_directory'
/home/user/uvcvideo/v4l/firedtv-1394.c: In function 'node_lock':
/home/user/uvcvideo/v4l/firedtv-1394.c:96: error: 'quadlet_t' undeclared (first use in this function)
/home/user/uvcvideo/v4l/firedtv-1394.c:96: error: (Each undeclared identifier is reported only once
/home/user/uvcvideo/v4l/firedtv-1394.c:96: error: for each function it appears in.)
/home/user/uvcvideo/v4l/firedtv-1394.c:96: error: 'd' undeclared (first use in this function)
/home/user/uvcvideo/v4l/firedtv-1394.c:97: warning: ISO C90 forbids mixed declarations and code
/home/user/uvcvideo/v4l/firedtv-1394.c:99: error: implicit declaration of function 'hpsb_node_lock'
/home/user/uvcvideo/v4l/firedtv-1394.c:100: error: 'EXTCODE_COMPARE_SWAP' undeclared (first use in this function)
/home/user/uvcvideo/v4l/firedtv-1394.c: In function 'node_read':
/home/user/uvcvideo/v4l/firedtv-1394.c:108: error: implicit declaration of function 'hpsb_node_read'
/home/user/uvcvideo/v4l/firedtv-1394.c: In function 'node_write':
/home/user/uvcvideo/v4l/firedtv-1394.c:113: error: implicit declaration of function 'hpsb_node_write'
/home/user/uvcvideo/v4l/firedtv-1394.c: In function 'start_iso':
/home/user/uvcvideo/v4l/firedtv-1394.c:124: error: implicit declaration of function 'hpsb_iso_recv_init'
/home/user/uvcvideo/v4l/firedtv-1394.c:124: error: dereferencing pointer to incomplete type
/home/user/uvcvideo/v4l/firedtv-1394.c:126: error: 'HPSB_ISO_DMA_DEFAULT' undeclared (first use in this function)
/home/user/uvcvideo/v4l/firedtv-1394.c:135: error: implicit declaration of function 'hpsb_iso_recv_start'
/home/user/uvcvideo/v4l/firedtv-1394.c:138: error: implicit declaration of function 'hpsb_iso_shutdown'
/home/user/uvcvideo/v4l/firedtv-1394.c: In function 'stop_iso':
/home/user/uvcvideo/v4l/firedtv-1394.c:149: error: implicit declaration of function 'hpsb_iso_stop'
/home/user/uvcvideo/v4l/firedtv-1394.c: At top level:
/home/user/uvcvideo/v4l/firedtv-1394.c:164: warning: 'struct hpsb_host' declared inside parameter list
/home/user/uvcvideo/v4l/firedtv-1394.c: In function 'fcp_request':
/home/user/uvcvideo/v4l/firedtv-1394.c:177: error: dereferencing pointer to incomplete type
/home/user/uvcvideo/v4l/firedtv-1394.c:178: error: dereferencing pointer to incomplete type
/home/user/uvcvideo/v4l/firedtv-1394.c: In function 'node_probe':
/home/user/uvcvideo/v4l/firedtv-1394.c:192: error: dereferencing pointer to incomplete type
/home/user/uvcvideo/v4l/firedtv-1394.c:192: warning: type defaults to 'int' in declaration of '__mptr'
/home/user/uvcvideo/v4l/firedtv-1394.c:192: warning: initialization from incompatible pointer type
/home/user/uvcvideo/v4l/firedtv-1394.c:192: error: invalid use of undefined type 'struct unit_directory'
/home/user/uvcvideo/v4l/firedtv-1394.c:197: error: dereferencing pointer to incomplete type
/home/user/uvcvideo/v4l/firedtv-1394.c:198: error: dereferencing pointer to incomplete type
/home/user/uvcvideo/v4l/firedtv-1394.c:199: error: implicit declaration of function 'CSR1212_TEXTUAL_DESCRIPTOR_LEAF_DATA'
/home/user/uvcvideo/v4l/firedtv-1394.c:199: error: dereferencing pointer to incomplete type
/home/user/uvcvideo/v4l/firedtv-1394.c: At top level:
/home/user/uvcvideo/v4l/firedtv-1394.c:258: warning: 'struct unit_directory' declared inside parameter list
/home/user/uvcvideo/v4l/firedtv-1394.c: In function 'node_update':
/home/user/uvcvideo/v4l/firedtv-1394.c:260: error: dereferencing pointer to incomplete type
/home/user/uvcvideo/v4l/firedtv-1394.c: At top level:
/home/user/uvcvideo/v4l/firedtv-1394.c:268: error: variable 'fdtv_driver' has initializer but incomplete type
/home/user/uvcvideo/v4l/firedtv-1394.c:269: error: unknown field 'name' specified in initializer
/home/user/uvcvideo/v4l/firedtv-1394.c:269: warning: excess elements in struct initializer
/home/user/uvcvideo/v4l/firedtv-1394.c:269: warning: (near initialization for 'fdtv_driver')
/home/user/uvcvideo/v4l/firedtv-1394.c:270: error: unknown field 'id_table' specified in initializer
/home/user/uvcvideo/v4l/firedtv-1394.c:270: warning: excess elements in struct initializer
/home/user/uvcvideo/v4l/firedtv-1394.c:270: warning: (near initialization for 'fdtv_driver')
/home/user/uvcvideo/v4l/firedtv-1394.c:271: error: unknown field 'update' specified in initializer
/home/user/uvcvideo/v4l/firedtv-1394.c:271: warning: excess elements in struct initializer
/home/user/uvcvideo/v4l/firedtv-1394.c:271: warning: (near initialization for 'fdtv_driver')
/home/user/uvcvideo/v4l/firedtv-1394.c:272: error: unknown field 'driver' specified in initializer
/home/user/uvcvideo/v4l/firedtv-1394.c:272: error: extra brace group at end of initializer
/home/user/uvcvideo/v4l/firedtv-1394.c:272: error: (near initialization for 'fdtv_driver')
/home/user/uvcvideo/v4l/firedtv-1394.c:275: warning: excess elements in struct initializer
/home/user/uvcvideo/v4l/firedtv-1394.c:275: warning: (near initialization for 'fdtv_driver')
/home/user/uvcvideo/v4l/firedtv-1394.c:278: error: variable 'fdtv_highlevel' has initializer but incomplete type
/home/user/uvcvideo/v4l/firedtv-1394.c:279: error: unknown field 'name' specified in initializer
/home/user/uvcvideo/v4l/firedtv-1394.c:279: warning: excess elements in struct initializer
/home/user/uvcvideo/v4l/firedtv-1394.c:279: warning: (near initialization for 'fdtv_highlevel')
/home/user/uvcvideo/v4l/firedtv-1394.c:280: error: unknown field 'fcp_request' specified in initializer
/home/user/uvcvideo/v4l/firedtv-1394.c:280: warning: excess elements in struct initializer
/home/user/uvcvideo/v4l/firedtv-1394.c:280: warning: (near initialization for 'fdtv_highlevel')
/home/user/uvcvideo/v4l/firedtv-1394.c: In function 'fdtv_1394_init':
/home/user/uvcvideo/v4l/firedtv-1394.c:287: error: implicit declaration of function 'hpsb_register_highlevel'
/home/user/uvcvideo/v4l/firedtv-1394.c:288: error: implicit declaration of function 'hpsb_register_protocol'
/home/user/uvcvideo/v4l/firedtv-1394.c:291: error: implicit declaration of function 'hpsb_unregister_highlevel'
/home/user/uvcvideo/v4l/firedtv-1394.c: In function 'fdtv_1394_exit':
/home/user/uvcvideo/v4l/firedtv-1394.c:298: error: implicit declaration of function 'hpsb_unregister_protocol'
make[3]: *** [/home/user/uvcvideo/v4l/firedtv-1394.o] Error 1
make[2]: *** [_module_/home/user/uvcvideo/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/user/uvcvideo/v4l'
make: *** [all] Error 2

And after that installing it (sudo make install) will not work also.

Any suggestions?

---

### Post by panopticon on 2010-07-22
Have you tried this guide? [https://help.ubuntu.com/community/UVC#Installing](https://help.ubuntu.com/community/UVC#Installing) UVC

---

### Post by no2498 on 2010-07-22
have you tried the cam in cheese webcam booth

most webcams just work now days

or try it in gstreamer-properties


open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

cheese has a nice help file look in the faq's

---

### Post by XM500 on 2010-07-23
> **panopticon said:**
> Have you tried this guide? [https://help.ubuntu.com/community/UVC#Installing](https://help.ubuntu.com/community/UVC#Installing) UVC
Yes, I tried it but I get these errors above when I enter "sudo make" command in Terminal.
> **no2498 said:**
> have you tried the cam in cheese webcam booth

most webcams just work now days

or try it in gstreamer-properties


open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

cheese has a nice help file look in the faq's
Yes, I have tried cheese also, but no picture. I guess its because of the missing UVC driver... I know - most webcams worked out-of-box for me also since this. Tried also "gstreamer-properties" and no picture with V4L1 or V4L2 (see screenshots below).

Guess I still need to compile that uvcvideo driver sucessfully to get this camera working, but how? I cannot sort these errors out by my self.


edit:
added some pics:

[[IMG]http://www.upload.ee/thumb/700898/Screenshot.png[/IMG]]("http://www.upload.ee/image/700898/Screenshot.png")

[[IMG]http://www.upload.ee/thumb/700899/Screenshot-1.png[/IMG]]("http://www.upload.ee/image/700899/Screenshot-1.png")

[[IMG]http://www.upload.ee/thumb/700903/Screenshot.png[/IMG]]("http://www.upload.ee/image/700903/Screenshot.png")


EDIT:
I did kernel update and webcam works!
Followed this tutorial: [http://www.ramoonus.nl/2010/05/linux-kernel-2-6-34-installation-guide-for-ubuntu-linux-10-04/](http://www.ramoonus.nl/2010/05/linux-kernel-2-6-34-installation-guide-for-ubuntu-linux-10-04/)

---

### Post by no2498 on 2010-07-23
glad you got it working

---

