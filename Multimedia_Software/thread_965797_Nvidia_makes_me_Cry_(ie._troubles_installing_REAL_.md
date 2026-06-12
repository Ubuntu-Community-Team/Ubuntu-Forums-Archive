---
title: "Nvidia makes me Cry (ie. troubles installing REAL Drivers)"
date: 2008-10-31
forum: Multimedia Software
---

### Post by au_vagabond on 2008-10-31
Hey, sorry to bother you all but I just installed Kubuntu 8.10 (so pretty ^^) and I am having a ridiculous amount of difficulty installing the *real*NVIDIA drivers. The last time I tried to do this in ubuntu, it worked great and I was able to game through wine and have pretty much replace windows - it's not like I am unfamiliar with the process. So yeah, I need help, here is the log file. It is really strange, it just stopped when it reached the compilation stage. It is also worth noting that the NVIDIA site is being REALLY weird at the moment, so I could have just downloaded the wrong driver - in which case could someone link to an alternative source, as I could not find one (saying that, I am pretty dumb at the moment - Card=7600GS). Thanks in advance - vags.

```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sat Nov  1 11:05:03 2008
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
-> Installing NVIDIA driver version 177.13.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
ERROR: Unable to connect to download.nvidia.com (unknown host)
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
   /tmp/selfgz12848/NVIDIA-Linux-x86-177.13-pkg1/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz12848/NVIDIA-Linux-x86-177.13-pkg1/usr/src/nv/.tmp_versi
   ons ; rm -f /tmp/selfgz12848/NVIDIA-Linux-x86-177.13-pkg1/usr/src/nv/.tmp_ve
   rsions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz12848/NVIDIA-Linux-x86-177.13-
   pkg1/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz12848/NVIDIA-Linux-x86-177.13-pkg1/usr/src/nv/.nv.o.
   d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.2/include -D__KERNEL__
    -Iinclude  -I/usr/src/linux-headers-2.6.27-7-generic/arch/x86/include -incl
   ude include/linux/autoconf.h -Iubun
   tu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-ali
   asing -fno-common -Werror-implicit-function-declaration -O2 -m32 -msoft-floa
   t -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -
   mtune=generic -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwin
   d-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iinclude/asm-x86/mach-defau
   lt -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls 
   -pg -Wdeclaration-after-statement -Wno-pointer-sign -I/tmp/selfgz12848/NVIDI
   A-Linux-x86-177.13-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -
   Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werr
   or -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM
   -DNV_VERSION_STRING=\"177.13\" -UDEBUG -U_DEBUG -DNDEBUG -DMODULE -D"KBUILD_
   STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KBUILD_STR(
   nvidia)" -c -o /tmp/selfgz12848/NVIDIA-Linux-x86-177.13-pkg1/usr/src/nv/.tmp
   _nv.o /tmp/selfgz12848/NVIDIA-Linux
   -x86-177.13-pkg1/usr/src/nv/nv.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz12848/NVIDIA-Linux-x86-177.13-pkg1/usr/src/
   nv/nv-linux.h:19,
                    from /tmp/selfgz12848/NVIDIA-Linux-x86-177.13-pkg1/usr/src/
   nv/nv.c:14:
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
                    from /tmp/selfgz12848/NVIDIA-Linux-x86-177.13-pkg1/usr/src/
   nv/nv-linux.h:19,
                    from /tmp/selfgz12848/NVIDIA-Linux-x86-177.13-pkg1/usr/src/
   nv/nv.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz12848/NVIDIA-Linux-x86-177.13-pkg1/usr/src/
   nv/nv-linux.h:19,
                    from /tmp/selfgz12848/NVIDIA-Linux-x86-177.13-pkg1/usr/src/
   nv/nv.c:14:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:1969: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:94,
                    from include/linux/pci.h:983,
                    from /tmp/selfgz12848/NVIDIA-Linux-x86-177.13-pkg1/usr/src/
   nv/nv-linux.h:86,
                    from /tmp/selfgz12848/NVIDIA-Linux-x86-177.13-pkg1/usr/src/
   nv/nv.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /tmp/selfgz12848/NVIDIA-Linux-x86-177.13-pkg1/usr/src/
   nv/nv.c:14:
   /tmp/selfgz12848/NVIDIA-Linux-x86-177.13-pkg1/usr/src/nv/nv-linux.h:107:27: 
   error: asm/semaphore.h: No such file or directory
   In file included from /tmp/selfgz12848/NVIDIA-Linux-x86-177.13-pkg1/usr/src/
   nv/nv-linux.h:109,
                    from /tmp/selfgz12848/NVIDIA-Linux-x86-177.13-pkg1/usr/src/
   nv/nv.c:14:
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
   In file included from /tmp/selfgz12848/NVIDIA-Linux-x86-177.13-pkg1/usr/src/
   nv/nv.c:14:
   /tmp/selfgz12848/NVIDIA-Linux-x86-177.13-pkg1/usr/src/nv/nv-linux.h: In func
   tion ‘nv_execute_on_all_cpus’:
   /tmp/selfgz12848/NVIDIA-Linux-x86-177.13-pkg1/usr/src/nv/nv-linux.h:674: err
   or: too many arguments to function ‘on_each_cpu’
   /tmp/selfgz12848/NVIDIA-Linux-x86-177.13-pkg1/usr/src/nv/nv.c: In function &#65533;
   &#65533;&#65533;nv_kern_cpu_callback’:
   /tmp/selfgz12848/NVIDIA-Linux-x86-177.13-pkg1/usr/src/nv/nv.c:1299: error: t
   oo many arguments to function ‘smp_call_function’
   /tmp/selfgz12848/NVIDIA-Linux-x86-177.13-pkg1/usr/src/nv/nv.c:1306: error: t
   oo many arguments to function ‘smp_call_function’
   make[3]: *** [/tmp/selfgz12848/NVIDIA-Linux-x86-177.13-pkg1/usr/src/nv/nv.o]
   Error 1
   make[2]: *** [_module_/tmp/selfgz12848/NVIDIA-Linux-x86-177.13-pkg1/usr/src/
   nv] Error 2
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

### Post by Dyst Mingus on 2008-10-31
quote from [http://www.linuxjournal.com/content/ubuntu-810-charges-mountain](http://www.linuxjournal.com/content/ubuntu-810-charges-mountain) :

"One hiccup encountered with 8.10 involves the proprietary drivers for certain nVidia video cards — including the GeForce & TNT lines — which are not compatible with X.Org 7.4. Affected users will be automatically switched to the free nv driver during the upgrade, however, the nv driver does not support 3D acceleration (i.e. No Compiz Fusion)."

good luck.

---

### Post by au_vagabond on 2008-10-31
71 & 96 drivers? Is it reffering to the driver version number (eg NVIDIA-Linux-x86-177.13) or the graphics card model (ie. and 8800gtx would work). In other words - can someone explain what works/doesn't work under Intrepid (well, X.org 7.4), and also - HOW LONG!!!!!!!! *goes back to crying*.

---

### Post by AaronP_ on 2008-11-01
177.13 is old.  You should use the current release, which is 177.80.

---

