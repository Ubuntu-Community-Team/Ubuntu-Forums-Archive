---
title: "Unable to build the NVIDIA kernel module."
date: 2009-04-09
forum: Multimedia Software
---

### Post by miatawnt2b on 2009-04-09
I am trying to rebuild my NVIDIA drivers on my laptop.  I recently upgraded to kernel 2.6.27-11-generic and since then my video has been flaky.

So as always I kill gdm and attempt to rebuild the NVIDIA kernel modules using the NVIDIA installer.

 sudo sh NVIDIA-Linux-x86-173.14.12-pkg1.run 

After a little chugging I get an error, "Unable to build the NVIDIA kernel module."

here is the log:

```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Thu Apr  9 14:06:17 2009
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
-> There appears to already be a driver installed on your system (version: 173.
   14.12).  As part of installing this driver (version: 173.14.12), the existin
   g driver will be uninstalled.  Are you sure you want to continue? ('no' will
   abort installation) (Answer: Yes)
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: No)
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
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
   =/tmp/selfgz5886/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		
\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are 
mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix
 it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz5886/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/.tmp_ver
   sions ; rm -f /tmp/selfgz5886/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/.tm
   p_versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz5886/NVIDIA-Linux-x86-173.14.1
   2-pkg1/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz5886/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/.nv.
   o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.2/include -D__KERNEL
   __  -Iinclude  -I/usr/src/linux-headers-2.6.27-11-generic/arch/x86/include -
   include include/linux/autoc
   onf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fn
   o-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -m32
   -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -m
   arch=i586 -mtune=generic -ffreestanding -pipe -Wno-sign-compare -fno-asynchr
   onous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iinclude/asm-x86
   /mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sib
   ling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fwrapv -I/tm
   p/selfgz5886/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv -Wall -Wimplicit -Wr
   eturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith
   -Wno-multichar -Werror -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERN
   EL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"173.14.12\" -UDEBUG -U_DEBUG -DND
   EBUG -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KB
   UILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz5886/NVIDIA-Linux-x86-173.
   14.12-pkg1/usr/src/nv/.tmp_nv.o /t
   mp/selfgz5886/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5886/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz5886/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
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
                    from /tmp/selfgz5886/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz5886/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz5886/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz5886/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:1975: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:94,
                    from include/linux/pci.h:989,
                    from /tmp/selfgz5886/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz5886/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /tmp/selfgz5886/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv.c:14:
   /tmp/selfgz5886/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv-linux.h:107:27
   : error: asm/semaphore.h: No such file or directory
   In file included from /tmp/selfgz5886/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv-linux.h:109,
                    from /tmp/selfgz5886/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
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
   In file included from /tmp/selfgz5886/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv.c:14:
   /tmp/selfgz5886/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv-linux.h: In fu
   nction ‘nv_execute_on_all_cpus’:
   /tmp/selfgz5886/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv-linux.h:674: e
   rror: too many arguments to function ‘on_each_cpu’
   /tmp/selfgz5886/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv.c: In function
   ‘nv_kern_cpu_callback’:
   /tmp/selfgz5886/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv.c:1299: error:
   too many arguments to function ‘smp_call_function’
   /tmp/selfgz5886/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv.c:1306: error:
   too many arguments to function ‘smp_call_function’
   make[3]: *** [/tmp/selfgz5886/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv.
   o] Error 1
   make[2]: *** [_module_/tmp/selfgz5886/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
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

Any idea what's going on here?
-J

---

### Post by cariboo on 2009-04-09
Have you got build-essential installed?

Jim

---

### Post by miatawnt2b on 2009-04-09
> **cariboo907 said:**
> Have you got build-essential installed?

Jim

You bet.  I've used this driver in the past with other kernels.  I have to rebuild every time a kernel update comes along.  However, this kernel seems to have broken things.

-J

---

