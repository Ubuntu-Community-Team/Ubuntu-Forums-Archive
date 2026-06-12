---
title: "IVTV on Ubuntu Edgy"
date: 2007-03-09
forum: Multimedia &amp; Video
---

### Post by ravalox on 2007-03-09
[https://help.ubuntu.com/community/Install_IVTV_Edgy#head-9d062fae8631f715fb10eb73624cae061fe61f69](https://help.ubuntu.com/community/Install_IVTV_Edgy#head-9d062fae8631f715fb10eb73624cae061fe61f69)

I am trying to follow the above instructions and I get a compile error on ivtv:
```
dh_clean
/usr/bin/make KVER=2.6.17-11-generic KDIR=/usr/src/linux-OLDVERSION.1173490828 HP_FWLOAD=1 DEBIAN_MAKE_KPKG=1 -C driver clean
make[1]: Entering directory `/usr/src/modules/ivtv/driver'
/usr/bin/make -C /usr/src/linux-OLDVERSION.1173490828 M=/usr/src/modules/ivtv/driver clean
make[2]: Entering directory `/usr/src/linux-source-2.6.17'
  CLEAN   /usr/src/modules/ivtv/driver/.tmp_versions
make[2]: Leaving directory `/usr/src/linux-source-2.6.17'
rm -f ivtv-svnversion.h ivtv-svnversion.h.tmp
make[1]: Leaving directory `/usr/src/modules/ivtv/driver'
/usr/bin/make KVER=2.6.17-11-generic KDIR=/usr/src/linux-OLDVERSION.1173490828 HP_FWLOAD=1 DEBIAN_MAKE_KPKG=1 -C i2c-drivers clean
make[1]: Entering directory `/usr/src/modules/ivtv/i2c-drivers'
/usr/bin/make -C /usr/src/linux-OLDVERSION.1173490828 M=/usr/src/modules/ivtv/i2c-drivers clean
make[2]: Entering directory `/usr/src/linux-source-2.6.17'
make[2]: Leaving directory `/usr/src/linux-source-2.6.17'
make[1]: Leaving directory `/usr/src/modules/ivtv/i2c-drivers'
/usr/bin/make  -f debian/rules kdist_clean kdist_config binary-modules
make[1]: Entering directory `/usr/src/modules/ivtv'
dh_clean
/usr/bin/make KVER=2.6.17-11-generic KDIR=/usr/src/linux-OLDVERSION.1173490828 HP_FWLOAD=1 DEBIAN_MAKE_KPKG=1 -C driver clean
make[2]: Entering directory `/usr/src/modules/ivtv/driver'
/usr/bin/make -C /usr/src/linux-OLDVERSION.1173490828 M=/usr/src/modules/ivtv/driver clean
make[3]: Entering directory `/usr/src/linux-source-2.6.17'
make[3]: Leaving directory `/usr/src/linux-source-2.6.17'
rm -f ivtv-svnversion.h ivtv-svnversion.h.tmp
make[2]: Leaving directory `/usr/src/modules/ivtv/driver'
/usr/bin/make KVER=2.6.17-11-generic KDIR=/usr/src/linux-OLDVERSION.1173490828 HP_FWLOAD=1 DEBIAN_MAKE_KPKG=1 -C i2c-drivers clean
make[2]: Entering directory `/usr/src/modules/ivtv/i2c-drivers'
/usr/bin/make -C /usr/src/linux-OLDVERSION.1173490828 M=/usr/src/modules/ivtv/i2c-drivers clean
make[3]: Entering directory `/usr/src/linux-source-2.6.17'
make[3]: Leaving directory `/usr/src/linux-source-2.6.17'
make[2]: Leaving directory `/usr/src/modules/ivtv/i2c-drivers'
/usr/bin/gcc
for templ in ; do \
    cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.17-11-generic/g'` ; \
  done
for templ in `ls debian/*.modules.in` ; do \
    test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in} ${templ%.modules.in}.backup 2>/dev/null || true; \
    sed -e 's/##KVERS##/2.6.17-11-generic/g ;s/#KVERS#/2.6.17-11-generic/g ; s/_KVERS_/2.6.17-11-generic/g ; s/##KDREV##/2.6.17.1-11.35/g ; s/#KDREV#/2.6.17.1-11.35/g ; s/_KDREV_/2.6.17.1-11.35/g  ' < $templ > ${templ%.modules.in}; \
  done
