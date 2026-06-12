---
title: "Need help making lirc modules in 7.10 &#8220;Gutsy&#8221;"
date: 2007-10-19
forum: Multimedia &amp; Video
---

### Post by Akriss on 2007-10-19
Hello. 

I finally have run in to a problem that searching through the forums has not provided an answer for.

I&#8217; am trying to build lirc kernel modules for my Hauppauge pvr 150 in 7.10 &#8220;Gusty&#8221; to enable blaster support. I&#8217; am following  the guide for 7.04 Feisty because the 7.10 &#8220;Gusty&#8221; lirc guide does not cover module building. However I&#8217; am running in to some trouble and need a little bit of help.

When I first ran ( sudo m-a a-i -f lirc ) I received an error of:


```
 
sed -e "s!\$KVERS!`sed -n -e '/UTS_RELEASE/s/^[^"]*"\([^"]*\)".*$/\1/p' /usr/src/linux/include/linux/version.h`!g; s!\$KSRC!/usr/src/linux!; s!\$KARCH!i386!; s!\$KEMAIL!!; s!\$KMAINT!!; s!\$KDREV!"Custom.1.00"!; s!\$DEBDATE!Fri, 19 Oct 2007 14:57:53 -0400!" debian/control.in > debian/control
/usr/bin/make  -f debian/rules clean
make[1]: Entering directory `/usr/src/modules/lirc'
dh_testdir
dh_testroot
rm -f build-stamp configure-stamp
# Add here commands to clean up after the build process.
/usr/bin/make clean
make[2]: Entering directory `/usr/src/modules/lirc'
/usr/bin/make clean -C drivers SUBDIRS="lirc_atiusb lirc_bt829 lirc_cmdir lirc_gpio lirc_i2c lirc_igorplugusb lirc_imon lirc_it87 lirc_mceusb lirc_mceusb2 lirc_parallel lirc_pvr150 lirc_sasem lirc_serial lirc_sir lirc_streamzap"
make[3]: Entering directory `/usr/src/modules/lirc/drivers'
Making clean in lirc_streamzap
make[4]: Entering directory `/usr/src/modules/lirc/drivers/lirc_streamzap'
test -z "lirc_streamzap.o .lirc_streamzap.o.flags lirc_streamzap.mod.c lirc_streamzap.ko *~" || rm -f lirc_streamzap.o .lirc_streamzap.o.flags lirc_streamzap.mod.c lirc_streamzap.ko *~
rm -rf .libs _libs
rm -f *.o core *.core
rm -f *.lo
make[4]: Leaving directory `/usr/src/modules/lirc/drivers/lirc_streamzap'
Making clean in lirc_sir
make[4]: Entering directory `/usr/src/modules/lirc/drivers/lirc_sir'
test -z "lirc_sir.o .lirc_sir.o.flags lirc_sir.mod.c lirc_sir.ko *~" || rm -f lirc_sir.o .lirc_sir.o.flags lirc_sir.mod.c lirc_sir.ko *~
rm -rf .libs _libs
rm -f *.o core *.core
rm -f *.lo
make[4]: Leaving directory `/usr/src/modules/lirc/drivers/lirc_sir'
Making clean in lirc_serial
make[4]: Entering directory `/usr/src/modules/lirc/drivers/lirc_serial'
test -z "lirc_serial.o .lirc_serial.o.flags lirc_serial.mod.c lirc_serial.ko *~" || rm -f lirc_serial.o .lirc_serial.o.flags lirc_serial.mod.c lirc_serial.ko *~
rm -rf .libs _libs
rm -f *.o core *.core
rm -f *.lo
make[4]: Leaving directory `/usr/src/modules/lirc/drivers/lirc_serial'
Making clean in lirc_sasem
make[4]: Entering directory `/usr/src/modules/lirc/drivers/lirc_sasem'
test -z "lirc_sasem.o .lirc_sasem.o.flags lirc_sasem.mod.c lirc_sasem.ko *~" || rm -f lirc_sasem.o .lirc_sasem.o.flags lirc_sasem.mod.c lirc_sasem.ko *~
rm -rf .libs _libs
rm -f *.o core *.core
rm -f *.lo
make[4]: Leaving directory `/usr/src/modules/lirc/drivers/lirc_sasem'
Making clean in lirc_pvr150
make[4]: Entering directory `/usr/src/modules/lirc/drivers/lirc_pvr150'
make[4]: Leaving directory `/usr/src/modules/lirc/drivers/lirc_pvr150'
make[3]: Leaving directory `/usr/src/modules/lirc/drivers'
make[2]: Leaving directory `/usr/src/modules/lirc'
dh_clean
rm -f debian/control
make[1]: Leaving directory `/usr/src/modules/lirc'
/usr/bin/make  -f debian/rules binary-modules
make[1]: Entering directory `/usr/src/modules/lirc'
sed -e "s!\$KVERS!2.6.22-14-generic!g; s!\$KSRC!/usr/src/linux-headers-2.6.22-14-generic!; s!\$KARCH!i386!; s!\$KEMAIL!!; s!\$KMAINT!!; s!\$KDREV!2.6.22-14.46!; s!\$DEBDATE!Fri, 19 Oct 2007 14:57:53 -0400!" debian/control.in > debian/control
dh_testdir
# Add here commands to configure the package.
touch configure-stamp
dh_testdir
# Add here commands to compile the package.
/usr/bin/make debconf
make[2]: Entering directory `/usr/src/modules/lirc'
mkdir modules
/usr/bin/make -C drivers SUBDIRS="lirc_dev"
make[3]: Entering directory `/usr/src/modules/lirc/drivers'
Making all in lirc_dev
make[4]: Entering directory `/usr/src/modules/lirc/drivers/lirc_dev'
mv Makefile Makefile.automake
cp ../Makefile.kernel Makefile
/usr/bin/make -C /usr/src/linux-headers-2.6.22-14-generic SUBDIRS=/usr/src/modules/lirc/drivers/lirc_dev modules \
		KBUILD_VERBOSE=1
make[5]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /usr/src/modules/lirc/drivers/lirc_dev/.tmp_versions
rm -f /usr/src/modules/lirc/drivers/lirc_dev/.tmp_versions/*
/usr/bin/make -f scripts/Makefile.build obj=/usr/src/modules/lirc/drivers/lirc_dev
  gcc -m32 -Wp,-MD,/usr/src/modules/lirc/drivers/lirc_dev/.lirc_dev.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.3/include -D__KERNEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-i386/mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign -DIRCTL_DEV_MAJOR=61 -DEXPORT_SYMTAB -DHAVE_CONFIG_H -I. -I. -I../.. -I/usr/src/modules/lirc/drivers/lirc_dev/../.. -I/usr/src/linux-headers-2.6.22-14-generic/include/ -I/usr/src/linux-headers-2.6.22-14-generic/drivers/media/video/  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(lirc_dev)"  -D"KBUILD_MODNAME=KBUILD_STR(lirc_dev)" -c -o /usr/src/modules/lirc/drivers/lirc_dev/.tmp_lirc_dev.o /usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.c
  Building modules, stage 2.
/usr/bin/make -f /usr/src/linux-headers-2.6.22-14-generic/scripts/Makefile.modpost
  scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.22-14-generic/Module.symvers -I /usr/src/modules/lirc/drivers/lirc_dev/Module.symvers -o /usr/src/modules/lirc/drivers/lirc_dev/Module.symvers -w
  gcc -m32 -Wp,-MD,/usr/src/modules/lirc/drivers/lirc_dev/.lirc_dev.mod.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.3/include -D__KERNEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-i386/mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign    -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(lirc_dev.mod)"  -D"KBUILD_MODNAME=KBUILD_STR(lirc_dev)" -DMODULE -c -o /usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.mod.o /usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.mod.c
  ld -m elf_i386 -m elf_i386 -r -o /usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.ko /usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.o /usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.mod.o
make[5]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
mv Makefile.automake Makefile
make[4]: Leaving directory `/usr/src/modules/lirc/drivers/lirc_dev'
make[4]: Entering directory `/usr/src/modules/lirc/drivers'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/usr/src/modules/lirc/drivers'
make[3]: Leaving directory `/usr/src/modules/lirc/drivers'
cp drivers/lirc_dev/lirc_dev.ko modules
/usr/bin/make -C drivers SUBDIRS="lirc_i2c"
make[3]: Entering directory `/usr/src/modules/lirc/drivers'
Making all in lirc_i2c
make[4]: Entering directory `/usr/src/modules/lirc/drivers/lirc_i2c'
mv Makefile Makefile.automake
cp ../Makefile.kernel Makefile
/usr/bin/make -C /usr/src/linux-headers-2.6.22-14-generic SUBDIRS=/usr/src/modules/lirc/drivers/lirc_i2c modules \
		KBUILD_VERBOSE=1
