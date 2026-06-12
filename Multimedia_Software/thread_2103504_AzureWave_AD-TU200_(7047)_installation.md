---
title: "AzureWave AD-TU200 (7047) installation"
date: 2013-01-10
forum: Multimedia Software
---

### Post by beardedwondr on 2013-01-10
Hi,
I've been trying to get this card installed for a while now, and i'm going spare trying to get it working.

lsusb: ID 13d3:3216 IMC Networks DTV-DVB UDTT 7047-USB 2.0 DVB-T Driver

I have followed all the instructions on the V4l wiki:

[http://linuxtv.org/wiki/index.php/Realtek_RTL2831U](http://linuxtv.org/wiki/index.php/Realtek_RTL2831U)

```
hg clone [http://linuxtv.org/hg/~jhoogenraad/rtl2831-r2]("http://linuxtv.org/hg/%7Ejhoogenraad/rtl2831-r2")
make
make install
```Stops at make:
```
In file included from /home/phil/rtl2831-r2/v4l/tuner-xc2028.h:10:0,
                 from /home/phil/rtl2831-r2/v4l/tuner-xc2028.c:22:
/home/phil/rtl2831-r2/v4l/dvb_frontend.h:49:33: error: field 'parameters' has incomplete type
/home/phil/rtl2831-r2/v4l/dvb_frontend.h:313:28: error: array type has incomplete element type
/home/phil/rtl2831-r2/v4l/tuner-xc2028.c: In function 'xc2028_set_params':
/home/phil/rtl2831-r2/v4l/tuner-xc2028.c:1081:2: error: unknown type name 'fe_bandwidth_t'
/home/phil/rtl2831-r2/v4l/tuner-xc2028.c:1081:26: error: 'BANDWIDTH_8_MHZ' undeclared (first use in this function)
/home/phil/rtl2831-r2/v4l/tuner-xc2028.c:1081:26: note: each undeclared identifier is reported only once for each function it appears in
/home/phil/rtl2831-r2/v4l/tuner-xc2028.c:1088:9: error: dereferencing pointer to incomplete type
/home/phil/rtl2831-r2/v4l/tuner-xc2028.c:1094:13: error: 'BANDWIDTH_6_MHZ' undeclared (first use in this function)
/home/phil/rtl2831-r2/v4l/tuner-xc2028.c:1109:8: error: dereferencing pointer to incomplete type
/home/phil/rtl2831-r2/v4l/tuner-xc2028.c:1116:7: error: 'BANDWIDTH_7_MHZ' undeclared (first use in this function)
/home/phil/rtl2831-r2/v4l/tuner-xc2028.c:1117:8: error: dereferencing pointer to incomplete type
/home/phil/rtl2831-r2/v4l/tuner-xc2028.c:1177:31: error: dereferencing pointer to incomplete type
/home/phil/rtl2831-r2/v4l/tuner-xc2028.c:1178:5: error: 'T_DIGITAL_TV' undeclared (first use in this function)
/home/phil/rtl2831-r2/v4l/tuner-xc2028.c:1179:1: warning: control reaches end of non-void function [-Wreturn-type]
make[3]: *** [/home/phil/rtl2831-r2/v4l/tuner-xc2028.o] Error 1
make[2]: *** [_module_/home/phil/rtl2831-r2/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-3.5.0-19-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/phil/rtl2831-r2/v4l'
make: *** [all] Error 2
``````

hg clone [http://linuxtv.org/hg/~anttip/rtl2831u/]("http://linuxtv.org/hg/%7Eanttip/rtl2831u/")
make
make install
```Stops at make:
```
In file included from <command-line>:0:0:
/home/phil/rtl2831-r2/rtl2831u/v4l/config-compat.h:4:28: fatal error: linux/autoconf.h: No such file or directory
compilation terminated.
make[3]: *** [/home/phil/rtl2831-r2/rtl2831u/v4l/tuner-xc2028.o] Error 1
make[2]: *** [_module_/home/phil/rtl2831-r2/rtl2831u/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-3.5.0-19-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/phil/rtl2831-r2/rtl2831u/v4l'
make: *** [all] Error 2
```So I then point 'config-compat.h' to a valid autoconf.h, run make again and it trips up over another tuner:
```
CC [M]  /home/phil/rtl2831-r2/rtl2831u/v4l/tuner-xc2028.o
In file included from /home/phil/rtl2831-r2/rtl2831u/v4l/tuner-xc2028.h:10:0,
                 from /home/phil/rtl2831-r2/rtl2831u/v4l/tuner-xc2028.c:21:
/home/phil/rtl2831-r2/rtl2831u/v4l/dvb_frontend.h:48:33: error: field 'parameters' has incomplete type
/home/phil/rtl2831-r2/rtl2831u/v4l/dvb_frontend.h:312:28: error: array type has incomplete element type
/home/phil/rtl2831-r2/rtl2831u/v4l/tuner-xc2028.c: In function 'free_firmware':
/home/phil/rtl2831-r2/rtl2831u/v4l/tuner-xc2028.c:251:3: error: implicit declaration of function 'kfree' [-Werror=implicit-function-declaration]
/home/phil/rtl2831-r2/rtl2831u/v4l/tuner-xc2028.c: In function 'load_all_firmwares':
/home/phil/rtl2831-r2/rtl2831u/v4l/tuner-xc2028.c:313:2: error: implicit declaration of function 'kzalloc' [-Werror=implicit-function-declaration]
/home/phil/rtl2831-r2/rtl2831u/v4l/tuner-xc2028.c:313:13: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/phil/rtl2831-r2/rtl2831u/v4l/tuner-xc2028.c:364:21: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/phil/rtl2831-r2/rtl2831u/v4l/tuner-xc2028.c: In function 'generic_set_freq':
/home/phil/rtl2831-r2/rtl2831u/v4l/tuner-xc2028.c:932:18: error: 'T_DIGITAL_TV' undeclared (first use in this function)
/home/phil/rtl2831-r2/rtl2831u/v4l/tuner-xc2028.c:932:18: note: each undeclared identifier is reported only once for each function it appears in
/home/phil/rtl2831-r2/rtl2831u/v4l/tuner-xc2028.c: In function 'xc2028_set_params':
/home/phil/rtl2831-r2/rtl2831u/v4l/tuner-xc2028.c:1028:2: error: unknown type name 'fe_bandwidth_t'
/home/phil/rtl2831-r2/rtl2831u/v4l/tuner-xc2028.c:1028:26: error: 'BANDWIDTH_8_MHZ' undeclared (first use in this function)
/home/phil/rtl2831-r2/rtl2831u/v4l/tuner-xc2028.c:1035:9: error: dereferencing pointer to incomplete type
/home/phil/rtl2831-r2/rtl2831u/v4l/tuner-xc2028.c:1041:13: error: 'BANDWIDTH_6_MHZ' undeclared (first use in this function)
/home/phil/rtl2831-r2/rtl2831u/v4l/tuner-xc2028.c:1056:8: error: dereferencing pointer to incomplete type
/home/phil/rtl2831-r2/rtl2831u/v4l/tuner-xc2028.c:1063:7: error: 'BANDWIDTH_7_MHZ' undeclared (first use in this function)
/home/phil/rtl2831-r2/rtl2831u/v4l/tuner-xc2028.c:1064:8: error: dereferencing pointer to incomplete type
/home/phil/rtl2831-r2/rtl2831u/v4l/tuner-xc2028.c:1117:31: error: dereferencing pointer to incomplete type
/home/phil/rtl2831-r2/rtl2831u/v4l/tuner-xc2028.c:1118:5: error: 'T_DIGITAL_TV' undeclared (first use in this function)
/home/phil/rtl2831-r2/rtl2831u/v4l/tuner-xc2028.c: In function 'xc2028_attach':
/home/phil/rtl2831-r2/rtl2831u/v4l/tuner-xc2028.c:1255:13: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/phil/rtl2831-r2/rtl2831u/v4l/tuner-xc2028.c: In function 'xc2028_set_params':
/home/phil/rtl2831-r2/rtl2831u/v4l/tuner-xc2028.c:1119:1: warning: control reaches end of non-void function [-Wreturn-type]
cc1: some warnings being treated as errors
make[3]: *** [/home/phil/rtl2831-r2/rtl2831u/v4l/tuner-xc2028.o] Error 1
make[2]: *** [_module_/home/phil/rtl2831-r2/rtl2831u/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-3.5.0-19-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/phil/rtl2831-r2/rtl2831u/v4l'
make: *** [all] Error 2
```I have managed to get another usb tv card working previously, which was just a case of putting a .fw file in /lib/firmware/ 

Does anyone have any pointers on how to get this working?

EDIT: 
Distributor ID:    Ubuntu
Description:    Ubuntu 12.10
Release:    12.10
Codename:    quantal
3.5.0-19-generic

---

### Post by beardedwondr on 2013-01-19
Hi,
I still can't get this stick to work. I have tried the install procedure here: [http://ubuntuforums.org/showthread.php?t=2078342](http://ubuntuforums.org/showthread.php?t=2078342) 

When I run the make command it seems to run fine, the only errors I can see are:
```
make[1]: Entering directory `/home/phil/media_build/v4l/firmware'
ln: accessing `../../linux/firmware/dabusb//*': No such file or directory
```

'sudo make install' gives 367 lines, the only problems seem to be:
```
make[2]: Entering directory `/home/phil/media_build/v4l/firmware'
Installing firmwares at /lib/firmware: vicam/firmware.fw dabusb/firmware.fw cp: cannot stat `dabusb/firmware.fw': No such file or directory
dabusb/bitstream.bin cp: cannot stat `dabusb/bitstream.bin': No such file or directory
```

---

