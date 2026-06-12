---
title: "Cannot install driver for GeForce 8600GT"
date: 2008-07-27
forum: Multimedia Software
---

### Post by rWarrior on 2008-07-27
Ubuntu 8.04.1
GeForce 8600GT 512MB

I tried System Ad > Hardware Drivers... and it didn't work (I cannot boot into gnome).
I tried envyng-gtk... and it didn't work.

Then, I downloaded NVIDIA-Linux-x86-173.14.05-pkg1.run from nVidia, followed the instructions outlined at [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)
( `uname -r` never generated the correct version number for me though... so I just made sure I have the latest version of linux-headers installed, and probably linked to make the nvidia installer happy)

After much trouble, the driver seemed to compile, but the installer was unable to load the kernel module 'nvidia.ko', because "nvidia: disagrees about version of symbol struct_module"...?

Help?


The /var/log/nvidia-installer.log is given here:

```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sun Jul 27 00:42:15 2008

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
  kernel source path      : /usr/src/linux-headers-2.6.24-19-generic/
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: No)
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> The CC version check failed:
   
   The compiler used to compile the kernel (gcc 4.1) does not exactly match the
   current compiler (gcc 4.2).  The Linux 2.6 kernel module loader rejects kern
   el modules built with a version of gcc that does not exactly match that of t
   he compiler used to build the running kernel.
   
   If you know what you are doing and want to ignore the gcc version check, sel
   ect "No" to continue installation.  Otherwise, select "Yes" to abort install
   ation, set the CC environment variable to the name of the compiler used to c
   ompile your kernel, and restart installation.  Abort now? (Answer: No)
-> Using the kernel source path '/usr/src/linux-headers-2.6.24-19-generic/' as
   specified by the '--kernel-source-path' commandline option.
-> Kernel source path: '/usr/src/linux-headers-2.6.24-19-generic/'
-> Kernel output path: '/usr/src/linux-headers-2.6.24-19-generic/'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/usr/src/linux-headers-2.6.2
   4-19-generic/ SYSOUT=/usr/src/linux-headers-2.6.24-19-generic/'...
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /usr/src/linux-headers-2.6.24-19-generic/ SU
   BDIRS=/tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/src/nv/.tmp_ver
   sions ; rm -f /tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/src/nv/.tm
   p_versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz6160/NVIDIA-Linux-x86-173.14.0
   5-pkg1/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/src/nv/.nv.
   o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D__KERNEL
   __  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prot
   otypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-func
   tion-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mpr
   eferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumu
   late-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer -g 
   -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign   -I/tm
   p/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/src/nv -Wall -Wimplicit -Wr
   eturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith
   -Wno-multichar -Werror -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D__KE
   RNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"173.14.05\" -UDEBUG -U_DEBUG -D
   NDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D
   "KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz6160/NVIDIA-Linux-x86-1
   73.14.05-pkg1/usr/src/nv/.tmp_nv.o /tmp/selfgz6160/NVIDIA-Linux-x86-173.14.0
   5-pkg1/usr/src/nv/nv.c
   In file included from include/linux/list.h:8,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:49,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:53,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/prefetch.h: In function &#8216;prefetch_range&#8217;:
   include/linux/prefetch.h:57: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   In file included from include/asm/dma-mapping_32.h:5,
                    from include/asm/dma-mapping.h:2,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/scatterlist.h: In function &#8216;sg_virt&#8217;:
   include/linux/scatterlist.h:293: warning: pointer of type &#8216;void *&#8217; used 
   in arithmetic
     cc -Wp,-MD,/tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/src/nv/.nv-
   vm.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D__KER
   NEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-p
   rototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-f
   unction-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -
   mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -macc
   umulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer 
   -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign   -
   I/tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/src/nv -Wall -Wimplicit
   -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-ar
   ith -Wno-multichar -Werror -MD 
     -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV
   _VERSION_STRING=\"173.14.05\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_
   STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_vm)"  -D"KBUILD_MODNAME=KBUILD_S
   TR(nvidia)" -c -o /tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/src/nv
   /.tmp_nv-vm.o /tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/src/nv/nv-
   vm.c
   In file included from include/linux/list.h:8,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:49,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:53,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/prefetch.h: In function &#8216;prefetch_range&#8217;:
   include/linux/prefetch.h:57: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   In file included from include/asm/dma-mapping_32.h:5,
                    from include/asm/dma-mapping.h:2,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/scatterlist.h: In function &#8216;sg_virt&#8217;:
   include/linux/scatterlist.h:293: warning: pointer of type &#8216;void *&#8217; used 
   in arithmetic
     cc -Wp,-MD,/tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/src/nv/.os-
   agp.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D__KE
   RNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-
   prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werr
   or-implicit-function-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-st
   ruct-return -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffrees
   tanding -maccumulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-f
   rame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-poi
   nter-sign   -I/tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/src/nv -Wa
   ll -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparenthese
   s -Wpointer-arith -Wno-multichar -Werror -MD   -Wsign-compare -Wno-cast-qual
   -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"173.14.05\" -U
   DEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KB
   UILD_STR(os_agp)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz61
   60/NVIDIA-Linux-x86-173.14.05-pkg1/usr/src/nv/.tmp_os-agp.o /tmp/selfgz6160/
   NVIDIA-Linux-x86-173.14.05-pkg1/usr/src/nv/os-agp.c
   In file included from include/linux/list.h:8,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:49,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:53,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/prefetch.h: In function &#8216;prefetch_range&#8217;:
   include/linux/prefetch.h:57: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   In file included from include/asm/dma-mapping_32.h:5,
                    from include/asm/dma-mapping.h:2,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/scatterlist.h: In function &#8216;sg_virt&#8217;:
   include/linux/scatterlist.h:293: warning: pointer of type &#8216;void *&#8217; used 
   in arithmetic
     cc -Wp,-MD,/tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/src/nv/.os-
   interface.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include 
   -D__KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Ws
   trict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-imp
   licit-function-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-r
   eturn -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestandin
   g -maccumulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-p
   ointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-s
   ign   -I/tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/src/nv -Wall -Wi
   mplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpo
   inter-arith -Wno-multichar -Werror -MD   -Wsign-co
   mpare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_ST
   RING=\"173.14.05\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" 
   -D"KBUILD_BASENAME=KBUILD_STR(os_interface)"  -D"KBUILD_MODNAME=KBUILD_STR(n
   vidia)" -c -o /tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/src/nv/.tm
   p_os-interface.o /tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/src/nv/
   os-interface.c
   In file included from include/linux/list.h:8,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:49,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:53,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/linux/prefetch.h: In function &#8216;prefetch_range&#8217;:
   include/linux/prefetch.h:57: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   In file included from include/asm/dma-mapping_32.h:5,
                    from include/asm/dma-mapping.h:2,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/linux/scatterlist.h: In function &#8216;sg_virt&#8217;:
   include/linux/scatterlist.h:293: warning: pointer of type &#8216;void *&#8217; used 
   in arithmetic
     cc -Wp,-MD,/tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/src/nv/.os-
   registry.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -
   D__KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wst
   rict-prototypes -Wno-trigraphs -fno-stri
   ct-aliasing -fno-common -Werror-implicit-function-declaration -O2 -pipe -mso
   ft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2  -marc
   h=i586 -mtune=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/
   asm-x86/mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclara
   tion-after-statement -Wno-pointer-sign   -I/tmp/selfgz6160/NVIDIA-Linux-x86-
   173.14.05-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -
   Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -MD   
   -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_V
   ERSION_STRING=\"173.14.05\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_ST
   R(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_registry)"  -D"KBUILD_MODNAME=KBUI
   LD_STR(nvidia)" -c -o /tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/sr
   c/nv/.tmp_os-registry.o /tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/
   src/nv/os-registry.c
   In file included from include/linux/list.h:8,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:49,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:53,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/sr
   c/nv/os-registry.c:15:
   include/linux/prefetch.h: In function &#8216;prefetch_range&#8217;:
   include/linux/prefetch.h:57: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   In file included from include/asm/dma-mapping_32.h:5,
                    from include/asm/dma-mapping.h:2,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/sr
   c/nv/os-registry.c:15:
   include/linux/scatterlist.h: In function &#8216;sg_virt&#8217;:
   include/linux/scatterlist.h:293: warning: pointer of type &#8216;void *&#8217; used 
   in arithmetic
     cc -Wp,-MD,/tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/src/nv/.nv-
   i2c.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D__KE
   RNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-
   prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-
   function-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return 
   -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -mac
   cumulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer
   -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign   -
   I/tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/src/nv -Wall -Wimplicit
   -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpoin
   ter-arith -Wno-multichar -Werror -MD   -Wsign-compare -Wno-cast-qual -Wno-er
   ror -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"173.14.05\" -UDEBUG -
   U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_ST
   R(nv_i2c)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz6160/NVID
   IA-Linux-x86-173.14.05-pkg1/usr/src/nv/.tmp_nv-i2c.o /tmp/selfgz6160/NVIDIA-
   Linux-x86-173.14.05-pkg1/usr/src/nv/nv-i2c.c
   In file included from include/linux/list.h:8,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:49,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:53,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   include/linux/prefetch.h: In function &#8216;prefetch_range&#8217;:
   include/linux/prefetch.h:57: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   In file included from include/asm/dma-mapping_32.h:5,
                    from include/asm/dma-mapping.h:2,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   include/linux/scatterlist.h: In function &#8216;sg_virt&#8217;:
   include/linux/scatterlist.h:293: warning: pointer of type &#8216;void *&#8217; used 
   in arithmetic
     cc -Wp,-MD,/tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/src/nv/.nva
   cpi.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D__KE
   RNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-
   prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-
   function-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return 
   -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -mac
   cumulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer
   -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign   -
   I/tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/src/nv -Wall -Wimplicit
   -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-ar
   ith -Wno-multichar -Werror -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D
   __KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"173.14.05\" -UDEBUG -U_DEBU
   G -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nvac
   pi)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz6160/NVIDIA-Lin
   ux-x86-173.14.05-pkg1/usr/src/nv/.tmp_nvacpi.o /tmp/selfgz6160/NVIDIA-Linux-
   x86-173.14.05-pkg1/usr/src/nv/nvacpi.c
   In file included from include/linux/list.h:8,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:49,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:53,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   include/linux/prefetch.h: In function &#8216;prefetch_range&#8217;:
   include/linux/prefetch.h:57: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   In file included from include/asm/dma-mapping_32.h:5,
                    from include/asm/dma-mapping.h:2,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   include/linux/scatterlist.h: In function &#8216;sg_virt&#8217;:
   include/linux/scatterlist.h:293: warning: pointer of type &#8216;void *&#8217; used 
   in arithmetic
     ld -m elf_i386 -m elf_i386   -r -o /tmp/selfgz6160/NVIDIA-Linux-x86-173.14
   .05-pkg1/usr/src/nv/nvidia.o /tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1
   /usr/src/nv/nv-kernel.o /tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/
   src/nv/nv.o /tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/src/nv/nv-vm
   .o /tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/src/nv/os-agp.o /tmp/
   selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/src/nv/os-interface.o /tmp/se
   lfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/src/nv/os-registry.o /tmp/selfg
   z6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/src/nv/nv-i2c.o /tmp/selfgz6160/NV
   IDIA-Linux-x86-173.14.05-pkg1/usr/src/nv/nvacpi.o
     Building modules, stage 2.
   make -f /usr/src/linux-headers-2.6.24-19-generic/scripts/Makefile.modpost
     scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.24-19-generic/Modu
   le.symvers -I /tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/src/nv/Mod
   ule.symvers -o /tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/src/nv/Mo
   dule.symvers -w -s
   WARNING: could not find /tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/
   src/nv/.nv-kernel.o.cmd for /tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/
   usr/src/nv/nv-kernel.o
     cc -Wp,-MD,/tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-pkg1/usr/src/nv/.nvi
   dia.mod.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D
   __KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstr
   ict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-impli
   cit-function-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-ret
   urn -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding 
   -maccumulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-poi
   nter -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sig
   n  
     -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nvidia.mod)"  -D"KBUILD
   _MODNAME=KBUILD_STR(nvidia)" -DMODULE -c -o /tmp/selfgz6160/NVIDIA-Linux-x86
   -173.14.05-pkg1/usr/src/nv/nvidia.mod.o /tmp/selfgz6160/NVIDIA-Linux-x86-173
   .14.05-pkg1/usr/src/nv/nvidia.mod.c
     ld -m elf_i386 -r -m elf_i386  --build-id -o /tmp/selfgz6160/NVIDIA-Linux-
   x86-173.14.05-pkg1/usr/src/nv/nvidia.ko /tmp/selfgz6160/NVIDIA-Linux-x86-173
   .14.05-pkg1/usr/src/nv/nvidia.o /tmp/selfgz6160/NVIDIA-Linux-x86-173.14.05-p
   kg1/usr/src/nv/nvidia.mod.o
   NVIDIA: left KBUILD.
-> done.
-> Kernel module compilation complete.
ERROR: Unable to load the kernel module 'nvidia.ko'.  This happens most
       frequently when this kernel module was built against the wrong or
       improperly configured kernel sources, with a version of gcc that differs
       from the one used to build the target kernel, or if a driver such as
       rivafb/nvidiafb is present and prevents the NVIDIA kernel module from
       obtaining ownership of the NVIDIA graphics device(s).
       
       Please see the log entries 'Kernel module load error' and 'Kernel
       messages' at the end of the file '/var/log/nvidia-installer.log' for
       more information.
-> Kernel module load error: insmod: error inserting './usr/src/nv/nvidia.ko':
   -1 Invalid module format
-> Kernel messages:
   [   35.960117] EXT3-fs: mounted filesystem with ordered data mode.
   [   36.813718] audit(1217132363.995:3):  type=1505 operation="profile_load"
   info="failed to unpack profile" name="/usr/lib/cups/backend/cups-pdf"
   pid=4100
   [   36.928456] ip_tables: (C) 2000-2006 Netfilter Core Team
   [   37.184247] PPP generic driver version 2.4.2
   [   37.358031] NET: Registered protocol family 24
   [   37.570517] No dock devices found.
   [   37.688921] input: Power Button (FF) as /class/input/input5
   [   37.689081] ACPI: Power Button (FF) [PWRF]
   [   37.689827] input: Sleep Button (CM) as /class/input/input6
   [   37.689985] ACPI: Sleep Button (CM) [SLPB]
   [   38.688014] Failure registering capabilities with primary security
   module.
   [   38.830038] ppdev: user-space parallel port driver
   [   39.021391] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
   [   39.021397] apm: disabled - APM is not SMP safe.
   [   40.093180] Bluetooth: Core ver 2.11
   [   40.093240] NET: Registered protocol family 31
   [   40.093243] Bluetooth: HCI device and connection manager initialized
   [   40.093246] Bluetooth: HCI socket layer initialized
   [   40.107178] Bluetooth: L2CAP ver 2.8
   [   40.107183] Bluetooth: L2CAP socket layer initialized
   [   40.237039] Bluetooth: RFCOMM socket layer initialized
   [   40.237173] Bluetooth: RFCOMM TTY layer initialized
   [   40.237177] Bluetooth: RFCOMM ver 1.8
   [   46.399778] eth0: no IPv6 routers present
   [ 1428.188157] nvidia: disagrees about version of symbol struct_module
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```

