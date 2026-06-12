---
title: "Can't Install newest NVIDIA driver on realtime kernel"
date: 2009-09-28
forum: Multimedia Software
---

### Post by Mike_IronFist on 2009-09-28
Okay, so I have a 64-bit install of Ubuntu Studio (Jaunty) and I've easily installed the newest NVIDIA drivers (the ones available on the website) before. 

However, when booting from an RT kernel, I can't install the drivers! Installation starts and when it has to "compile the kernel module" it gets to 100%, then says "Error: Could not build kernel module". The installation then ends.

Has anyone had this problem before? Can anyone help me? I really don't wanna use the terribly slow version177 driver or the buggy, crashing version180 driver included in the Repos.

**EDIT:** Here's the installation log:
```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Mon Sep 28 23:12:55 2009
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
  force compat32 tls      : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  compat32 install chroot : (not specified)
  compat32 install prefix : (not specified)
  compat32 install libdir : (not specified)
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
-> Installing NVIDIA driver version 185.18.36.
-> There appears to already be a driver installed on your system (version: 185.
   18.36).  As part of installing this driver (version: 185.18.36), the existin
   g driver will be uninstalled.  Are you sure you want to continue? ('no' will
   abort installation) (Answer: Yes)
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: No)
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.28-3-rt/build'
-> Kernel output path: '/lib/modules/2.6.28-3-rt/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.28-3-rt/bui
   ld SYSOUT=/lib/modules/2.6.28-3-rt/build'...
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.28-3-rt/build SUBDIRS=/tmp/
   selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr/src/nv/.tmp_
   versions ; rm -f /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr/src/
   nv/.tmp_versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz6272/NVIDIA-Linux-x86_64-185.1
   8.36-pkg2/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr/src/nv/.
   nv.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.3.3/include -D__K
   ERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-3-rt/arch/x86/include -i
   nclude include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-pro
   totypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-fun
   ction-declaration -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -fun
   it-at-a-time -maccumulate-outgoing-args -pipe -Wno-sign-compare -fno-asynchr
   onous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iarch/x86/includ
   e/asm/mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-optimiz
   e-sibling-calls -Wdeclaration-after-statement -Wno-pointer-sign -fwrapv -I/t
   mp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr/src/nv -Wall -Wimplicit
   -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-ar
   ith -Wno-multichar -Werror -mcmodel=kernel -mno-red-zone -fno-defer-pop -MD 
   -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_V
   ERSION_STRING=\"185.18.36\" -UDEBUG -U_DEBUG -DNDEBUG -DMODULE -D"KBUILD_STR
   (s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KBUILD_STR(nvi
   dia)"  -c -o /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.
   36-pkg2/usr/src/nv/.tmp_nv.o /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-p
   kg2/usr/src/nv/nv.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/nv-linux.h:19,
                    from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/nv.c:14:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h: In functio
   n &#8216;set_bit&#8217;:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h:60: warning
   : pointer of type &#8216;void *&#8217; used in arithmetic
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h: In functio
   n &#8216;clear_bit&#8217;:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h:97: warning
   : pointer of type &#8216;void *&#8217; used in arithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/nv-linux.h:19,
                    from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/nv.c:14:
   include/linux/sched.h: In function &#8216;object_is_on_stack&#8217;:
   include/linux/sched.h:2124: warning: pointer of type &#8216;void *&#8217; used in ar
   ithmetic
   In file included from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/nv-linux.h:86,
                    from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/nv.c:14:
   include/linux/scatterlist.h: In function &#8216;sg_virt&#8217;:
   include/linux/scatterlist.h:199: warning: pointer of type &#8216;void *&#8217; used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/hardirq_64.h:5,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/hardirq.h:4,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/nv-linux.h:87,
                    from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/nv.c:14:
   include/linux/irq.h: In function &#8216;irq_to_desc&#8217;:
   include/linux/irq.h:203: warning: comparison between signed and unsigned
   In file included from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/nv-linux.h:113,
                    from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/nv.c:14:
   include/linux/highmem.h: In function &#8216;zero_user_segments&#8217;:
   include/linux/highmem.h:136: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   In file included from include/linux/compat.h:14,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/mtrr.h:141,
                    from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/nv-linux.h:142,
                    from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/nv.c:14:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/compat.h: In functio
   n &#8216;compat_alloc_user_space&#8217;:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/compat.h:210: warnin
   g: pointer of type &#8216;void *&#8217; used in arithmetic
     cc -Wp,-MD,/tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr/src/nv/.
   nv-vm.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.3.3/include -D
   __KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-3-rt/arch/x86/include
   -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-p
   rototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-f
   unction-declaration -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -f
   unit-at-a-time -maccumulate-outgoing-args -
   pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mn
   o-sse2 -mno-3dnow -Iarch/x86/include/asm/mach-default -fno-stack-protector -
   fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-after-state
   ment -Wno-pointer-sign -fwrapv -I/tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.
   36-pkg2/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-s
   ubscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -mcmodel=kern
   el -mno-red-zone -fno-defer-pop -MD -Wsign-compare -Wno-cast-qual -Wno-error
   -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"185.18.36\" -UDEBUG -U_DE
   BUG -DNDEBUG -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_
   vm)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz6272/NVIDIA-Li
   nux-x86_64-185.18.36-pkg2/usr/src/nv/.tmp_nv-vm.o /tmp/selfgz6272/NVIDIA-Lin
   ux-x86_64-185.18.36-pkg2/usr/src/nv/nv-vm.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/nv-linux.h:19,
                    from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/nv-vm.c:14:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h: In functio
   n &#8216;set_bit&#8217;:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h:60: warning
   : pointer of type &#8216;void *&#8217; used in arithmetic
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h: In functio
   n &#8216;clear_bit&#8217;:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h:97: warning
   : pointer of type &#8216;void *&#8217; used in arithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/nv-linux.h:19,
                    from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/nv-vm.c:14:
   include/linux/sched.h: In function &#8216;object_is_on_stack&#8217;:
   include/linux/sched.h:2124: warning: pointer of type &#8216;void *&#8217; used in ar
   ithmetic
   In file included from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/nv-linux.h:86,
                    from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/nv-vm.c:14:
   include/linux/scatterlist.h: In function &#8216;sg_virt&#8217;:
   include/linux/scatterlist.h:199: warning: pointer of type &#8216;void *&#8217; used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/hardirq_64.h:5,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/hardirq.h:4,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/nv-linux.h:87,
                    from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/nv-vm.c:14:
   include/linux/irq.h: In function &#8216;irq_to_desc&#8217;:
   include/linux/irq.h:203: warning: comparison between signed and unsigned
   In file included from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/nv-linux.h:113,
                    from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/nv-vm.c:14:
   include/linux/highmem.h: In function &#8216;zero_user_segments&#8217;:
   include/linux/highmem.h:136: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   In file included from include/linux/compat.h:14,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/mtrr.h:141,
                    from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/nv-linux.h:142,
                    from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/nv-vm.c:14:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/compat.h: In functio
   n &#8216;compat_alloc_user_space&#8217;:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/compat.h:210: warnin
   g: pointer of type &#8216;void *&#8217; used in arithmetic
     cc -Wp,-MD,/tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr/src/nv/.
   os-agp.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.3.3/include -
   D__KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-3-rt/arch/x86/includ
   e -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict
   -prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit
   -function-declaration -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel 
   -funit-at-a-time -maccumulate-outgoing-args -pipe -Wno-sign-compare -fno-asy
   nchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iarch/x86/in
   clude/asm/mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-opt
   imize-sibling-calls -Wdeclaration-aft
   er-statement -Wno-pointer-sign -fwrapv -I/tmp/selfgz6272/NVIDIA-Linux-x86_64
   -185.18.36-pkg2/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat 
   -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -mcmo
   del=kernel -mno-red-zone -fno-defer-pop -MD -Wsign-compare -Wno-cast-qual -W
   no-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"185.18.36\" -UDE
   BUG -U_DEBUG -DNDEBUG -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUIL
   D_STR(os_agp)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz6272
   /NVIDIA-Linux-x86_64-185.18.36-pkg2/usr/src/nv/.tmp_os-agp.o /tmp/selfgz6272
   /NVIDIA-Linux-x86_64-185.18.36-pkg2/usr/src/nv/os-agp.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/nv-linux.h:19,
                    from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/os-agp.c:24:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h: In functio
   n &#8216;set_bit&#8217;:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h:60: warning
   : pointer of type &#8216;void *&#8217; used in arithmetic
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h: In functio
   n &#8216;clear_bit&#8217;:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h:97: warning
   : pointer of type &#8216;void *&#8217; used in arithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/nv-linux.h:19,
                    from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/os-agp.c:24:
   include/linux/sched.h: In function &#8216;object_is_on_stack&#8217;:
   include/linux/sched.h:2124: warning: pointer of type &#8216;void *&#8217; used in ar
   ithmetic
   In file included from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/nv-linux.h:86,
                    from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/os-agp.c:24:
   include/linux/scatterlist.h: In function &#8216;sg_virt&#8217;:
   include/linux/scatterlist.h:199: warning: pointer of type &#8216;void *&#8217; used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/hardirq_64.h:5,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/hardirq.h:4,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/nv-linux.h:87,
                    from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/os-agp.c:24:
   include/linux/irq.h: In function &#8216;irq_to_desc&#8217;:
   include/linux/irq.h:203: warning: comparison between signed and unsigned
   In file included from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/nv-linux.h:113,
                    from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/os-agp.c:24:
   include/linux/highmem.h: In function &#8216;zero_user_segments&#8217;:
   include/linux/highmem.h:136: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   In file included from include/linux/compat.h:14,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/mtrr.h:141,
                    from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/nv-linux.h:142,
                    from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/os-agp.c:24:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/compat.h: In functio
   n &#8216;compat_alloc_user_space&#8217;:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/compat.h:210: warnin
   g: pointer of type &#8216;void *&#8217; used in arithmetic
     cc -Wp,-MD,/tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr/src/nv/.
   os-interface.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.3.3/inc
   lude -D__KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-3-rt/arch/x86/
   include -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -W
   strict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-im
   plicit-function-declaration -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=k
   ernel -funit-at-a-time -maccumulate-outgoing-args -pipe -Wno-sign-compare -f
   no-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iarch/
   x86/include/asm/mach-default -fno-stack-protector -fno-omit-frame-pointer -f
   no-optimize-sibling-calls -Wdeclaration-after-statement -Wno-pointer-sign -f
   wrapv -I/tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr/src/nv -Wall 
   -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -
   Wpointer-arith -Wno-
   multichar -Werror -mcmodel=kernel -mno-red-zone -fno-defer-pop -MD -Wsign-co
   mpare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_ST
   RING=\"185.18.36\" -UDEBUG -U_DEBUG -DNDEBUG -DMODULE -D"KBUILD_STR(s)=#s" -
   D"KBUILD_BASENAME=KBUILD_STR(os_interface)"  -D"KBUILD_MODNAME=KBUILD_STR(nv
   idia)"  -c -o /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr/src/nv/
   .tmp_os-interface.o /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr/s
   rc/nv/os-interface.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/nv-linux.h:19,
                    from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/os-interface.c:26:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h: In functio
   n &#8216;set_bit&#8217;:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h:60: warning
   : pointer of type &#8216;void *&#8217; used in arithmetic
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h: In functio
   n &#8216;clear_bit&#8217;:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h:97: warning
   : pointer of type &#8216;void *&#8217; used in arithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/nv-linux.h:19,
                    from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/os-interface.c:26:
   include/linux/sched.h: In function &#8216;object_is_on_stack&#8217;:
   include/linux/sched.h:2124: warning: pointer of type &#8216;void *&#8217; used in ar
   ithmetic
   In file included from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/nv-linux.h:86,
                    from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/os-interface.c:26:
   include/linux/scatterlist.h: In function &#8216;sg_virt&#8217;:
   include/linux/scatterlist.h:199: warning: pointer of type &#8216;void *&#8217; used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/hardirq_64.h:5,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/hardirq.h:4,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/nv-linux.h:87,
                    from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/os-interface.c:26:
   include/linux/irq.h: In function &#8216;irq_to_desc&#8217;:
   include/linux/irq.h:203: warning: comparison between signed and unsigned
   In file included from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/nv-linux.h:113,
                    from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/os-interface.c:26:
   include/linux/highmem.h: In function &#8216;zero_user_segments&#8217;:
   include/linux/highmem.h:136: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   In file included from include/linux/compat.h:14,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/mtrr.h:141,
                    from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/nv-linux.h:142,
                    from /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv/os-interface.c:26:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/compat.h: In functio
   n &#8216;compat_alloc_user_space&#8217;:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/compat.h:210: warnin
   g: pointer of type &#8216;void *&#8217; used in arithmetic
   /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr/src/nv/os-interface.c
   : In function &#8216;os_alloc_sema&#8217;:
   /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr/src/nv/os-interface.c
   :130: error: incompatible types in assignment
   /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr/src/nv/os-interface.c
   : In function &#8216;os_acquire_sema&#8217;:
   /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr/src/nv/os-interface.c
   :174: warning: passing argument 1 of &#8216;_spin_lock_irqsave&#8217; from incompati
   ble pointer type
   /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr/src/nv/os-interface.c
   :178: warning: passing argument 1 of &#8216;_spin_unlock_irqrestore&#8217; from inco
   mpatible pointer type
   /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr/src/nv/os-interface.c
   :185: warning: passing argument 1 of &#8216;_spin_unlock_irqrestore&#8217; from inco
   mpatible pointer type
   /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr/src/nv/os-interface.c
   : In function &#8216;os_cond_acquire_sema&#8217;:
   /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr/src/nv/os-interface.c
   :208: warning: passing argument 1 of &#8216;_spin_lock_irqsave&#8217; from incompati
   ble pointer type
   /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr/src/nv/os-interface.c
   :211: warning: passing argument 1 of &#8216;_spin_unlock_irqrestore&#8217; from inco
   mpatible pointer type
   /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr/src/nv/os-interface.c
   :218: warning: passing argument 1 of &#8216;_spin_unlock_irqrestore&#8217; from inco
   mpatible pointer type
   /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr/src/nv/os-interface.c
   : In function &#8216;os_release_sema&#8217;:
   /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr/src/nv/os-interface.c
   :242: warning: passing argument 1 of &#8216;_spin_lock_irqsave&#8217; from incompati
   ble pointer type
   /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr/src/nv/os-interface.c
   :253: warning: passing argument 1 of &#8216;_spin_unlock_irqrestore&#8217; from inco
   mpatible pointer type
   /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr/src/nv/os-interface.c
   : In function &#8216;os_acquire_spinlock&#8217;:
   /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr/src/nv/os-interface.c
   :1322: warning: passing argument 1 of &#8216;_spin_lock_irqsave&#8217; from incompat
   ible pointer type
   /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr/src/nv/os-interface.c
   : In function &#8216;os_release_spinlock&#8217;:
   /tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr/src/nv/os-interface.c
   :1333: warning: passing argument 1 of &#8216;_spin_unlock_irqrestore&#8217; from inc
   ompatible pointer type
   make[3]: *** [/tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr/src/nv/
   os-interface.o] Error 1
   make[2]: *** [_module_/tmp/selfgz6272/NVIDIA-Linux-x86_64-185.18.36-pkg2/usr
   /src/nv] Error 2
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

### Post by renkinjutsu on 2009-09-28
Have you installed your kernel-headers?

---

### Post by Mike_IronFist on 2009-09-28
> **renkinjutsu said:**
> Have you installed your kernel-headers?

Yes, I have.

However, I got the driver running for a non-realtime kernel WITHOUT any headers installed. So that doesn't appear to be the problem.

I'll post a log file in my original post.

---

### Post by Mike_IronFist on 2009-09-29
Bump

---

### Post by Arup on 2009-09-29
Only the nvidia driver available through hardware applet has the rt patch, the one from nvidia doesn't have any rt patch so you can't install it on your Ubuntu Studio PC.

---

