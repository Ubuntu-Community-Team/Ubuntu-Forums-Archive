---
title: "V4L-DVB Device Drivers"
date: 2013-05-15
forum: Multimedia Software
---

### Post by razza30 on 2013-05-15
I am following the instructions here: [http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

Specifically:
```
git clone git://linuxtv.org/media_build.git
cd media_build
./build
```

I get the following failure:
```

...
  CC [M]  /home/ray/media_build/v4l/drxk_hard.o
  CC [M]  /home/ray/media_build/v4l/dvbdev.o
  CC [M]  /home/ray/media_build/v4l/dmxdev.o
  CC [M]  /home/ray/media_build/v4l/dvb_demux.o
  CC [M]  /home/ray/media_build/v4l/dvb_filter.o
  CC [M]  /home/ray/media_build/v4l/dvb_ca_en50221.o
  CC [M]  /home/ray/media_build/v4l/dvb_frontend.o
  CC [M]  /home/ray/media_build/v4l/dvb_net.o
/home/ray/media_build/v4l/dvb_net.c: In function 'dvb_net_eth_type_trans':
/home/ray/media_build/v4l/dvb_net.c:188:29: error: 'ETH_P_802_3_MIN' undeclared (first use in this function)
/home/ray/media_build/v4l/dvb_net.c:188:29: note: each undeclared identifier is reported only once for each function it appears in
/home/ray/media_build/v4l/dvb_net.c: In function 'ule_bridged_sndu':
/home/ray/media_build/v4l/dvb_net.c:231:27: error: 'ETH_P_802_3_MIN' undeclared (first use in this function)
/home/ray/media_build/v4l/dvb_net.c: In function 'handle_ule_extensions':
/home/ray/media_build/v4l/dvb_net.c:323:30: error: 'ETH_P_802_3_MIN' undeclared (first use in this function)
/home/ray/media_build/v4l/dvb_net.c: In function 'dvb_net_ule':
/home/ray/media_build/v4l/dvb_net.c:715:31: error: 'ETH_P_802_3_MIN' undeclared (first use in this function)
make[3]: *** [/home/ray/media_build/v4l/dvb_net.o] Error 1
make[2]: *** [_module_/home/ray/media_build/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-3.2.0-41-generic-pae'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/ray/media_build/v4l'
make: *** [all] Error 2
build failed at ./build line 452.

```
Any advice?

---

### Post by oldos2er on 2013-05-15
What device do you have?

---

### Post by shlomicthailand on 2013-08-31
why the device is matter - according to instructions you suppose to git pull then build .

---

