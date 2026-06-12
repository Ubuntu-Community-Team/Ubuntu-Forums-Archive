---
title: "error compiling em2880 driver"
date: 2009-01-24
forum: Multimedia Software
---

### Post by jmite on 2009-01-24
I'm trying to compile the em2880 driver (for a MSI vox video capture card) for my ubuntu laptop... when I do "make" it gives the following output:

```


joey@joey-laptop:~/driver/em28xx-new$ make

running ./build.sh build

make[1]: Entering directory `/home/joey/driver/em28xx-new'
rm -rf Module.symvers; 
make -C /lib/modules/`if [ -d /lib/modules/2.6.21.4-eeepc ]; then echo 2.6.21.4-eeepc; else uname -r; fi`/build SUBDIRS=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /home/joey/driver/em28xx-new/em2880-dvb.o
In file included from /home/joey/driver/em28xx-new/em2880-dvb.c:37:
/home/joey/driver/em28xx-new/em28xx.h:32:20: error: dmxdev.h: No such file or directory
/home/joey/driver/em28xx-new/em28xx.h:33:23: error: dvb_demux.h: No such file or directory
/home/joey/driver/em28xx-new/em28xx.h:34:21: error: dvb_net.h: No such file or directory
/home/joey/driver/em28xx-new/em28xx.h:35:26: error: dvb_frontend.h: No such file or directory
In file included from /home/joey/driver/em28xx-new/em2880-dvb.c:37:
/home/joey/driver/em28xx-new/em28xx.h:560: error: field ‘demux’ has incomplete type
/home/joey/driver/em28xx-new/em28xx.h:568: error: field ‘adapter’ has incomplete type
/home/joey/driver/em28xx-new/em28xx.h:571: error: field ‘dmxdev’ has incomplete type
/home/joey/driver/em28xx-new/em28xx.h:573: error: field ‘dvbnet’ has incomplete type
In file included from /home/joey/driver/em28xx-new/em2880-dvb.c:44:
/home/joey/driver/em28xx-new/mt352/mt352.h: In function ‘mt352_write’:
/home/joey/driver/em28xx-new/mt352/mt352.h:68: error: dereferencing pointer to incomplete type
/home/joey/driver/em28xx-new/mt352/mt352.h:69: error: dereferencing pointer to incomplete type
In file included from /home/joey/driver/em28xx-new/em2880-dvb.c:46:
/home/joey/driver/em28xx-new/drx3973d/drx3973d_demod.h: At top level:
/home/joey/driver/em28xx-new/drx3973d/drx3973d_demod.h:9: error: field ‘frontend’ has incomplete type
/home/joey/driver/em28xx-new/em2880-dvb.c:52:22: error: lgdt330x.h: No such file or directory
/home/joey/driver/em28xx-new/em2880-dvb.c:245: warning: ‘struct dvb_frontend_tune_settings’ declared inside parameter list
/home/joey/driver/em28xx-new/em2880-dvb.c:245: warning: its scope is only this definition or declaration, which is probably not what you want
/home/joey/driver/em28xx-new/em2880-dvb.c: In function ‘em2880_fe_get_tune_settings’:
/home/joey/driver/em28xx-new/em2880-dvb.c:246: error: dereferencing pointer to incomplete type
/home/joey/driver/em28xx-new/em2880-dvb.c:247: error: dereferencing pointer to incomplete type
/home/joey/driver/em28xx-new/em2880-dvb.c:248: error: dereferencing pointer to incomplete type
/home/joey/driver/em28xx-new/em2880-dvb.c: At top level:
/home/joey/driver/em28xx-new/em2880-dvb.c:276: error: variable ‘em2880_fe_template_ops’ has initializer but incomplete type
/home/joey/driver/em28xx-new/em2880-dvb.c:277: error: unknown field ‘info’ specified in initializer
/home/joey/driver/em28xx-new/em2880-dvb.c:277: error: extra brace group at end of initializer
/home/joey/driver/em28xx-new/em2880-dvb.c:277: error: (near initialization for ‘em2880_fe_template_ops’)
/home/joey/driver/em28xx-new/em2880-dvb.c:284: warning: excess elements in struct initializer
/home/joey/driver/em28xx-new/em2880-dvb.c:284: warning: (near initialization for ‘em2880_fe_template_ops’)
/home/joey/driver/em28xx-new/em2880-dvb.c:285: error: unknown field ‘init’ specified in initializer
/home/joey/driver/em28xx-new/em2880-dvb.c:285: warning: excess elements in struct initializer
/home/joey/driver/em28xx-new/em2880-dvb.c:285: warning: (near initialization for ‘em2880_fe_template_ops’)
/home/joey/driver/em28xx-new/em2880-dvb.c:286: error: unknown field ‘release’ specified in initializer
/home/joey/driver/em28xx-new/em2880-dvb.c:286: warning: excess elements in struct initializer
/home/joey/driver/em28xx-new/em2880-dvb.c:286: warning: (near initialization for ‘em2880_fe_template_ops’)
/home/joey/driver/em28xx-new/em2880-dvb.c:288: error: unknown field ‘sleep’ specified in initializer
/home/joey/driver/em28xx-new/em2880-dvb.c:288: warning: excess elements in struct initializer
/home/joey/driver/em28xx-new/em2880-dvb.c:288: warning: (near initialization for ‘em2880_fe_template_ops’)
/home/joey/driver/em28xx-new/em2880-dvb.c:289: error: unknown field ‘set_frontend’ specified in initializer
/home/joey/driver/em28xx-new/em2880-dvb.c:289: warning: excess elements in struct initializer
/home/joey/driver/em28xx-new/em2880-dvb.c:289: warning: (near initialization for ‘em2880_fe_template_ops’)
/home/joey/driver/em28xx-new/em2880-dvb.c:290: error: unknown field ‘get_frontend’ specified in initializer
/home/joey/driver/em28xx-new/em2880-dvb.c:290: warning: excess elements in struct initializer
/home/joey/driver/em28xx-new/em2880-dvb.c:290: warning: (near initialization for ‘em2880_fe_template_ops’)
/home/joey/driver/em28xx-new/em2880-dvb.c:291: error: unknown field ‘get_tune_settings’ specified in initializer
/home/joey/driver/em28xx-new/em2880-dvb.c:291: warning: excess elements in struct initializer
/home/joey/driver/em28xx-new/em2880-dvb.c:291: warning: (near initialization for ‘em2880_fe_template_ops’)
/home/joey/driver/em28xx-new/em2880-dvb.c:292: error: unknown field ‘read_status’ specified in initializer
/home/joey/driver/em28xx-new/em2880-dvb.c:292: warning: excess elements in struct initializer
/home/joey/driver/em28xx-new/em2880-dvb.c:292: warning: (near initialization for ‘em2880_fe_template_ops’)
/home/joey/driver/em28xx-new/em2880-dvb.c:293: error: unknown field ‘read_ber’ specified in initializer
/home/joey/driver/em28xx-new/em2880-dvb.c:293: warning: excess elements in struct initializer
/home/joey/driver/em28xx-new/em2880-dvb.c:293: warning: (near initialization for ‘em2880_fe_template_ops’)
/home/joey/driver/em28xx-new/em2880-dvb.c:294: error: unknown field ‘read_signal_strength’ specified in initializer
/home/joey/driver/em28xx-new/em2880-dvb.c:294: warning: excess elements in struct initializer
/home/joey/driver/em28xx-new/em2880-dvb.c:294: warning: (near initialization for ‘em2880_fe_template_ops’)
/home/joey/driver/em28xx-new/em2880-dvb.c:295: error: unknown field ‘read_snr’ specified in initializer
/home/joey/driver/em28xx-new/em2880-dvb.c:295: warning: excess elements in struct initializer
/home/joey/driver/em28xx-new/em2880-dvb.c:295: warning: (near initialization for ‘em2880_fe_template_ops’)
/home/joey/driver/em28xx-new/em2880-dvb.c:296: error: unknown field ‘read_ucblocks’ specified in initializer
/home/joey/driver/em28xx-new/em2880-dvb.c:297: warning: excess elements in struct initializer
/home/joey/driver/em28xx-new/em2880-dvb.c:297: warning: (near initialization for ‘em2880_fe_template_ops’)
/home/joey/driver/em28xx-new/em2880-dvb.c: In function ‘em2880_complete_irq’:
/home/joey/driver/em28xx-new/em2880-dvb.c:336: error: implicit declaration of function ‘dvb_dmx_swfilter’
/home/joey/driver/em28xx-new/em2880-dvb.c: At top level:
/home/joey/driver/em28xx-new/em2880-dvb.c:445: warning: ‘struct dvb_demux_feed’ declared inside parameter list
/home/joey/driver/em28xx-new/em2880-dvb.c: In function ‘em2880_start_feed’:
/home/joey/driver/em28xx-new/em2880-dvb.c:447: error: dereferencing pointer to incomplete type
/home/joey/driver/em28xx-new/em2880-dvb.c:448: error: dereferencing pointer to incomplete type
/home/joey/driver/em28xx-new/em2880-dvb.c: At top level:
/home/joey/driver/em28xx-new/em2880-dvb.c:462: warning: ‘struct dvb_demux_feed’ declared inside parameter list
/home/joey/driver/em28xx-new/em2880-dvb.c: In function ‘em2880_stop_feed’:
/home/joey/driver/em28xx-new/em2880-dvb.c:464: error: dereferencing pointer to incomplete type
/home/joey/driver/em28xx-new/em2880-dvb.c:465: error: dereferencing pointer to incomplete type
/home/joey/driver/em28xx-new/em2880-dvb.c: In function ‘em28xx_ts_bus_ctrl’:
/home/joey/driver/em28xx-new/em2880-dvb.c:491: error: dereferencing pointer to incomplete type
/home/joey/driver/em28xx-new/em2880-dvb.c: In function ‘mt352_pinnacle_init’:
/home/joey/driver/em28xx-new/em2880-dvb.c:542: error: dereferencing pointer to incomplete type
/home/joey/driver/em28xx-new/em2880-dvb.c: At top level:
/home/joey/driver/em28xx-new/em2880-dvb.c:570: error: variable ‘em2880_lgdt3303_dev’ has initializer but incomplete type
/home/joey/driver/em28xx-new/em2880-dvb.c:571: error: unknown field ‘demod_address’ specified in initializer
/home/joey/driver/em28xx-new/em2880-dvb.c:571: warning: excess elements in struct initializer
/home/joey/driver/em28xx-new/em2880-dvb.c:571: warning: (near initialization for ‘em2880_lgdt3303_dev’)
/home/joey/driver/em28xx-new/em2880-dvb.c:572: error: unknown field ‘demod_chip’ specified in initializer
/home/joey/driver/em28xx-new/em2880-dvb.c:572: error: ‘LGDT3303’ undeclared here (not in a function)
/home/joey/driver/em28xx-new/em2880-dvb.c:573: warning: excess elements in struct initializer
/home/joey/driver/em28xx-new/em2880-dvb.c:573: warning: (near initialization for ‘em2880_lgdt3303_dev’)
/home/joey/driver/em28xx-new/em2880-dvb.c: In function ‘kworld355u_i2c_gate_ctrl’:
/home/joey/driver/em28xx-new/em2880-dvb.c:587: error: field ‘frontend’ has incomplete type
/home/joey/driver/em28xx-new/em2880-dvb.c:593: error: dereferencing pointer to incomplete type
/home/joey/driver/em28xx-new/em2880-dvb.c: In function ‘em28xx_set_params’:
/home/joey/driver/em28xx-new/em2880-dvb.c:607: error: dereferencing pointer to incomplete type
/home/joey/driver/em28xx-new/em2880-dvb.c:616: error: dereferencing pointer to incomplete type
/home/joey/driver/em28xx-new/em2880-dvb.c: In function ‘em28xx_get_frequency’:
/home/joey/driver/em28xx-new/em2880-dvb.c:734: error: dereferencing pointer to incomplete type
/home/joey/driver/em28xx-new/em2880-dvb.c: In function ‘em28xx_get_bandwidth’:
/home/joey/driver/em28xx-new/em2880-dvb.c:741: error: dereferencing pointer to incomplete type
/home/joey/driver/em28xx-new/em2880-dvb.c: In function ‘em28xx_dvb_init’:
/home/joey/driver/em28xx-new/em2880-dvb.c:749: error: dereferencing pointer to incomplete type
/home/joey/driver/em28xx-new/em2880-dvb.c: In function ‘em28xx_s921_init’:
/home/joey/driver/em28xx-new/em2880-dvb.c:804: error: dereferencing pointer to incomplete type
/home/joey/driver/em28xx-new/em2880-dvb.c: In function ‘em28xx_zl10353_init’:
/home/joey/driver/em28xx-new/em2880-dvb.c:821: error: dereferencing pointer to incomplete type
/home/joey/driver/em28xx-new/em2880-dvb.c: In function ‘em28xx_zl10353_sleep’:
/home/joey/driver/em28xx-new/em2880-dvb.c:870: error: dereferencing pointer to incomplete type
/home/joey/driver/em28xx-new/em2880-dvb.c: In function ‘em28xx_dvb_sleep’:
/home/joey/driver/em28xx-new/em2880-dvb.c:886: error: dereferencing pointer to incomplete type
/home/joey/driver/em28xx-new/em2880-dvb.c: In function ‘em2880_dvb_init’:
/home/joey/driver/em28xx-new/em2880-dvb.c:957: error: implicit declaration of function ‘dvb_attach’
/home/joey/driver/em28xx-new/em2880-dvb.c:961: warning: assignment makes pointer from integer without a cast
/home/joey/driver/em28xx-new/em2880-dvb.c:980: warning: assignment makes pointer from integer without a cast
/home/joey/driver/em28xx-new/em2880-dvb.c:983: warning: assignment makes pointer from integer without a cast
/home/joey/driver/em28xx-new/em2880-dvb.c:988: warning: assignment makes pointer from integer without a cast
/home/joey/driver/em28xx-new/em2880-dvb.c:994: error: ‘lgdt330x_attach’ undeclared (first use in this function)
/home/joey/driver/em28xx-new/em2880-dvb.c:994: error: (Each undeclared identifier is reported only once
/home/joey/driver/em28xx-new/em2880-dvb.c:994: error: for each function it appears in.)
/home/joey/driver/em28xx-new/em2880-dvb.c:995: warning: assignment makes pointer from integer without a cast
/home/joey/driver/em28xx-new/em2880-dvb.c:1004: warning: assignment makes pointer from integer without a cast
/home/joey/driver/em28xx-new/em2880-dvb.c:1009: warning: assignment makes pointer from integer without a cast
/home/joey/driver/em28xx-new/em2880-dvb.c:1015: warning: assignment makes pointer from integer without a cast
/home/joey/driver/em28xx-new/em2880-dvb.c:1018: error: dereferencing pointer to incomplete type
/home/joey/driver/em28xx-new/em2880-dvb.c:1019: error: dereferencing pointer to incomplete type
/home/joey/driver/em28xx-new/em2880-dvb.c:1020: error: dereferencing pointer to incomplete type
/home/joey/driver/em28xx-new/em2880-dvb.c:1032: error: invalid application of ‘sizeof’ to incomplete type ‘struct dvb_frontend’ 
/home/joey/driver/em28xx-new/em2880-dvb.c:1033: error: dereferencing pointer to incomplete type
/home/joey/driver/em28xx-new/em2880-dvb.c:1033: error: invalid application of ‘sizeof’ to incomplete type ‘struct dvb_frontend_ops’ 
/home/joey/driver/em28xx-new/em2880-dvb.c:1047: error: dereferencing pointer to incomplete type
/home/joey/driver/em28xx-new/em2880-dvb.c:1048: error: dereferencing pointer to incomplete type
/home/joey/driver/em28xx-new/em2880-dvb.c:1050: error: dereferencing pointer to incomplete type
/home/joey/driver/em28xx-new/em2880-dvb.c:1052: error: dereferencing pointer to incomplete type
/home/joey/driver/em28xx-new/em2880-dvb.c:1056: error: dereferencing pointer to incomplete type
/home/joey/driver/em28xx-new/em2880-dvb.c:1058: error: dereferencing pointer to incomplete type
/home/joey/driver/em28xx-new/em2880-dvb.c:1067: error: dereferencing pointer to incomplete type
/home/joey/driver/em28xx-new/em2880-dvb.c:1081: error: dereferencing pointer to incomplete type
/home/joey/driver/em28xx-new/em2880-dvb.c:1083: error: dereferencing pointer to incomplete type
/home/joey/driver/em28xx-new/em2880-dvb.c:1084: error: dereferencing pointer to incomplete type
/home/joey/driver/em28xx-new/em2880-dvb.c:1102: error: dereferencing pointer to incomplete type
/home/joey/driver/em28xx-new/em2880-dvb.c:1105: error: implicit declaration of function ‘dvb_register_adapter’
/home/joey/driver/em28xx-new/em2880-dvb.c:1123: error: implicit declaration of function ‘dvb_register_frontend’
/home/joey/driver/em28xx-new/em2880-dvb.c:1130: error: ‘DMX_TS_FILTERING’ undeclared (first use in this function)
/home/joey/driver/em28xx-new/em2880-dvb.c:1131: error: ‘DMX_SECTION_FILTERING’ undeclared (first use in this function)
/home/joey/driver/em28xx-new/em2880-dvb.c:1132: error: ‘DMX_MEMORY_BASED_FILTERING’ undeclared (first use in this function)
/home/joey/driver/em28xx-new/em2880-dvb.c:1134: error: implicit declaration of function ‘dvb_dmx_init’
/home/joey/driver/em28xx-new/em2880-dvb.c:1145: error: implicit declaration of function ‘dvb_dmxdev_init’
/home/joey/driver/em28xx-new/em2880-dvb.c:1149: error: implicit declaration of function ‘dvb_dmxdev_release’
/home/joey/driver/em28xx-new/em2880-dvb.c:1160: error: implicit declaration of function ‘dvb_net_init’
/home/joey/driver/em28xx-new/em2880-dvb.c:1160: error: dereferencing pointer to incomplete type
/home/joey/driver/em28xx-new/em2880-dvb.c: In function ‘em2880_dvb_fini’:
/home/joey/driver/em28xx-new/em2880-dvb.c:1180: error: implicit declaration of function ‘dvb_net_release’
/home/joey/driver/em28xx-new/em2880-dvb.c:1181: error: implicit declaration of function ‘dvb_unregister_frontend’
/home/joey/driver/em28xx-new/em2880-dvb.c:1188: error: implicit declaration of function ‘dvb_frontend_detach’
/home/joey/driver/em28xx-new/em2880-dvb.c:1193: error: implicit declaration of function ‘dvb_dmx_release’
/home/joey/driver/em28xx-new/em2880-dvb.c:1195: error: implicit declaration of function ‘dvb_unregister_adapter’
make[3]: *** [/home/joey/driver/em28xx-new/em2880-dvb.o] Error 1
make[2]: *** [_module_/home/joey/driver/em28xx-new] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/joey/driver/em28xx-new'

