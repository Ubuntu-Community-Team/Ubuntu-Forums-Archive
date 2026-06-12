---
title: "Not able to install e-GeForce FX 5200"
date: 2009-02-27
forum: Multimedia Software
---

### Post by 4dplane on 2009-02-27
Hi,

I have an e-GeForce FX 5200 
I have unbuntu 8 with kernal 2.6.27-11
I am tring to use driver x86-173.14.12 

This error seems to be the problem, I have googled a bit but nothing works.

from nvidia log file
```

   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
   	echo;

```

Any Ideas?

nvidia log file
```

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Fri Feb 27 15:14:20 2009
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
   14.16).  As part of installing this driver (version: 173.14.12), the existin
   g driver will be uninstalled.  Are you sure you want to continue? ('no' will
   abort installation) (Answer: Yes)
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
   =/tmp/selfgz8167/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz8167/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/.tmp_ver
   sions ; rm -f /tmp/selfgz8167/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/.tm
   p_versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz8167/NVIDIA-Linux-x86-173.14.1
   2-pkg1/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz8167/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/.nv.
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
   8167/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-ty
   pe -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-mu
   ltichar -Werror -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -D
   MODULE -DNVRM -DNV_VERSION_STRING=\"173.14.12\" -UDEBUG -U_DEBUG -DNDEBUG -D
   MODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MO
   DNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz8167/NVIDIA-Linux-x86-173.14.12-p
   kg1/usr/src/nv/.tmp_nv.o /tmp/selfg
   z8167/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz8167/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz8167/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv.c:14:
   include/asm/bitops.h: In function â€˜set_bitâ€™:
   include/asm/bitops.h:60: warning: pointer of type â€˜void *â€™ used in arith
   metic
   include/asm/bitops.h: In function â€˜clear_bitâ€™:
   include/asm/bitops.h:97: warning: pointer of type â€˜void *â€™ used in arith
   metic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz8167/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz8167/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/prefetch.h: In function â€˜prefetch_rangeâ€™:
   include/linux/prefetch.h:57: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz8167/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz8167/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/sched.h: In function â€˜object_is_on_stackâ€™:
   include/linux/sched.h:1975: warning: pointer of type â€˜void *â€™ used in ar
   ithmetic
   In file included from include/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:94,
                    from include/linux/pci.h:989,
                    from /tmp/selfgz8167/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz8167/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/scatterlist.h: In function â€˜sg_virtâ€™:
   include/linux/scatterlist.h:199: warning: pointer of type â€˜void *â€™ used 
   in arithmetic
   In file included from /tmp/selfgz8167/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv.c:14:
   /tmp/selfgz8167/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv-linux.h:107:27
   : error: asm/semaphore.h: No such file or directory
   In file included from /tmp/selfgz8167/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv-linux.h:109,
                    from /tmp/selfgz8167/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/highmem.h: In function â€˜zero_user_segmentsâ€™:
   include/linux/highmem.h:134: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   In file included from /tmp/selfgz8167/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv.c:14:
   /tmp/selfgz8167/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv-linux.h: In fu
   nction â€˜nv_execute_on_all_cpusâ€™:
   /tmp/selfgz8167/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv-linux.h:674: e
   rror: too many arguments to function â€˜on_each_cpuâ€™
   /tmp/selfgz8167/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv.c: In function
   â€˜nv_kern_cpu_callbackâ€™:
   /tmp/selfgz8167/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv.c:1299: error:
   too many arguments to function â€˜smp_call_functionâ€™
   /tmp/selfgz8167/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv.c:1306: error:
   too many arguments to function â€˜smp_call_functionâ€™
   make[3]: *** [/tmp/selfgz8167/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv.
   o] Error 1
   make[2]: *** [_module_/tmp/selfgz8167/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
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

---

### Post by cariboo on 2009-02-27
Why not install the driver from the repositories? 
Go to System-->Administration-->Hardware  Drivers and activate the suggested driver.

If that doesn't work, open System-->Administration-->Synaptic Package Manager and search for nvidia-glx-173.

Jim

---

### Post by 4dplane on 2009-02-27
Thanks Jim,

I tried: "Go to System-->Administration-->Hardware Drivers and activate the suggested driver" the driver is there and I activate it but when I reboot the machine is in low graphics mode.

I then tried:
open System-->Administration-->Synaptic Package Manager and there seems to be a bug with Unbuntu and it will not let me login. I get the error message "failed to run /usr/sbin/synaptic as root"
I tried both su password and current user password, I believe it wants the current user password.

Thanks,
4dplane

---

### Post by Cpyles07 on 2009-02-28
Try activating 96 version instead of 173. I didn't have the exact problem you do but similar.

---

### Post by 4dplane on 2009-02-28
So i installed the kunbutu desktop and rebooted, I then go into gnome and now I can use the Synaptic Package Manager and I installed nvidia-glx-173 - greet! well no... when I reboot the machine it does not say it's in low graphics mode but the screen is far too red and the screen resolution is stuck at 640 x 480 50hz. When I go to screen resolution there are no other selections and when I go to the nVidia control panel the sliders to modify the color move the the window in a crazy sporadic fashion. :mad:

any idea why this is,
4D

---

### Post by 4dplane on 2009-02-28
Got it - and its a wopper! 

you where correct Cpyles07, all I had to use was the Hardware Drivers page and activate it! The reason why I thought it was not working is because the video card is damaged; it does not produce any green. Plus you have to manually modify the xconfig file to set the proper resolution. So after I activated it and it still looked like crap I knew something was wrong and immediately thought software. I installed the card on my windows box and it's still missing the green - so its the card :guitar: 

Thank you for your help,
4dplane

---