---

### Post by nikgare on 2008-07-27
> I tried System Ad > Hardware Drivers... and it didn't work (I cannot boot into gnome).
I tried envyng-gtk... and it didn't work.

In what way don't they work?
What error messages, if any, are you getting here?

---

### Post by xc3RnbFO8P on 2008-07-27
Mistake

---

### Post by nbayiha on 2008-07-27
rWarrior , i just follow those steps in a clean Hardy Heron instalation , and everything went fine for me.:guitar: 
Give it a try and let me help you if you encounter some problem.

1- first try to install this (unless you have it installed already )
   ```
sudo apt-get install build-essential
```

2- Download from Nvidia the lastest driver of you card, for mine i took this one [http://www.nvidia.com/object/linux_display_ia32_177.13.html](http://www.nvidia.com/object/linux_display_ia32_177.13.html) and i thinks it should be the same for you .

3- Now kill the server (you may want to write in a paper the other command), with this command .
   ```
sudo /etc/init.d/gdm stop 
```
  and then ctrl+alt+f1 

4- Now you should log in and put your password. and go to the folder where you downloaded the nvidia drivers. mine was downloaded in home.

5- now input this command to install it .
   ```
sudo sh NVIDIA* 
```
accept the configuration of the new server and the backing up :D

6-after the installation just start the server 
   ```
sudo /etc/init.d/gdm start 
```

7-Now you should want to edit the Xorg.conf file , for that do this .
  
   Application->System Tool->NVIDIA X Server Settings->X server Display configuration-> Save to X Configuration File(click on it,down on you right)->show preview (copy all the text inside preview).

8- In the terminal input this command. 
    ```
gksudo gedit /etc/X11/xorg.conf 
```
    backup this file, saving it with another name.
     
    and Now Just Paste in the gedit (!!! xorg.conf file!!!)
what you copy in step 7 . Reboot and everything should be fine :popcorn:.

PS: if you had some problem , just let me know in which step .:)

