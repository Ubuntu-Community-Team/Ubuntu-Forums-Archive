---
title: "Trying to get Myth to work with a Hauppauge Capture Card"
date: 2010-04-09
forum: Multimedia Software
---

### Post by mjr2k on 2010-04-09
I have a Hauppauge HVR-2250 and having a heck of a time getting it to work in Ubuntu Karmic.

I downloaded the driver(s) from Steven Toth's website and I followed another poster's exactly instructions on installation and I came up with errors up the wazoo.  Here's what I got when I did "make":
```

mike@tivo:~/v4l-dvb-7c0b887911cf$ sudo make
[sudo] password for mike: 
make -C /home/mike/v4l-dvb-7c0b887911cf/v4l 
make[1]: Entering directory `/home/mike/v4l-dvb-7c0b887911cf/v4l'
creating symbolic links...
make -C firmware prep
make[2]: Entering directory `/home/mike/v4l-dvb-7c0b887911cf/v4l/firmware'
make[2]: Leaving directory `/home/mike/v4l-dvb-7c0b887911cf/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/mike/v4l-dvb-7c0b887911cf/v4l/firmware'
make[2]: Nothing to be done for `default'.
make[2]: Leaving directory `/home/mike/v4l-dvb-7c0b887911cf/v4l/firmware'
Kernel build directory is /lib/modules/2.6.31-14-generic/build
make -C /lib/modules/2.6.31-14-generic/build SUBDIRS=/home/mike/v4l-dvb-7c0b887911cf/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.o
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:21:17: error: dma.h: No such file or directory
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:22:21: error: csr1212.h: No such file or directory
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:23:23: error: highlevel.h: No such file or directory
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:24:19: error: hosts.h: No such file or directory
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:25:22: error: ieee1394.h: No such file or directory
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:26:17: error: iso.h: No such file or directory
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:27:21: error: nodemgr.h: No such file or directory
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:40: warning: 'struct hpsb_iso' declared inside parameter list
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:40: warning: its scope is only this definition or declaration, which is probably not what you want
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c: In function 'rawiso_activity_cb':
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:56: error: dereferencing pointer to incomplete type
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:57: error: implicit declaration of function 'hpsb_iso_n_ready'
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:64: error: dereferencing pointer to incomplete type
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:65: error: implicit declaration of function 'dma_region_i'
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:65: error: dereferencing pointer to incomplete type
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:65: error: expected expression before 'unsigned'
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:66: warning: assignment makes pointer from integer without a cast
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:67: error: dereferencing pointer to incomplete type
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:71: error: dereferencing pointer to incomplete type
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:85: error: implicit declaration of function 'hpsb_iso_recv_release_packets'
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c: In function 'node_of':
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:90: error: dereferencing pointer to incomplete type
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:90: warning: type defaults to 'int' in declaration of '__mptr'
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:90: warning: initialization from incompatible pointer type
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:90: error: invalid use of undefined type 'struct unit_directory'
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c: In function 'node_lock':
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:95: error: 'quadlet_t' undeclared (first use in this function)
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:95: error: (Each undeclared identifier is reported only once
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:95: error: for each function it appears in.)
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:95: error: 'd' undeclared (first use in this function)
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:96: warning: ISO C90 forbids mixed declarations and code
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:98: error: implicit declaration of function 'hpsb_node_lock'
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:99: error: 'EXTCODE_COMPARE_SWAP' undeclared (first use in this function)
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c: In function 'node_read':
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:107: error: implicit declaration of function 'hpsb_node_read'
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c: In function 'node_write':
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:112: error: implicit declaration of function 'hpsb_node_write'
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c: In function 'start_iso':
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:123: error: implicit declaration of function 'hpsb_iso_recv_init'
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:123: error: dereferencing pointer to incomplete type
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:125: error: 'HPSB_ISO_DMA_DEFAULT' undeclared (first use in this function)
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:127: warning: assignment makes pointer from integer without a cast
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:134: error: implicit declaration of function 'hpsb_iso_recv_start'
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:137: error: implicit declaration of function 'hpsb_iso_shutdown'
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c: In function 'stop_iso':
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:148: error: implicit declaration of function 'hpsb_iso_stop'
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c: At top level:
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:163: warning: 'struct hpsb_host' declared inside parameter list
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c: In function 'fcp_request':
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:176: error: dereferencing pointer to incomplete type
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:177: error: dereferencing pointer to incomplete type
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c: In function 'node_probe':
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:191: error: dereferencing pointer to incomplete type
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:191: warning: type defaults to 'int' in declaration of '__mptr'
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:191: warning: initialization from incompatible pointer type
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:191: error: invalid use of undefined type 'struct unit_directory'
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:196: error: dereferencing pointer to incomplete type
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:197: error: dereferencing pointer to incomplete type
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:198: error: implicit declaration of function 'CSR1212_TEXTUAL_DESCRIPTOR_LEAF_DATA'
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:198: error: dereferencing pointer to incomplete type
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:198: warning: assignment makes pointer from integer without a cast
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c: At top level:
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:257: warning: 'struct unit_directory' declared inside parameter list
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c: In function 'node_update':
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:259: error: dereferencing pointer to incomplete type
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c: At top level:
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:267: error: variable 'fdtv_driver' has initializer but incomplete type
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:268: error: unknown field 'name' specified in initializer
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:268: warning: excess elements in struct initializer
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:268: warning: (near initialization for 'fdtv_driver')
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:269: error: unknown field 'id_table' specified in initializer
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:269: warning: excess elements in struct initializer
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:269: warning: (near initialization for 'fdtv_driver')
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:270: error: unknown field 'update' specified in initializer
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:270: warning: excess elements in struct initializer
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:270: warning: (near initialization for 'fdtv_driver')
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:271: error: unknown field 'driver' specified in initializer
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:271: error: extra brace group at end of initializer
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:271: error: (near initialization for 'fdtv_driver')
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:274: warning: excess elements in struct initializer
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:274: warning: (near initialization for 'fdtv_driver')
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:277: error: variable 'fdtv_highlevel' has initializer but incomplete type
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:278: error: unknown field 'name' specified in initializer
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:278: warning: excess elements in struct initializer
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:278: warning: (near initialization for 'fdtv_highlevel')
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:279: error: unknown field 'fcp_request' specified in initializer
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:279: warning: excess elements in struct initializer
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:279: warning: (near initialization for 'fdtv_highlevel')
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c: In function 'fdtv_1394_init':
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:286: error: implicit declaration of function 'hpsb_register_highlevel'
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:287: error: implicit declaration of function 'hpsb_register_protocol'
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:290: error: implicit declaration of function 'hpsb_unregister_highlevel'
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c: In function 'fdtv_1394_exit':
/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.c:297: error: implicit declaration of function 'hpsb_unregister_protocol'
make[3]: *** [/home/mike/v4l-dvb-7c0b887911cf/v4l/firedtv-1394.o] Error 1
make[2]: *** [_module_/home/mike/v4l-dvb-7c0b887911cf/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/mike/v4l-dvb-7c0b887911cf/v4l'
make: *** [all] Error 2
mike@tivo:~/v4l-dvb-7c0b887911cf$ 
```

When I do "make install", I get:
```

mike@tivo:~/v4l-dvb-7c0b887911cf$ sudo make install
make -C /home/mike/v4l-dvb-7c0b887911cf/v4l install
make[1]: Entering directory `/home/mike/v4l-dvb-7c0b887911cf/v4l'
-e 
Removing obsolete files from /lib/modules/2.6.31-14-generic/kernel/drivers/media/video:

-e 
Removing obsolete files from /lib/modules/2.6.31-14-generic/kernel/drivers/media/dvb/cinergyT2:

-e 
Removing obsolete files from /lib/modules/2.6.31-14-generic/kernel/drivers/media/common:

-e 
Removing obsolete files from /lib/modules/2.6.31-14-generic/kernel/drivers/media/dvb/frontends:

Installing kernel modules under /lib/modules/2.6.31-14-generic/kernel/drivers/media/:
/sbin/depmod -a 2.6.31-14-generic 
make -C firmware install
make[2]: Entering directory `/home/mike/v4l-dvb-7c0b887911cf/v4l/firmware'
Installing firmwares at /lib/firmware: vicam/firmware.fw dabusb/firmware.fw dabusb/bitstream.bin ttusb-budget/dspbootcode.bin cpia2/stv0672_vp4.bin av7110/bootcode.bin 
make[2]: Leaving directory `/home/mike/v4l-dvb-7c0b887911cf/v4l/firmware'
make[1]: Leaving directory `/home/mike/v4l-dvb-7c0b887911cf/v4l'
mike@tivo:~/v4l-dvb-7c0b887911cf$ 
```


In other screenshots that I've seen of success, it shows you what capture card is installed.  I'm decent with Linux but a novice when it comes to installing drivers.  Any help would be appreciated.

---

### Post by mjr2k on 2010-04-10
50 views and no replies?  Is it that nobody knows or am I truly a new person to this whole thing and should be kicked right square below the belt?

If nobody knows, could they recommend a TV Capture card that would work with Myth that I could invest in?

---

### Post by WinterRain on 2010-04-10
I hear the Hauppauge HVR-1600 is very linux friendly. Generally, with linux, if you want the greatest chance for compatibility, you need to use hardware that is a generation or 2 behind what windows users are using. Linux devs and manufacturers need time to develop drivers for the linux kernel.

---

### Post by mjr2k on 2010-04-10
> **WinterRain said:**
> I hear the Hauppauge HVR-1600 is very linux friendly. Generally, with linux, if you want the greatest chance for compatibility, you need to use hardware that is a generation or 2 behind what windows users are using. Linux devs and manufacturers need time to develop drivers for the linux kernel.

I don't need the latest and greatest - I only bought the 2250 at the time because it's dual tuner and was supposed to integrate well with WMC 7.  The proprietary software is a POS.  As far as Myth goes, Everything I've read says that Myth is not only the most stable, but the most customizable.  I have no problem returning or selling the 2250 and getting something else.

---

### Post by WinterRain on 2010-04-10
Here it is [http://www.newegg.com/Product/Product.aspx?Item=N82E16815116033&cm_re=hvr_1600-_-15-116-033-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16815116033&cm_re=hvr_1600-_-15-116-033-_-Product)

Just remember mythtv can be a bit of a project. Be patient and you should be OK. You could also check over at the mythtv forums for help. Good luck.

---

### Post by mjr2k on 2010-04-10
> **WinterRain said:**
> Here it is [http://www.newegg.com/Product/Product.aspx?Item=N82E16815116033&cm_re=hvr_1600-_-15-116-033-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16815116033&cm_re=hvr_1600-_-15-116-033-_-Product)

Just remember mythtv can be a bit of a project. Be patient and you should be OK. You could also check over at the mythtv forums for help. Good luck.

I know that... that's why I was trying it out; something different.

I'll check those forums out.  Thanks for the help and URL!

---

