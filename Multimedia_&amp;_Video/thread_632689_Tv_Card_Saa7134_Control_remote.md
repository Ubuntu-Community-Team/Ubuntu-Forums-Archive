---
title: "Tv Card Saa7134 Control remote"
date: 2007-12-05
forum: Multimedia &amp; Video
---

### Post by Mariog123 on 2007-12-05
I am trying to operate the remote control. I try to compile the lirc. The error is as follows:

/usr/src/lirc-0.8.1pre2$ sudo make
make  all-recursive
make[1]: se ingresa al directorio `/usr/src/lirc-0.8.1pre2'
Making all in drivers
make[2]: se ingresa al directorio `/usr/src/lirc-0.8.1pre2/drivers'
Making all in lirc_dev
make[3]: se ingresa al directorio `/usr/src/lirc-0.8.1pre2/drivers/lirc_dev'
Makefile:8: **************************************************
Makefile:8: *** Makefile trick not undone, trying to recover *
Makefile:8: **************************************************
mv Makefile.automake Makefile
make all
make[4]: se ingresa al directorio `/usr/src/lirc-0.8.1pre2/drivers/lirc_dev'
mv Makefile Makefile.automake
cp ../Makefile.kernel Makefile
make -C /lib/modules/2.6.22-14-generic/build/ SUBDIRS=/usr/src/lirc-0.8.1pre2/drivers/lirc_dev modules \
                KBUILD_VERBOSE=1
make[5]: se ingresa al directorio `/usr/src/linux-headers-2.6.22-14-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (            \
        echo;                                                           \
        echo "  ERROR: Kernel configuration is invalid.";               \
        echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";      \
        echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";  \
        echo;                                                           \
        /bin/false)
mkdir -p /usr/src/lirc-0.8.1pre2/drivers/lirc_dev/.tmp_versions
rm -f /usr/src/lirc-0.8.1pre2/drivers/lirc_dev/.tmp_versions/* 
make -f scripts/Makefile.build obj=/usr/src/lirc-0.8.1pre2/drivers/lirc_dev
  gcc -m32 -Wp,-MD,/usr/src/lirc-0.8.1pre2/drivers/lirc_dev/.lirc_dev.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.3/include -D__KERNEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-i386/mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign -DIRCTL_DEV_MAJOR=61 -DEXPORT_SYMTAB -DHAVE_CONFIG_H -I. -I. -I../.. -I/usr/src/lirc- 0.8.1pre2/drivers/lirc_dev/../.. -I/lib/modules/2.6.22-14-generic/build//include/ -I/lib/modules/2.6.22-14-generic/build//drivers/media/video/  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(lirc_dev)"  -D"KBUILD_MODNAME=KBUILD_STR(lirc_dev)" -c -o /usr/src/lirc- 0.8.1pre2/drivers/lirc_dev/.tmp_lirc_dev.o /usr/src/lirc-0.8.1pre2/drivers/lirc_dev/lirc_dev.c
/usr/src/lirc-0.8.1pre2/drivers/lirc_dev/lirc_dev.c:35:26: error: linux/config.h: No existe el fichero ó directorio
make[6]: *** [/usr/src/lirc-0.8.1pre2/drivers/lirc_dev/lirc_dev.o] Error 1
make[5]: *** [_module_/usr/src/lirc-0.8.1pre2/drivers/lirc_dev] Error 2
make[5]: se sale del directorio `/usr/src/linux-headers-2.6.22-14-generic'
make[4]: *** [lirc_dev.o] Error 2
make[4]: se sale del directorio `/usr/src/lirc-0.8.1pre2/drivers/lirc_dev'
make[3]: *** [all] Error 2
make[3]: se sale del directorio `/usr/src/lirc-0.8.1pre2/drivers/lirc_dev'
make[2]: *** [all-recursive] Error 1
make[2]: se sale del directorio `/usr/src/lirc-0.8.1pre2/drivers'
make[1]: *** [all-recursive] Error 1
make[1]: se sale del directorio `/usr/src/lirc-0.8.1pre2'
make: *** [all] Error 2

/usr/src/lirc-0.8.1pre2$ sudo make oldconfig && make prepare
make: *** No hay ninguna regla para construir el objetivo `oldconfig'.  Alto.

But, I don't unerstand what happened
Help, please, help... mi card is compatible with card: 3, 13, 30, or 35, the is tuner: 39

Thans, very thanks

---

### Post by ariel on 2007-12-08
I have an SAA7134 and could make the remote work fine without compiling sources.

I posted a "mini howto" describing what I did and pointing to resources.

You can find it here:

**[SIZE=2] 	LIRC for Compro VIdeoMate TV PVR - Resources to set it up[/SIZE]**

[http://ubuntuforums.org/showthread.php?p=3916602#post3916602](http://ubuntuforums.org/showthread.php?p=3916602#post3916602)

---

