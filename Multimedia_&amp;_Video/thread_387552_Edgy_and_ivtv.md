---
title: "Edgy and ivtv"
date: 2007-03-18
forum: Multimedia &amp; Video
---

### Post by ejconcepcion on 2007-03-18
HI,

I'm attempting the install mythtv on Edgy. I'm using the howto @ [http://www.djlosch.com/article_How-to:_Ubuntu_Edgy_and_MythTV_and_Hauppauge_PVR-150]("http://www.djlosch.com/article_How-to:_Ubuntu_Edgy_and_MythTV_and_Hauppauge_PVR-150")

I can't get the ivtv drivers to install. Everything is fine until I get the the point of installing the ivtv drivers.

```
m-a a-i ivtv
```

Module assistant runs and fails to complete. Here is the log.

```
dh_clean
/usr/bin/make KVER=2.6.15-26-386 KDIR=/lib/modules/2.6.15-26-386/build HP_FWLOAD=1 DEBIAN_MAKE_KPKG=1 -C driver clean
make[1]: Entering directory `/usr/src/modules/ivtv/driver'
/usr/bin/make -C /lib/modules/2.6.15-26-386/build M=/usr/src/modules/ivtv/driver clean
make[2]: Entering directory `/usr/src/linux-headers-2.6.15-26-386'
  CLEAN   /usr/src/modules/ivtv/driver/.tmp_versions
make[2]: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'
rm -f ivtv-svnversion.h ivtv-svnversion.h.tmp
make[1]: Leaving directory `/usr/src/modules/ivtv/driver'
/usr/bin/make KVER=2.6.15-26-386 KDIR=/lib/modules/2.6.15-26-386/build HP_FWLOAD=1 DEBIAN_MAKE_KPKG=1 -C i2c-drivers clean
make[1]: Entering directory `/usr/src/modules/ivtv/i2c-drivers'
/usr/bin/make -C /lib/modules/2.6.15-26-386/build M=/usr/src/modules/ivtv/i2c-drivers clean
make[2]: Entering directory `/usr/src/linux-headers-2.6.15-26-386'
make[2]: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'
make[1]: Leaving directory `/usr/src/modules/ivtv/i2c-drivers'
/usr/bin/make  -f debian/rules kdist_clean kdist_config binary-modules
sh: gcc-4.0: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
make[1]: Entering directory `/usr/src/modules/ivtv'
dh_clean
/usr/bin/make KVER=2.6.15-26-386 KDIR=/lib/modules/2.6.15-26-386/build HP_FWLOAD=1 DEBIAN_MAKE_KPKG=1 -C driver clean
make[2]: Entering directory `/usr/src/modules/ivtv/driver'
/usr/bin/make -C /lib/modules/2.6.15-26-386/build M=/usr/src/modules/ivtv/driver clean
make[3]: Entering directory `/usr/src/linux-headers-2.6.15-26-386'
make[3]: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'
rm -f ivtv-svnversion.h ivtv-svnversion.h.tmp
make[2]: Leaving directory `/usr/src/modules/ivtv/driver'
/usr/bin/make KVER=2.6.15-26-386 KDIR=/lib/modules/2.6.15-26-386/build HP_FWLOAD=1 DEBIAN_MAKE_KPKG=1 -C i2c-drivers clean
make[2]: Entering directory `/usr/src/modules/ivtv/i2c-drivers'
/usr/bin/make -C /lib/modules/2.6.15-26-386/build M=/usr/src/modules/ivtv/i2c-drivers clean
make[3]: Entering directory `/usr/src/linux-headers-2.6.15-26-386'
make[3]: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'
make[2]: Leaving directory `/usr/src/modules/ivtv/i2c-drivers'
[H[2J

The required compiler gcc-4.0 is not installed, expect trouble!


for templ in ; do \
    cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.15-26-386/g'` ; \
  done
for templ in `ls debian/*.modules.in` ; do \
    test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in} ${templ%.modules.in}.backup 2>/dev/null || true; \
    sed -e 's/##KVERS##/2.6.15-26-386/g ;s/#KVERS#/2.6.15-26-386/g ; s/_KVERS_/2.6.15-26-386/g ; s/##KDREV##/2.6.15-26.47/g ; s/#KDREV#/2.6.15-26.47/g ; s/_KDREV_/2.6.15-26.47/g  ' < $templ > ${templ%.modules.in}; \
  done
dh_testdir
dh_testroot
dh_clean -k
/usr/bin/make KVER=2.6.15-26-386 KDIR=/lib/modules/2.6.15-26-386/build HP_FWLOAD=1 DEBIAN_MAKE_KPKG=1 -C driver
make[2]: Entering directory `/usr/src/modules/ivtv/driver'
created ivtv-svnversion.h
/usr/bin/make -C /lib/modules/2.6.15-26-386/build M=/usr/src/modules/ivtv/driver KERNELRELEASE=2.6.15-26-386 modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.15-26-386'
  CC [M]  /usr/src/modules/ivtv/driver/ivtv-osd.o
  CC [M]  /usr/src/modules/ivtv/driver/ivtv-queue.o
  CC [M]  /usr/src/modules/ivtv/driver/ivtv-driver.o
In file included from /usr/src/modules/ivtv/driver/ivtv-driver.c:59:
/usr/src/modules/ivtv/driver/ivtv-audio.h:21: warning: â€˜struct v4l2_routingâ€™ declared inside parameter list
/usr/src/modules/ivtv/driver/ivtv-audio.h:21: warning: its scope is only this definition or declaration, which is probably not what you want
/usr/src/modules/ivtv/driver/ivtv-driver.c: In function â€˜ivtv_parse_stdâ€™:
/usr/src/modules/ivtv/driver/ivtv-driver.c:619: error: â€˜V4L2_STD_NTSC_M_KRâ€™ undeclared (first use in this function)
/usr/src/modules/ivtv/driver/ivtv-driver.c:619: error: (Each undeclared identifier is reported only once
/usr/src/modules/ivtv/driver/ivtv-driver.c:619: error: for each function it appears in.)
/usr/src/modules/ivtv/driver/ivtv-driver.c: In function â€˜ivtv_probeâ€™:
/usr/src/modules/ivtv/driver/ivtv-driver.c:1395: warning: implicit declaration of function â€˜TDA9887_TOPâ€™
/usr/src/modules/ivtv/driver/ivtv-driver.c:1411: error: â€˜TUNER_PANASONIC_VP27â€™ undeclared (first use in this function)
make[4]: *** [/usr/src/modules/ivtv/driver/ivtv-driver.o] Error 1
make[3]: *** [_module_/usr/src/modules/ivtv/driver] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/usr/src/modules/ivtv/driver'
make[1]: *** [binary-modules] Error 2
make[1]: Leaving directory `/usr/src/modules/ivtv'
make: *** [kdist_build] Error 2
```

I'm stuck at this point. Any Ideas?

Thanks

---

### Post by barney_1 on 2007-03-18
I would give the Edgy community pages a try:

[https://help.ubuntu.com/community/Install_IVTV_Edgy](https://help.ubuntu.com/community/Install_IVTV_Edgy)

Worked like a charm for me.

---

### Post by majoridiot on 2007-03-19
> **barney_1 said:**
> I would give the Edgy community pages a try:

[https://help.ubuntu.com/community/Install_IVTV_Edgy](https://help.ubuntu.com/community/Install_IVTV_Edgy)

Worked like a charm for me.

agreed.  that guide has never failed me on dapper, edgy and feisty.

---