```

anyone know why this is? how can I fix this?

---

### Post by gborzi on 2009-01-25
Hello jmite,
it looks like you are trying to compile the mcentral.de em28xx-new driver under Intrepid. The same problem has been reported [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204578"), just scroll down to Treviño and Chmiels posts. Treviño wrote that it is possible to get the missing kernel headers from the linux-source package.

---

### Post by Nickedynick on 2009-02-05
Hi, I don't know if it helps but I've had similar problems (see [here]("http://ubuntuforums.org/showthread.php?t=846340")).
Have you got it sorted yet?

---

### Post by gborzi on 2009-02-05
Hello Nickedynick and jmite,
I've found the solution to this problem on an italian language blog, see [here]("http://www.quadrantegamma.it/component/content/article/12-intrepid/60-pinnacle-pctv-usb-stick-dvb-t.html").
Even if you don't understand italian, it is easy to follow, just copy and paste in a shell the commands. I followed this guide to get my dazzle TV to work under an Intrepid installation on an USB stick. The only different command I used was > hg clone [http://mcentral.de/hg/~mrec/em28xx-new](http://mcentral.de/hg/~mrec/em28xx-new) i.e. without "pinnacle" at the end.
Don't hesitate to ask me if something is not clear to you. I've seen similar howtos in german and french, but none in english.

Hope it works.

---

### Post by Nickedynick on 2009-02-11
Awesome, it works!! Thanks :)

---

