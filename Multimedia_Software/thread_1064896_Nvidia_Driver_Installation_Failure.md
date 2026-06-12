---
title: "Nvidia Driver Installation Failure"
date: 2009-02-09
forum: Multimedia Software
---

### Post by GuitarFreak1857 on 2009-02-09
I just did a fresh install of Xubuntu 8.10 on my Toshiba Tecra M2.  I downloaded the Nvidia driver from the web site and ran it and it failed and said to check the .log file.  Here's what it said.  Can anyone help me?

```

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Mon Feb  9 11:13:29 2009
installer version: 1.0.7

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  no cc version check     : false
  force tls               : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 173.14.12.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.27-7-generic/build'
-> Kernel output path: '/lib/modules/2.6.27-7-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.27-7-generi
   c/build SYSOUT=/lib/modules/2.6.27-7-generic/build'...
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.27-7-generic/build SUBDIRS=
   /tmp/selfgz6486/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz6486/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/.tmp_ver
   sions ; rm -f /tmp/selfgz6486/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/.tm
   p_versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz6486/NVIDIA-Linux-x86-173.14.1
   2-pkg1/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz6486/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/.nv.
   o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.2/include -D__KERNEL
   __  -Iinclude  -I/usr/src/linux-headers-2.6.27-7-generic/arch/x86/include -i
   nclude include/linux/autocon
   f.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-
   strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -m32 -
   msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -ma
   rch=i586 -mtune=generic -ffreestanding -pipe -Wno-sign-compare -fno-asynchro
   nous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iinclude/asm-x86/
   mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibl
   ing-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -I/tmp/selfgz6
   486/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-typ
   e -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-mul
   tichar -Werror -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DM
   ODULE -DNVRM -DNV_VERSION_STRING=\"173.14.12\" -UDEBUG -U_DEBUG -DNDEBUG -DM
   ODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MOD
   NAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz6486/NVIDIA-Linux-x86-173.14.12-pk
   g1/usr/src/nv/.tmp_nv.o /tmp/selfgz6
   486/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6486/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6486/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv.c:14:
   include/asm/bitops.h: In function ‘set_bit’:
   include/asm/bitops.h:60: warning: pointer of type ‘void *’ used in arith
   metic
   include/asm/bitops.h: In function ‘clear_bit’:
   include/asm/bitops.h:97: warning: pointer of type ‘void *’ used in arith
   metic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6486/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6486/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz6486/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6486/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:1969: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:94,
                    from include/linux/pci.h:983,
                    from /tmp/selfgz6486/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz6486/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /tmp/selfgz6486/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv.c:14:
   /tmp/selfgz6486/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv-linux.h:107:27
   : error: asm/semaphore.h: No such file or directory
   In file included from /tmp/selfgz6486/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv-linux.h:109,
                    from /tmp/selfgz6486/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:134: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from /tmp/selfgz6486/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv.c:14:
   /tmp/selfgz6486/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv-linux.h: In fu
   nction ‘nv_execute_on_all_cpus’:
   /tmp/selfgz6486/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv-linux.h:674: e
   rror: too many arguments to function ‘on_each_cpu’
   /tmp/selfgz6486/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv.c: In function
   ‘nv_kern_cpu_callback’:
   /tmp/selfgz6486/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv.c:1299: error:
   too many arguments to function ‘smp_call_function’
   /tmp/selfgz6486/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv.c:1306: error:
   too many arguments to function ‘smp_call_function’
   make[3]: *** [/tmp/selfgz6486/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv.
   o] Error 1
   make[2]: *** [_module_/tmp/selfgz6486/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv] Error 2
   NVIDIA: left KBUILD.
   nvidia.ko failed to build!
   make[1]: *** [module] Error 1
   make: *** [module] Error 2
-> Error.
ERROR: Unable to build the NVIDIA kernel module.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

```

~Thanks!

---

### Post by jbrown96 on 2009-02-09
Is that the newest driver available for your hardware. I have a year old card and am using the 180.22 drivers. That shouldn't make a difference, but you may get better performance/features from a newer driver, but only if it's for your card. 

Try installing the build-essential package. this should give you all the compilers and header files you need. ```
sudo apt-get install build-essential
```

---

### Post by GuitarFreak1857 on 2009-02-09
Tried that and the installation got a little farther, except i got an error and it failed. 

```

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Mon Feb  9 13:12:24 2009
installer version: 1.0.7

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  no cc version check     : false
  force tls               : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 173.14.12.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.27-11-generic/build'
-> Kernel output path: '/lib/modules/2.6.27-11-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.27-11-gener
   ic/build SYSOUT=/lib/modules/2.6.27-11-generic/build'...
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.27-11-generic/build SUBDIRS
   =/tmp/selfgz6041/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz6041/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/.tmp_ver
   sions ; rm -f /tmp/selfgz6041/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/.tm
   p_versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz6041/NVIDIA-Linux-x86-173.14.1
   2-pkg1/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz6041/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/.nv.
   o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.2/include -D__KERNEL
   __  -Iinclude  -I/usr/src/linux-headers-2.6.27-11-generic/arch/x86/include -
   include include/linux/autoc
   onf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fn
   o-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -m32
   -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -m
   arch=i586 -mtune=generic -ffreestanding -pipe -Wno-sign-compare -fno-asynchr
   onous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iinclude/asm-x86
   /mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sib
   ling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -I/tmp/selfgz
   6041/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-ty
   pe -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-mu
   ltichar -Werror -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -D
   MODULE -DNVRM -DNV_VERSION_STRING=\"173.14.12\" -UDEBUG -U_DEBUG -DNDEBUG -D
   MODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MO
   DNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz6041/NVIDIA-Linux-x86-173.14.12-p
   kg1/usr/src/nv/.tmp_nv.o /tmp/selfg
   z6041/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6041/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6041/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv.c:14:
   include/asm/bitops.h: In function ‘set_bit’:
   include/asm/bitops.h:60: warning: pointer of type ‘void *’ used in arith
   metic
   include/asm/bitops.h: In function ‘clear_bit’:
   include/asm/bitops.h:97: warning: pointer of type ‘void *’ used in arith
   metic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6041/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6041/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz6041/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6041/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:1975: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:94,
                    from include/linux/pci.h:989,
                    from /tmp/selfgz6041/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz6041/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /tmp/selfgz6041/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv.c:14:
   /tmp/selfgz6041/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv-linux.h:107:27
   : error: asm/semaphore.h: No such file or directory
   In file included from /tmp/selfgz6041/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv-linux.h:109,
                    from /tmp/selfgz6041/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:134: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from /tmp/selfgz6041/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv.c:14:
   /tmp/selfgz6041/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv-linux.h: In fu
   nction ‘nv_execute_on_all_cpus’:
   /tmp/selfgz6041/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv-linux.h:674: e
   rror: too many arguments to function ‘on_each_cpu’
   /tmp/selfgz6041/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv.c: In function
   ‘nv_kern_cpu_callback’:
   /tmp/selfgz6041/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv.c:1299: error:
   too many arguments to function ‘smp_call_function’
   /tmp/selfgz6041/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv.c:1306: error:
   too many arguments to function ‘smp_call_function’
   make[3]: *** [/tmp/selfgz6041/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv.
   o] Error 1
   make[2]: *** [_module_/tmp/selfgz6041/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv] Error 2
   NVIDIA: left KBUILD.
   nvidia.ko failed to build!
   make[1]: *** [module] Error 1
   make: *** [module] Error 2
-> Error.
ERROR: Unable to build the NVIDIA kernel module.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.

```

~Thanks

---