dh_testdir
dh_testroot
dh_clean -k
/usr/bin/make KVER=2.6.17-11-generic KDIR=/usr/src/linux-OLDVERSION.1173490828 HP_FWLOAD=1 DEBIAN_MAKE_KPKG=1 -C driver
make[2]: Entering directory `/usr/src/modules/ivtv/driver'
created ivtv-svnversion.h
/usr/bin/make -C /usr/src/linux-OLDVERSION.1173490828 M=/usr/src/modules/ivtv/driver KERNELRELEASE=2.6.17-11-generic modules
make[3]: Entering directory `/usr/src/linux-source-2.6.17'

  WARNING: Symbol version dump /usr/src/linux-source-2.6.17/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /usr/src/modules/ivtv/driver/ivtv-osd.o
  CC [M]  /usr/src/modules/ivtv/driver/ivtv-queue.o
  CC [M]  /usr/src/modules/ivtv/driver/ivtv-driver.o
/bin/sh: scripts/genksyms/genksyms: not found
make[4]: *** [/usr/src/modules/ivtv/driver/ivtv-driver.o] Error 127
make[3]: *** [_module_/usr/src/modules/ivtv/driver] Error 2
make[3]: Leaving directory `/usr/src/linux-source-2.6.17'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/usr/src/modules/ivtv/driver'
make[1]: *** [binary-modules] Error 2
make[1]: Leaving directory `/usr/src/modules/ivtv'
make: *** [kdist_build] Error 2

```

Anyone have any notions as to why this is happening?

---

### Post by superm1 on 2007-03-10
> **ravalox said:**
> [https://help.ubuntu.com/community/Install_IVTV_Edgy#head-9d062fae8631f715fb10eb73624cae061fe61f69](https://help.ubuntu.com/community/Install_IVTV_Edgy#head-9d062fae8631f715fb10eb73624cae061fe61f69)

I am trying to follow the above instructions and I get a compile error on ivtv:
```
dh_clean
/usr/bin/make KVER=2.6.17-11-generic KDIR=/usr/src/linux-OLDVERSION.1173490828 HP_FWLOAD=1 DEBIAN_MAKE_KPKG=1 -C driver clean
make[1]: Entering directory `/usr/src/modules/ivtv/driver'
/usr/bin/make -C /usr/src/linux-OLDVERSION.1173490828 M=/usr/src/modules/ivtv/driver clean
make[2]: Entering directory `/usr/src/linux-source-2.6.17'
  CLEAN   /usr/src/modules/ivtv/driver/.tmp_versions