---

### Post by rWarrior on 2008-07-27
By "didn't work", I mean that after the splash screen, ubuntu would fail (repeatedly) to launch gnome, asked me to configure my graphics card, gave an a black blank screen, rebooted, and used the generic driver to launch gnome.



nbayiha, the part I get stuck at is the "sudo sh NVIDIA*" step. The installer seemed to be able to compile the driver, but it could not mount "nvidia.ko" and aborted the installation process, as stated in my first post.

My driver file has the same name has yours, but I got mine at [http://www.nvidia.com/object/linux_display_ia32_173.14.05.html](http://www.nvidia.com/object/linux_display_ia32_173.14.05.html), which should be for the GeForce 8 series.

---

### Post by rWarrior on 2008-07-27
Alright, it's fixed.

It turned out the problem was that my kernel was not updated properly from ubuntu 7.10.

So I used the hardy.py script found somewhere on this forum to get the latest kernel, removed all old kernel from /lib/modules and /boot, (sudo grub-update to update the boot screen), and rebooted.

uname -r then gave me the right release version: 2.6.24-19-generic (It was giving me 2.6.22 before...)

I ran the installer from nvidia, and this time it didn't complain that the kernel source did not match the actually installed kernel. I re-started gnome, fixed the resolution, and it's all good.

P.S. I accidentally pressed "cntrl+r", which seemed to zoom in the screen, with panning enabled. I couldn't find a way to reverse this except by rebooting... How do you get out of that zoom in mode?

Thanks for all your help.

---

### Post by vandalous03 on 2008-07-30
People i really need your help...
I'm facing a similar situation.Here's the case:

I made a fresh install with Ubuntu 8.04.1.I tried to install the nvidia drivers with the nvidia method.Though it seems to be installed flawlessly after the restart the monitor turns off or it turns to black screen with no sound or anything to saw something that works in the backgorund.I ve even tried th EnvyNG and the restricted drivers manger but no solution to my problem.Sometimes when i run the recovery mode and an xfix my system return in safe mode and the resolution is low!
This situation is awful at least...!I think i almost tried everything.I ve used several different drivers older beta, and newer version wit no results.Today i even installed the latest driver but still no good results.Fresh install definetly didn'y solve this and i really hope that there is a solution to this problem cause i really enjoy ubuntu as my desktop OS!

If anyone could help please,i would appreciate it!
thanx in advance!

*Specs: Gigabyte Nvidia Geforce 8600GT 512 MB// Ubuntu 8.04// Amd A64 3500+//MSI Neo4 Platinum mobo// 1GB RAM...!

---

### Post by nbayiha on 2008-07-31
Did you try what i show before in the thread ?
If it didnt work so try this one


[http://ubuntuforums.org/showthread.php?t=765985&page=3](http://ubuntuforums.org/showthread.php?t=765985&page=3) 
and report here if you still have the same problem .

---

### Post by vandalous03 on 2008-08-03
My friend i followed your guide step by step but unfortunately there were no good results.Monitor still turn's off after reboot.
Any other suggestions?

---

### Post by ldgilman on 2008-08-03
nbayiha - I have an Nvidia 6900 which only gives me a max of 800x600, I need at least 1024x768. 
  I am assuming the instruction you gave to rWarrior would be the same for me. I followed them and things went well till step 6. When I turned the X Server back on there was some system thinking and then I lost video. My monitor let me know that "Video Mode was not supported". A Shut Down Restart did not fix the problem. I was able to fix the problem at reboot by having the system fix the X Server. What am I missing, according to the NVIDIA site the 173.14.12 supports 6900 le.[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)
  I used NVIDIA-Linux-x86-173.14.12-pkg1.run.
  I am a complete "newbe" at Ubuntu 8.04. Not including the system setup, it took me the better part of 4 hours to finally get the NVIDIA driver to load and I was excited to have won that round. 
  Any ideas as to what I need to do or undo??[http://ubuntuforums.org/images/smilies/eusa_pray.gif](http://ubuntuforums.org/images/smilies/eusa_pray.gif)

Many thanks in advance

---

### Post by hellknight_mnd on 2008-08-03
Mine was installed instantly.. i'm also using 8600 GT on an AMD processor with Ubuntu 64-bit.. it gave me no problems..

---

### Post by hellknight_mnd on 2008-08-03
and I think that you might also need Linux kernel sources while manually installing the NVIDIA drivers.. I used to do the same on openSUSE 11.. I selected the Linux-kernel-source package during the installation of the system.. then I switched to terminal and went to init 3 and executed the sh NVIDIA* command.. sax2 -r NVIDIA was also required there.. don't know whether sax2 will be required on Ubuntu as it is openSUSE specific..

---

### Post by nbayiha on 2008-08-05
Sorry guys i was off for a while. Now i am back.
I guess in a couple of days i will make a thread about how to correctly install Nvidia graphic card series 8 and other while i collect enough information, cause i think a lot of us right here had a problem installing those driver.

Edit : Here is the link [http://ubuntuforums.org/showthread.php?p=5534401#post5534401](http://ubuntuforums.org/showthread.php?p=5534401#post5534401)

---

