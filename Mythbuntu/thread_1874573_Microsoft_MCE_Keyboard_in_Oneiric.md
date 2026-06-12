---
title: "Microsoft MCE Keyboard in Oneiric"
date: 2011-11-03
forum: Mythbuntu
---

### Post by a1anmacp on 2011-11-03
Hi there,

Has anyone redone the lirc_mod_mce for Oneiric Ubuntu 11? I'm trying to get the keyboard and remote control working in mythbuntu 11, so far without success. When I use the scripts I get errors. I was following Jon47's guide here:
[http://ubuntuforums.org/showthread.php?t=661795&highlight=mce+keyboard&page=7](http://ubuntuforums.org/showthread.php?t=661795&highlight=mce+keyboard&page=7)

Any ideas? All suggestions gratefully received!

The command I typed was:

./setup.sh && make install

and the output ended with:
You will have to use the lirc_mceusb kernel module.

Now enter 'make' and 'make install' to compile and install the package.

Making install in drivers
make[1]: Entering directory `/home/alanm/Downloads/lirc-0.8.7/drivers'
Making install in lirc_dev
make[2]: Entering directory `/home/alanm/Downloads/lirc-0.8.7/drivers/lirc_dev'
cp ./../lirc_dev/Module*.symvers .
cp: cannot stat `./../lirc_dev/Module*.symvers': No such file or directory
make[2]: [lirc_dev.o] Error 1 (ignored)
mv Makefile Makefile.automake
cp ./../Makefile.kernel Makefile
CPPFLAGS="" CFLAGS="" LDFLAGS="" \
        make -C /lib/modules/3.0.0-12-generic/build/ SUBDIRS=/home/alanm/Downloads/lirc-0.8.7/drivers/lirc_dev modules \
                KBUILD_VERBOSE=1
make[3]: Entering directory `/usr/src/linux-headers-3.0.0-12-generic'
test -e include/generated/autoconf.h -a -e include/config/auto.conf || (       \
        echo;                                                           \
        echo "  ERROR: Kernel configuration is invalid.";               \
        echo "         include/generated/autoconf.h or include/config/auto.conf are missing.";\
        echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";  \
        echo;                                                           \
        /bin/false)
mkdir -p /home/alanm/Downloads/lirc-0.8.7/drivers/lirc_dev/.tmp_versions ; rm -f /home/alanm/Downloads/lirc-0.8.7/drivers/lirc_dev/.tmp_versions/*
make -f scripts/Makefile.build obj=/home/alanm/Downloads/lirc-0.8.7/drivers/lirc_dev
  gcc -Wp,-MD,/home/alanm/Downloads/lirc-0.8.7/drivers/lirc_dev/.lirc_dev.o.d  -nostdinc -isystem /usr/lib/gcc/i686-linux-gnu/4.6.1/include  -I/usr/src/linux-headers-3.0.0-12-generic/arch/x86/include -Iarch/x86/include/generated -Iinclude  -include include/generated/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -DIRCTL_DEV_MAJOR=61 -DEXPORT_SYMTAB -DHAVE_CONFIG_H -I. -I../.. -I/home/alanm/Downloads/lirc-0.8.7/drivers/lirc_dev/. -I/home/alanm/Downloads/lirc-0.8.7/drivers/lirc_dev/. -I/home/alanm/Downloads/lirc-0.8.7/drivers/lirc_dev/../.. -I/home/alanm/Downloads/lirc-0.8.7/drivers/lirc_dev/../.. -I/lib/modules/3.0.0-12-generic/build//include/ -I/lib/modules/3.0.0-12-generic/build//drivers/media/video/  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(lirc_dev)"  -D"KBUILD_MODNAME=KBUILD_STR(lirc_dev)" -c -o /home/alanm/Downloads/lirc-0.8.7/drivers/lirc_dev/.tmp_lirc_dev.o /home/alanm/Downloads/lirc-0.8.7/drivers/lirc_dev/lirc_dev.c
/home/alanm/Downloads/lirc-0.8.7/drivers/lirc_dev/lirc_dev.c:45:28: fatal error: linux/smp_lock.h: No such file or directory
compilation terminated.
make[4]: *** [/home/alanm/Downloads/lirc-0.8.7/drivers/lirc_dev/lirc_dev.o] Error 1
make[3]: *** [_module_/home/alanm/Downloads/lirc-0.8.7/drivers/lirc_dev] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic'
make[2]: *** [lirc_dev.o] Error 2
make[2]: Leaving directory `/home/alanm/Downloads/lirc-0.8.7/drivers/lirc_dev'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/alanm/Downloads/lirc-0.8.7/drivers'
make: *** [install-recursive] Error 1

---

### Post by klc5555 on 2011-11-03
> **a1anmacp said:**
> Hi there,

Has anyone redone the lirc_mod_mce for Oneiric Ubuntu 11? I'm trying to get the keyboard and remote control working in mythbuntu 11, so far without success. When I use the scripts I get errors. I was following Jon47's guide here:
[http://ubuntuforums.org/showthread.php?t=661795&highlight=mce+keyboard&page=7](http://ubuntuforums.org/showthread.php?t=661795&highlight=mce+keyboard&page=7)

Any ideas? All suggestions gratefully received!

The command I typed was:

./setup.sh && make install

and the output ended with:
You will have to use the lirc_mceusb kernel module.

Now enter 'make' and 'make install' to compile and install the package.

Making install in drivers
make[1]: Entering directory `/home/alanm/Downloads/lirc-0.8.7/drivers'
Making install in lirc_dev
make[2]: Entering directory `/home/alanm/Downloads/lirc-0.8.7/drivers/lirc_dev'
cp ./../lirc_dev/Module*.symvers .
cp: cannot stat `./../lirc_dev/Module*.symvers': No such file or directory
make[2]: [lirc_dev.o] Error 1 (ignored)
mv Makefile Makefile.automake
cp ./../Makefile.kernel Makefile
CPPFLAGS="" CFLAGS="" LDFLAGS="" \
        make -C /lib/modules/3.0.0-12-generic/build/ SUBDIRS=/home/alanm/Downloads/lirc-0.8.7/drivers/lirc_dev modules \
                KBUILD_VERBOSE=1
make[3]: Entering directory `/usr/src/linux-headers-3.0.0-12-generic'
test -e include/generated/autoconf.h -a -e include/config/auto.conf || (       \
        echo;                                                           \
        echo "  ERROR: Kernel configuration is invalid.";               \
        echo "         include/generated/autoconf.h or include/config/auto.conf are missing.";\
        echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";  \
        echo;                                                           \
        /bin/false)
mkdir -p /home/alanm/Downloads/lirc-0.8.7/drivers/lirc_dev/.tmp_versions ; rm -f /home/alanm/Downloads/lirc-0.8.7/drivers/lirc_dev/.tmp_versions/*
make -f scripts/Makefile.build obj=/home/alanm/Downloads/lirc-0.8.7/drivers/lirc_dev
  gcc -Wp,-MD,/home/alanm/Downloads/lirc-0.8.7/drivers/lirc_dev/.lirc_dev.o.d  -nostdinc -isystem /usr/lib/gcc/i686-linux-gnu/4.6.1/include  -I/usr/src/linux-headers-3.0.0-12-generic/arch/x86/include -Iarch/x86/include/generated -Iinclude  -include include/generated/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -DIRCTL_DEV_MAJOR=61 -DEXPORT_SYMTAB -DHAVE_CONFIG_H -I. -I../.. -I/home/alanm/Downloads/lirc-0.8.7/drivers/lirc_dev/. -I/home/alanm/Downloads/lirc-0.8.7/drivers/lirc_dev/. -I/home/alanm/Downloads/lirc-0.8.7/drivers/lirc_dev/../.. -I/home/alanm/Downloads/lirc-0.8.7/drivers/lirc_dev/../.. -I/lib/modules/3.0.0-12-generic/build//include/ -I/lib/modules/3.0.0-12-generic/build//drivers/media/video/  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(lirc_dev)"  -D"KBUILD_MODNAME=KBUILD_STR(lirc_dev)" -c -o /home/alanm/Downloads/lirc-0.8.7/drivers/lirc_dev/.tmp_lirc_dev.o /home/alanm/Downloads/lirc-0.8.7/drivers/lirc_dev/lirc_dev.c
/home/alanm/Downloads/lirc-0.8.7/drivers/lirc_dev/lirc_dev.c:45:28: fatal error: linux/smp_lock.h: No such file or directory
compilation terminated.
make[4]: *** [/home/alanm/Downloads/lirc-0.8.7/drivers/lirc_dev/lirc_dev.o] Error 1
make[3]: *** [_module_/home/alanm/Downloads/lirc-0.8.7/drivers/lirc_dev] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic'
make[2]: *** [lirc_dev.o] Error 2
make[2]: Leaving directory `/home/alanm/Downloads/lirc-0.8.7/drivers/lirc_dev'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/alanm/Downloads/lirc-0.8.7/drivers'
make: *** [install-recursive] Error 1

Oddly enough, I just happened to have two instances of this exact lirc compile failure with the same error message the day before yesterday, on a couple of Slackware boxes where I had installed freshly compiled kernels at the 2.6.39.4 and 3.0.4 level. Happened with lirc 0.8.7 source and 0.9.0 source. I wonder whether this glitch may affect any compiling of lirc at above 2.6.38-ish or so --I haven't had the opportunity to roll back the kernels on the two machines yet to test the theory.

On a more practical side for you, the mceusb module has itself been moved to the kernel since about 2.6.36 --a "sudo modprobe mceusb" is supposed to load the module and create a /dev/lirc0  If the module loads and the device node actually gets created for you after the modprobe, is it possible you could get your keyboard and/or IR running off of it? :confused:
------------------
As a later edit, I have since run a couple of additional kernels on one of the machines I mentioned above. And I tried compiling lirc-0.8.7pre2 and lirc-0.9.0-pre1 (since the "git" snapshots include source for lirc_mceusb, unlike the released versions). 

In my test machine, 3.0.4 and 2.6.39.4 failed to compile either lirc source, erroring with the error mentioned above. A newly compiled 2.6.38.8 compiled 0.9.0 and installed it successfully, but errored out on lirc 0.8.7 with ioctl errors. Ancient kernel 2.6.33.4 from the Wayback Machine compiled both lirc versions.

With lirc-0.9.0-pre1 compiled for lirc_mceusb and installed on kernel 2.6.38.8, lircd --driver=? yields the only supported driver as "default". However, modprobe lirc_mceusb in fact loads the lirc_mceusb module, and sets up the device node "/dev/lirc"

So in your case, you might want to try compiling the later "git snapshot" instead of 0.8.7, though I suspect that it too will fail on Oneiric kernel version 3.0.0.12.14 with the same error.

If it does, I'm not sure what to recommend. Modifying kernels in Ubuntu is about as much fun as hitting yourself in the head with a brick. If some other 11.10 runner can confirm this behavior in compiling lirc, then you likely a bug report should be filed.

---

### Post by a1anmacp on 2011-11-03
Hi klc5555 and thanks for taking the trouble to look into this. I see that lirc is included; the reason I was trying things manually is to add support for some Microsoft hardware: the remote control and IR keyboard from my old media centre setup (I can see from old posts that there are still a lot out there). The out of the box lirc allows for some very limited MCE remote control use but nothing really practical (and no MCE keyboard), so I was trying to add in some support which Jon46 had compiled for 10.04 & 10.10.

I think you may be right about the bug, but I don't have the knowledge (yet, anyway) to look at the possible git option and confirm it for myself. I really appreciate your time, though! I think that's as far as I can take it.

---