make[2]: Leaving directory `/usr/src/linux-source-2.6.17'
rm -f ivtv-svnversion.h ivtv-svnversion.h.tmp
make[1]: Leaving directory `/usr/src/modules/ivtv/driver'
/usr/bin/make KVER=2.6.17-11-generic KDIR=/usr/src/linux-OLDVERSION.1173490828 HP_FWLOAD=1 DEBIAN_MAKE_KPKG=1 -C i2c-drivers clean
make[1]: Entering directory `/usr/src/modules/ivtv/i2c-drivers'
/usr/bin/make -C /usr/src/linux-OLDVERSION.1173490828 M=/usr/src/modules/ivtv/i2c-drivers clean
make[2]: Entering directory `/usr/src/linux-source-2.6.17'
make[2]: Leaving directory `/usr/src/linux-source-2.6.17'
make[1]: Leaving directory `/usr/src/modules/ivtv/i2c-drivers'
/usr/bin/make  -f debian/rules kdist_clean kdist_config binary-modules
make[1]: Entering directory `/usr/src/modules/ivtv'
dh_clean
/usr/bin/make KVER=2.6.17-11-generic KDIR=/usr/src/linux-OLDVERSION.1173490828 HP_FWLOAD=1 DEBIAN_MAKE_KPKG=1 -C driver clean
make[2]: Entering directory `/usr/src/modules/ivtv/driver'
/usr/bin/make -C /usr/src/linux-OLDVERSION.1173490828 M=/usr/src/modules/ivtv/driver clean
make[3]: Entering directory `/usr/src/linux-source-2.6.17'
make[3]: Leaving directory `/usr/src/linux-source-2.6.17'
rm -f ivtv-svnversion.h ivtv-svnversion.h.tmp
make[2]: Leaving directory `/usr/src/modules/ivtv/driver'
/usr/bin/make KVER=2.6.17-11-generic KDIR=/usr/src/linux-OLDVERSION.1173490828 HP_FWLOAD=1 DEBIAN_MAKE_KPKG=1 -C i2c-drivers clean
make[2]: Entering directory `/usr/src/modules/ivtv/i2c-drivers'
/usr/bin/make -C /usr/src/linux-OLDVERSION.1173490828 M=/usr/src/modules/ivtv/i2c-drivers clean
make[3]: Entering directory `/usr/src/linux-source-2.6.17'
make[3]: Leaving directory `/usr/src/linux-source-2.6.17'
make[2]: Leaving directory `/usr/src/modules/ivtv/i2c-drivers'
/usr/bin/gcc
for templ in ; do \
    cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.17-11-generic/g'` ; \
  done
for templ in `ls debian/*.modules.in` ; do \
    test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in} ${templ%.modules.in}.backup 2>/dev/null || true; \
    sed -e 's/##KVERS##/2.6.17-11-generic/g ;s/#KVERS#/2.6.17-11-generic/g ; s/_KVERS_/2.6.17-11-generic/g ; s/##KDREV##/2.6.17.1-11.35/g ; s/#KDREV#/2.6.17.1-11.35/g ; s/_KDREV_/2.6.17.1-11.35/g  ' < $templ > ${templ%.modules.in}; \
  done
dh_testdir
dh_testroot
dh_clean -k
/usr/bin/make KVER=2.6.17-11-generic KDIR=/usr/src/linux-OLDVERSION.1173490828 HP_FWLOAD=1 DEBIAN_MAKE_KPKG=1 -C driver
make[2]: Entering directory `/usr/src/modules/ivtv/driver'
created ivtv-svnversion.h
/usr/bin/make -C /usr/src/linux-OLDVERSION.1173490828 M=/usr/src/modules/ivtv/driver KERNELRELEASE=2.6.17-11-generic modules
make[3]: Entering directory `/usr/src/linux-source-2.6.17'

  WARNING: Symbol version dump /usr/src/linux-source-2.6.17/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /usr/src/modules/ivtv/driver/ivtv-osd.o
  CC [M]  /usr/src/modules/ivtv/driver/ivtv-queue.o
  CC [M]  /usr/src/modules/ivtv/driver/ivtv-driver.o
/bin/sh: scripts/genksyms/genksyms: not found
make[4]: *** [/usr/src/modules/ivtv/driver/ivtv-driver.o] Error 127
make[3]: *** [_module_/usr/src/modules/ivtv/driver] Error 2
make[3]: Leaving directory `/usr/src/linux-source-2.6.17'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/usr/src/modules/ivtv/driver'
make[1]: *** [binary-modules] Error 2
make[1]: Leaving directory `/usr/src/modules/ivtv'
make: *** [kdist_build] Error 2

```Anyone have any notions as to why this is happening?
At a glance, it appears that you didn't do 
```
sudo m-a update,prepare
```
Since its using 
```
/usr/src/linux-OLDVERSION.1173490828
```

---

