---
title: "Lirc-modules-source installation problem"
date: 2010-08-29
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by songochain on 2010-08-29
Hi, I'm trying to install lirc-modules-source but I get this error:
> Removing old lirc-0.8.7~pre2 DKMS files...

------------------------------
Deleting module version: 0.8.7~pre2
completely from the DKMS tree.
------------------------------
Done.
Loading new lirc-0.8.7~pre2 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.35-19-generic
Building for architecture x86_64
Building initial module for 2.6.35-19-generic

Error! Bad return status for module build on kernel: 2.6.35-19-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/lirc/0.8.7~pre2/build/ for more information.
dpkg: error al procesar lirc-modules-source (--configure):
 el subproceso script post-installation instalado devolvió el código de salida de error 10
Se encontraron errores al procesar:
 lirc-modules-source
E: Sub-process /usr/bin/dpkg returned an error code (1)
Is there someone with this problem too?

Thanks.

BR.

---

### Post by cariboo on 2010-08-29
What does the log entry in /var/lib/dkms/lirc/0.8.7~pre2/build say?

---

### Post by songochain on 2010-08-29
> **cariboo907 said:**
> What does the log entry in /var/lib/dkms/lirc/0.8.7~pre2/build say?
Here's:

> 
DKMS make.log for lirc-0.8.7~pre2 for kernel 2.6.35-19-generic (x86_64)
dom ago 29 21:52:09 CEST 2010
mkdir modules
make -C drivers SUBDIRS="lirc_dev"
make[1]: se ingresa al directorio `/var/lib/dkms/lirc/0.8.7~pre2/build/drivers'
Making all in lirc_dev
make[2]: se ingresa al directorio `/var/lib/dkms/lirc/0.8.7~pre2/build/drivers/lirc_dev'
cp ./../lirc_dev/Module*.symvers .
cp: no se puede efectuar «stat» sobre «./../lirc_dev/Module*.symvers»: No existe el archivo o directorio
make[2]: [lirc_dev.o] Error 1 (no tiene efecto)
mv Makefile Makefile.automake
cp ./../Makefile.kernel Makefile
CPPFLAGS="" CFLAGS="" LDFLAGS="" \
    make -C /lib/modules/2.6.35-19-generic/build SUBDIRS=/var/lib/dkms/lirc/0.8.7~pre2/build/drivers/lirc_dev modules \
        KBUILD_VERBOSE=1
make[3]: se ingresa al directorio `/usr/src/linux-headers-2.6.35-19-generic'
test -e include/generated/autoconf.h -a -e include/config/auto.conf || (        \
    echo;                                \
    echo "  ERROR: Kernel configuration is invalid.";        \
    echo "         include/generated/autoconf.h or include/config/auto.conf are missing.";\
    echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";    \
    echo;                                \
    /bin/false)
mkdir -p /var/lib/dkms/lirc/0.8.7~pre2/build/drivers/lirc_dev/.tmp_versions ; rm -f /var/lib/dkms/lirc/0.8.7~pre2/build/drivers/lirc_dev/.tmp_versions/*
make -f scripts/Makefile.build obj=/var/lib/dkms/lirc/0.8.7~pre2/build/drivers/lirc_dev
  gcc -Wp,-MD,/var/lib/dkms/lirc/0.8.7~pre2/build/drivers/lirc_dev/.lirc_dev.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.5/include  -I/usr/src/linux-headers-2.6.35-19-generic/arch/x86/include -Iinclude  -include include/generated/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DIRCTL_DEV_MAJOR=61 -DEXPORT_SYMTAB -DHAVE_CONFIG_H -I. -I../.. -I/var/lib/dkms/lirc/0.8.7~pre2/build/drivers/lirc_dev/. -I/var/lib/dkms/lirc/0.8.7~pre2/build/drivers/lirc_dev/. -I/var/lib/dkms/lirc/0.8.7~pre2/build/drivers/lirc_dev/../.. -I/var/lib/dkms/lirc/0.8.7~pre2/build/drivers/lirc_dev/../.. -I/lib/modules/2.6.35-19-generic/build/include/ -I/lib/modules/2.6.35-19-generic/build/drivers/media/video/  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(lirc_dev)"  -D"KBUILD_MODNAME=KBUILD_STR(lirc_dev)"  -c -o /var/lib/dkms/lirc/0.8.7~pre2/build/drivers/lirc_dev/.tmp_lirc_dev.o /var/lib/dkms/lirc/0.8.7~pre2/build/drivers/lirc_dev/lirc_dev.c
In file included from /var/lib/dkms/lirc/0.8.7~pre2/build/drivers/lirc_dev/lirc_dev.c:73:
/var/lib/dkms/lirc/0.8.7~pre2/build/drivers/lirc_dev/../../drivers/lirc.h:14: fatal error: stdint.h: No existe el archivo o directorio
compilation terminated.
make[4]: *** [/var/lib/dkms/lirc/0.8.7~pre2/build/drivers/lirc_dev/lirc_dev.o] Error 1
make[3]: *** [_module_/var/lib/dkms/lirc/0.8.7~pre2/build/drivers/lirc_dev] Error 2
make[3]: se sale del directorio `/usr/src/linux-headers-2.6.35-19-generic'
make[2]: *** [lirc_dev.o] Error 2
make[2]: se sale del directorio `/var/lib/dkms/lirc/0.8.7~pre2/build/drivers/lirc_dev'
make[1]: *** [all-recursive] Error 1
make[1]: se sale del directorio `/var/lib/dkms/lirc/0.8.7~pre2/build/drivers'
make: *** [dev] Error 2

Thank you 
Br.

---

### Post by cariboo on 2010-08-29
Install build-essentials and try installing the module again.

---

### Post by songochain on 2010-08-30
> **cariboo907 said:**
> Install build-essentials and try installing the module again.
I doesn't work :S Same error...

---

### Post by songochain on 2010-08-31
up!

---

