---
title: "[SOLVED] Compiling LIRC from scratch"
date: 2008-09-09
forum: Mythbuntu
---

### Post by Marsupilami23 on 2008-09-09
I'm trying to compile LIRC from scratch against kernel source 2.26.3. I've had to recompile the kernel because the stock kernel with Ubuntu 8.04 doesn't work with my Pinnicle HD PCTV Card. So now that I've got the card working, I need an IRBlaster for my cable box. But when compiling the LIRC package I get this error:

```
make  all-recursive                     
make[1]: Entering directory `/home/mathew/lirc-0.8.3'
Making all in drivers                                
make[2]: Entering directory `/home/mathew/lirc-0.8.3/drivers'
Making all in lirc_dev                                       
make[3]: Entering directory `/home/mathew/lirc-0.8.3/drivers/lirc_dev'
mv Makefile Makefile.automake                                         
cp ./../Makefile.kernel Makefile                                      
CPPFLAGS="" CFLAGS="" LDFLAGS="" \                                    
        make -C /lib/modules/2.6.26.3/build/ SUBDIRS=/home/mathew/lirc-0.8.3/drivers/lirc_dev modules \
                KBUILD_VERBOSE=1                                                                       
make[4]: Entering directory `/usr/src/linux-2.6.26.3'                                                  
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (            \                      
        echo;                                                           \                              
        echo "  ERROR: Kernel configuration is invalid.";               \                              
        echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";      \      
        echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";  \              
        echo;                                                           \                              
        /bin/false)                                                                                    
mkdir -p /home/mathew/lirc-0.8.3/drivers/lirc_dev/.tmp_versions ; rm -f /home/mathew/lirc-0.8.3/drivers/lirc_dev/.tmp_versions/*                                                                                                          
make -f scripts/Makefile.build obj=/home/mathew/lirc-0.8.3/drivers/lirc_dev                                          
  gcc -Wp,-MD,/home/mathew/lirc-0.8.3/drivers/lirc_dev/.lirc_dev.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D__KERNEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2   -fno-stack-protector -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2  -march=i686 -mtune=pentium4 -mtune=generic -ffreestanding   -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iinclude/asm-x86/mach-default -fomit-frame-pointer -g -Wdeclaration-after-statement -Wno-pointer-sign   -DIRCTL_DEV_MAJOR=61 -DEXPORT_SYMTAB -DHAVE_CONFIG_H -I. -I. -I../.. -I/home/mathew/lirc-0.8.3/drivers/lirc_dev/. -I/home/mathew/lirc-0.8.3/drivers/lirc_dev/ -I/home/mathew/lirc-0.8.3/drivers/lirc_dev/../.. -I/home/mathew/lirc-0.8.3/drivers/lirc_dev/../.. -I/lib/modules/2.6.26.3/build//include/ -I/lib/modules/2.6.26.3/build//drivers/media/video/  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(lirc_dev)"  -D"KBUILD_MODNAME=KBUILD_STR(lirc_dev)" -c -o /home/mathew/lirc-0.8.3/drivers/lirc_dev/.tmp_lirc_dev.o /home/mathew/lirc-0.8.3/drivers/lirc_dev/lirc_dev.c
/home/mathew/lirc-0.8.3/drivers/lirc_dev/lirc_dev.c: In function ‘cleanup’:
/home/mathew/lirc-0.8.3/drivers/lirc_dev/lirc_dev.c:148: error: implicit declaration of function ‘class_device_destroy’
/home/mathew/lirc-0.8.3/drivers/lirc_dev/lirc_dev.c: In function ‘lirc_register_plugin’:
/home/mathew/lirc-0.8.3/drivers/lirc_dev/lirc_dev.c:403: error: implicit declaration of function ‘class_device_create’
make[5]: *** [/home/mathew/lirc-0.8.3/drivers/lirc_dev/lirc_dev.o] Error 1
make[4]: *** [_module_/home/mathew/lirc-0.8.3/drivers/lirc_dev] Error 2
make[4]: Leaving directory `/usr/src/linux-2.6.26.3'
make[3]: *** [lirc_dev.o] Error 2
make[3]: Leaving directory `/home/mathew/lirc-0.8.3/drivers/lirc_dev'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/mathew/lirc-0.8.3/drivers'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mathew/lirc-0.8.3'
make: *** [all] Error 2

```

Any help would be ideal, I've already tried the suggested above, I do have both include/linux/autoconf.h and include/config/auto.conf. I'm lost.

---

### Post by mattduckman on 2008-09-09
that error about the kernel configuration not being valid isn't being echoed, that's just the error that would echo if those files weren't found. somewhat misleading.

the real errors are in lirc_dev.c, on lines 148 and 403, but unfortunately, you'll have to contact the lirc devs directly to get a meaningful answer about this problem, since no one here probably knows the code well enough.

before doing that though, you might have luck searching the forums, lirc mailing lists, and google for people who might have had this same problem

---

### Post by Marsupilami23 on 2008-09-14
Marking SOLVED, downloaded the CVS version, made sure I had the autotools installed and it compiled.

---