make[5]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /usr/src/modules/lirc/drivers/lirc_i2c/.tmp_versions
rm -f /usr/src/modules/lirc/drivers/lirc_i2c/.tmp_versions/*
/usr/bin/make -f scripts/Makefile.build obj=/usr/src/modules/lirc/drivers/lirc_i2c
  gcc -m32 -Wp,-MD,/usr/src/modules/lirc/drivers/lirc_i2c/.lirc_i2c.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.3/include -D__KERNEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-i386/mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign -DIRCTL_DEV_MAJOR=61 -DEXPORT_SYMTAB -DHAVE_CONFIG_H -I. -I. -I../.. -I/usr/src/modules/lirc/drivers/lirc_i2c/../.. -I/usr/src/linux-headers-2.6.22-14-generic/include/ -I/usr/src/linux-headers-2.6.22-14-generic/drivers/media/video/  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(lirc_i2c)"  -D"KBUILD_MODNAME=KBUILD_STR(lirc_i2c)" -c -o /usr/src/modules/lirc/drivers/lirc_i2c/.tmp_lirc_i2c.o /usr/src/modules/lirc/drivers/lirc_i2c/lirc_i2c.c
  Building modules, stage 2.
/usr/bin/make -f /usr/src/linux-headers-2.6.22-14-generic/scripts/Makefile.modpost
  scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.22-14-generic/Module.symvers -I /usr/src/modules/lirc/drivers/lirc_i2c/Module.symvers -o /usr/src/modules/lirc/drivers/lirc_i2c/Module.symvers -w
WARNING: "lirc_register_plugin" [/usr/src/modules/lirc/drivers/lirc_i2c/lirc_i2c.ko] undefined!
WARNING: "lirc_unregister_plugin" [/usr/src/modules/lirc/drivers/lirc_i2c/lirc_i2c.ko] undefined!
  gcc -m32 -Wp,-MD,/usr/src/modules/lirc/drivers/lirc_i2c/.lirc_i2c.mod.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.3/include -D__KERNEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-i386/mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign    -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(lirc_i2c.mod)"  -D"KBUILD_MODNAME=KBUILD_STR(lirc_i2c)" -DMODULE -c -o /usr/src/modules/lirc/drivers/lirc_i2c/lirc_i2c.mod.o /usr/src/modules/lirc/drivers/lirc_i2c/lirc_i2c.mod.c
  ld -m elf_i386 -m elf_i386 -r -o /usr/src/modules/lirc/drivers/lirc_i2c/lirc_i2c.ko /usr/src/modules/lirc/drivers/lirc_i2c/lirc_i2c.o /usr/src/modules/lirc/drivers/lirc_i2c/lirc_i2c.mod.o
make[5]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
mv Makefile.automake Makefile
make[4]: Leaving directory `/usr/src/modules/lirc/drivers/lirc_i2c'
make[4]: Entering directory `/usr/src/modules/lirc/drivers'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/usr/src/modules/lirc/drivers'
make[3]: Leaving directory `/usr/src/modules/lirc/drivers'
cp drivers/lirc_i2c/lirc_i2c.ko modules
/usr/bin/make -C drivers SUBDIRS="lirc_pvr150"
make[3]: Entering directory `/usr/src/modules/lirc/drivers'
Making all in lirc_pvr150
make[4]: Entering directory `/usr/src/modules/lirc/drivers/lirc_pvr150'
Makefile:185: *** missing separator.  Stop.
make[4]: Leaving directory `/usr/src/modules/lirc/drivers/lirc_pvr150'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/usr/src/modules/lirc/drivers'
make[2]: *** [pvr150] Error 2
make[2]: Leaving directory `/usr/src/modules/lirc'
make[1]: *** [build-stamp] Error 2
make[1]: Leaving directory `/usr/src/modules/lirc'
make: *** [kdist_image] Error 2

 
```


So the error seemed to indicate to me that I needed to run 'make oldconfig && make prepare'  and did so. And then re ran ( sudo m-a a-i -f lirc ) and received another error of:

```

 sed -e "s!\$KVERS!`sed -n -e '/UTS_RELEASE/s/^[^"]*"\([^"]*\)".*$/\1/p' /usr/src/linux/include/linux/version.h`!g; s!\$KSRC!/usr/src/linux!; s!\$KARCH!i386!; s!\$KEMAIL!!; s!\$KMAINT!!; s!\$KDREV!"Custom.1.00"!; s!\$DEBDATE!Fri, 19 Oct 2007 19:19:34 -0400!" debian/control.in > debian/control
/usr/bin/make  -f debian/rules clean
make[1]: Entering directory `/usr/src/modules/lirc'
dh_testdir
dh_testroot
rm -f build-stamp configure-stamp
# Add here commands to clean up after the build process.
/usr/bin/make clean
make[2]: Entering directory `/usr/src/modules/lirc'
/usr/bin/make clean -C drivers SUBDIRS="lirc_atiusb lirc_bt829 lirc_cmdir lirc_gpio lirc_i2c lirc_igorplugusb lirc_imon lirc_it87 lirc_mceusb lirc_mceusb2 lirc_parallel lirc_pvr150 lirc_sasem lirc_serial lirc_sir lirc_streamzap"
make[3]: Entering directory `/usr/src/modules/lirc/drivers'
Making clean in lirc_streamzap
make[4]: Entering directory `/usr/src/modules/lirc/drivers/lirc_streamzap'
test -z "lirc_streamzap.o .lirc_streamzap.o.flags lirc_streamzap.mod.c lirc_streamzap.ko *~" || rm -f lirc_streamzap.o .lirc_streamzap.o.flags lirc_streamzap.mod.c lirc_streamzap.ko *~
rm -rf .libs _libs
rm -f *.o core *.core
rm -f *.lo
make[4]: Leaving directory `/usr/src/modules/lirc/drivers/lirc_streamzap'
Making clean in lirc_sir
make[4]: Entering directory `/usr/src/modules/lirc/drivers/lirc_sir'
test -z "lirc_sir.o .lirc_sir.o.flags lirc_sir.mod.c lirc_sir.ko *~" || rm -f lirc_sir.o .lirc_sir.o.flags lirc_sir.mod.c lirc_sir.ko *~
rm -rf .libs _libs
rm -f *.o core *.core
rm -f *.lo
make[4]: Leaving directory `/usr/src/modules/lirc/drivers/lirc_sir'
Making clean in lirc_serial
make[4]: Entering directory `/usr/src/modules/lirc/drivers/lirc_serial'
test -z "lirc_serial.o .lirc_serial.o.flags lirc_serial.mod.c lirc_serial.ko *~" || rm -f lirc_serial.o .lirc_serial.o.flags lirc_serial.mod.c lirc_serial.ko *~
rm -rf .libs _libs
rm -f *.o core *.core
rm -f *.lo
make[4]: Leaving directory `/usr/src/modules/lirc/drivers/lirc_serial'
Making clean in lirc_sasem
make[4]: Entering directory `/usr/src/modules/lirc/drivers/lirc_sasem'
test -z "lirc_sasem.o .lirc_sasem.o.flags lirc_sasem.mod.c lirc_sasem.ko *~" || rm -f lirc_sasem.o .lirc_sasem.o.flags lirc_sasem.mod.c lirc_sasem.ko *~
rm -rf .libs _libs
rm -f *.o core *.core
rm -f *.lo
make[4]: Leaving directory `/usr/src/modules/lirc/drivers/lirc_sasem'
Making clean in lirc_pvr150
make[4]: Entering directory `/usr/src/modules/lirc/drivers/lirc_pvr150'
make[4]: Leaving directory `/usr/src/modules/lirc/drivers/lirc_pvr150'
make[3]: Leaving directory `/usr/src/modules/lirc/drivers'
make[2]: Leaving directory `/usr/src/modules/lirc'
dh_clean
rm -f debian/control
make[1]: Leaving directory `/usr/src/modules/lirc'
/usr/bin/make  -f debian/rules binary-modules
make[1]: Entering directory `/usr/src/modules/lirc'
sed -e "s!\$KVERS!2.6.22-14-generic!g; s!\$KSRC!/usr/src/linux-headers-2.6.22-14-generic!; s!\$KARCH!i386!; s!\$KEMAIL!!; s!\$KMAINT!!; s!\$KDREV!2.6.22-14.46!; s!\$DEBDATE!Fri, 19 Oct 2007 19:19:35 -0400!" debian/control.in > debian/control
dh_testdir
# Add here commands to configure the package.
touch configure-stamp
dh_testdir
# Add here commands to compile the package.
/usr/bin/make debconf
make[2]: Entering directory `/usr/src/modules/lirc'
/usr/bin/make -C drivers SUBDIRS="lirc_dev"
make[3]: Entering directory `/usr/src/modules/lirc/drivers'
Making all in lirc_dev
make[4]: Entering directory `/usr/src/modules/lirc/drivers/lirc_dev'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/usr/src/modules/lirc/drivers/lirc_dev'
make[4]: Entering directory `/usr/src/modules/lirc/drivers'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/usr/src/modules/lirc/drivers'
make[3]: Leaving directory `/usr/src/modules/lirc/drivers'
cp drivers/lirc_dev/lirc_dev.ko modules
/usr/bin/make -C drivers SUBDIRS="lirc_i2c"
make[3]: Entering directory `/usr/src/modules/lirc/drivers'
Making all in lirc_i2c
make[4]: Entering directory `/usr/src/modules/lirc/drivers/lirc_i2c'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/usr/src/modules/lirc/drivers/lirc_i2c'
make[4]: Entering directory `/usr/src/modules/lirc/drivers'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/usr/src/modules/lirc/drivers'
make[3]: Leaving directory `/usr/src/modules/lirc/drivers'
cp drivers/lirc_i2c/lirc_i2c.ko modules
/usr/bin/make -C drivers SUBDIRS="lirc_pvr150"
make[3]: Entering directory `/usr/src/modules/lirc/drivers'
Making all in lirc_pvr150
make[4]: Entering directory `/usr/src/modules/lirc/drivers/lirc_pvr150'
Makefile:185: *** missing separator.  Stop.
make[4]: Leaving directory `/usr/src/modules/lirc/drivers/lirc_pvr150'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/usr/src/modules/lirc/drivers'
make[2]: *** [pvr150] Error 2
make[2]: Leaving directory `/usr/src/modules/lirc'
make[1]: *** [build-stamp] Error 2
make[1]: Leaving directory `/usr/src/modules/lirc'
make: *** [kdist_image] Error 2
  
```

Now I&#8217; am stuck not knowing what exactly to do. I must say the lirc 7.04 Feisty guide is spot on and work great for me when I was using 7.04 Feisty. 

Thanks
Akriss

---

### Post by Akriss on 2007-10-20
I came upon this bit of info wile Googleing for an answer ( [https://launchpad.net/ubuntu/gutsy/+source/lirc/+changelog](https://launchpad.net/ubuntu/gutsy/+source/lirc/+changelog) )

So I 'am guessing its a known problem? and its on Superm1 list to be fixed.

Well if Superm1 is working on it, I know its in good hands and most likely be fixed when Mythbuntu final is out.

Thanks
Akriss

---

### Post by Anubis on 2008-01-08
> **Akriss said:**
> I came upon this bit of info wile Googleing for an answer ( [https://launchpad.net/ubuntu/gutsy/+source/lirc/+changelog](https://launchpad.net/ubuntu/gutsy/+source/lirc/+changelog) )

So I 'am guessing its a known problem? and its on Superm1 list to be fixed.

Well if Superm1 is working on it, I know its in good hands and most likely be fixed when Mythbuntu final is out.

Thanks
Akriss

Still broken in Hardy except for kernel 2.6.24.2.

---

