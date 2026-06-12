---
title: "nvidia.ko failed to build!"
date: 2009-06-01
forum: Multimedia Software
---

### Post by StuartZ on 2009-06-01
On a clean install of Jaunty I'm having a hair pulling experience installing an nvidia driver for Geforce4.  I've done the following:

build essentials
downloaded the latest pkg from nvdia 96.43.11
ctr+alt=F1
cd /to driver folder
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-86-96.43.11-pkg1.run

After accepting license etc. it goes thru to the end and fails

Is this driver supposed to work with this kernel or is there a patch?  I've search Ubuntu and the web all morning to get to this point.

nvida-installer.log below

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Mon Jun  1 11:51:35 2009
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
-> Installing NVIDIA driver version 96.43.11.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
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
   selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src/nv/.tmp_vers
   ions ; rm -f /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src/nv/.tmp_
   versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11
   -pkg1/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src/nv/.nv.o
   .d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -D__KERNEL_
   _  -Iinclude  -I/usr/src/linux-headers-2.6.28-3-rt/arch/x86/include -include
   include/linux/autoconf.h -Iubuntu/in
   clude  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing
   -fno-common -Werror-implicit-function-declaration -O2 -m32 -msoft-float -mre
   gparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=
   generic -Wa,-mtune=generic32 -ffreestanding -pipe -Wno-sign-compare -fno-asy
   nchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iarch/x86/in
   clude/asm/mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-opt
   imize-sibling-calls -Wdeclaration-after-statement -Wno-pointer-sign -fwrapv 
   -I/tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src/nv -Wall -Wimplicit
   -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-ar
   ith -Wno-multichar -Werror -MD -Wsign-compare -Wno-cast-qual -Wno-error -D_L
   OOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"96.43.1
   1\" -UDEBUG -U_DEBUG -DNDEBUG -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENA
   ME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz
   4569/NVIDIA-Linux-x86-96.43.11-pkg
   1/usr/src/nv/.tmp_nv.o /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/sr
   c/nv/nv.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/nv-linux.h:19,
                    from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/nv.c:14:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h: In functio
   n ‘set_bit’:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h:60: warning
   : pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h: In functio
   n ‘clear_bit’:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h:97: warning
   : pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/nv-linux.h:19,
                    from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/nv.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/nv-linux.h:19,
                    from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/nv.c:14:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2124: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/nv-linux.h:85,
                    from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/nv.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/hardirq_32.h:5,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/hardirq.h:2,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/nv-linux.h:86,
                    from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/nv.c:14:
   include/linux/irq.h: In function ‘irq_to_desc’:
   include/linux/irq.h:203: warning: comparison between signed and unsigned
   In file included from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/nv-linux.h:112,
                    from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/nv.c:14:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src/nv/.nv-v
   m.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -D__KERN
   EL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-3-rt/arch/x86/include -incl
   ude include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-protot
   ypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-functi
   on-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mprefe
   rred-stack-boundary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -ffree
   standing -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -m
   no-mmx -mno-sse2 -mno-3dnow -Iarch/x86/include/asm/mach-default -fno-stack-p
   rotector -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-a
   fter-statement -Wno-pointer-sign -fwrapv -I/tmp/selfgz4569/NVIDIA-Linux-x86-
   96.43.11-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wform
   at -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -M
   D -Wsign-compare -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -D__KERNEL_
   _ -DMODULE -DNVRM -DNV_VERSION_STRING=\"96.43.11\" -UDEBUG -U_DEBUG -DNDEBUG
   -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_vm)"  -D"KBUI
   LD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz4569/NVIDIA-Linux-x86-96.43
   .11-pkg1/usr/src/nv/.tmp_nv-vm.o /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-p
   kg1/usr/src/nv/nv-vm.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/nv-linux.h:19,
                    from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/nv-vm.c:14:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h: In functio
   n ‘set_bit’:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h:60: warning
   : pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h: In functio
   n ‘clear_bit’:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h:97: warning
   : pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/nv-linux.h:19,
                    from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/nv-vm.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/nv-linux.h:19,
                    from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/nv-vm.c:14:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2124: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/nv-linux.h:85,
                    from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/nv-vm.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/hardirq_32.h:5,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/hardirq.h:2,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/nv-linux.h:86,
                    from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/nv-vm.c:14:
   include/linux/irq.h: In function ‘irq_to_desc’:
   include/linux/irq.h:203: warning: comparison between signed and unsigned
   In file included from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/nv-linux.h:112,
                    from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/nv-vm.c:14:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src/nv/.os-a
   gp.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -D__KER
   NEL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-3-rt/arch/x86/include -inc
   lude include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-proto
   types -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-funct
   ion-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpref
   erred-stack-boundary=2 -march=i586 -mtu
   ne=generic -Wa,-mtune=generic32 -ffreestanding -pipe -Wno-sign-compare -fno-
   asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iarch/x86
   /include/asm/mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-
   optimize-sibling-calls -Wdeclaration-after-statement -Wno-pointer-sign -fwra
   pv -I/tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src/nv -Wall -Wimpli
   cit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointe
   r-arith -Wno-multichar -Werror -MD -Wsign-compare -Wno-cast-qual -Wno-error 
   -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"96.
   43.11\" -UDEBUG -U_DEBUG -DNDEBUG -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BA
   SENAME=KBUILD_STR(os_agp)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tm
   p/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src/nv/.tmp_os-agp.o /tmp/se
   lfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src/nv/os-agp.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/nv-linux.h:19,
                    from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/os-agp.c:24:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h: In functio
   n ‘set_bit’:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h:60: warning
   : pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h: In functio
   n ‘clear_bit’:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h:97: warning
   : pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/nv-linux.h:19,
                    from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/os-agp.c:24:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/nv-linux.h:19,
                    from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/os-agp.c:24:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2124: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/nv-linux.h:85,
                    from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/os-agp.c:24:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/hardirq_32.h:5,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/hardirq.h:2,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/nv-linux.h:86,
                    from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/os-agp.c:24:
   include/linux/irq.h: In function ‘irq_to_desc’:
   include/linux/irq.h:203: warning: comparison between signed and unsigned
   In file included from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/nv-linux.h:112,
                    from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/os-agp.c:24:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src/nv/.os-i
   nterface.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -
   D__KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-3-rt/arch/x86/includ
   e -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict
   -prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit
   -function-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return 
   -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32
   -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-
   sse -mno-mmx -mno-sse2 -mno-3dnow -Iarch/x86/include/asm/mach-default -fno-s
   tack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclara
   tion-after-statement -Wno-pointer-sign -fwrapv -I/tmp/selfgz4569/NVIDIA-Linu
   x-x86-96.43.11-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wfor
   mat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -
   MD -Wsign-compare -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -D__KERNEL
   __ -DMODULE -DNVRM -DNV_VERSION_
   STRING=\"96.43.11\" -UDEBUG -U_DEBUG -DNDEBUG -DMODULE -D"KBUILD_STR(s)=#s" 
   -D"KBUILD_BASENAME=KBUILD_STR(os_interface)"  -D"KBUILD_MODNAME=KBUILD_STR(n
   vidia)"  -c -o /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src/nv/.tm
   p_os-interface.o /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src/nv/o
   s-interface.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/nv-linux.h:19,
                    from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/os-interface.c:26:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h: In functio
   n ‘set_bit’:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h:60: warning
   : pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h: In functio
   n ‘clear_bit’:
   /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h:97: warning
   : pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/nv-linux.h:19,
                    from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/os-interface.c:26:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/nv-linux.h:19,
                    from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/os-interface.c:26:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2124: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/nv-linux.h:85,
                    from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/os-interface.c:26:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/hardirq_32.h:5,
                    from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/as
   m/hardirq.h:2,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/nv-linux.h:86,
                    from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/os-interface.c:26:
   include/linux/irq.h: In function ‘irq_to_desc’:
   include/linux/irq.h:203: warning: comparison between signed and unsigned
   In file included from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/nv-linux.h:112,
                    from /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv/os-interface.c:26:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src/nv/os-interface.c: In
   function ‘os_alloc_sema’:
   /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src/nv/os-interface.c:104
   : error: incompatible types in assignment
   /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src/nv/os-interface.c: In
   function ‘os_acquire_sema’:
   /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src/nv/os-interface.c:143
   : warning: passing argument 1 of ‘_spin_lock_irqsave’ from incompatible 
   pointer type
   /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src/nv/os-interface.c:147
   : warning: passing argument 1 of ‘_spin_unlock_irqrestore’ from incompat
   ible pointer type
   /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src/nv/os-interface.c:154
   : warning: passing argument 1 of ‘_spin_unlock_irqrestore’ from incompat
   ible pointer type
   /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src/nv/os-interface.c: In
   function ‘os_cond_acquire_sema’:
   /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src/nv/os-interface.c:177
   : warning: passing argument 1 of ‘_spin_lock_irqsave’ from incompatible 
   pointer type
   /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src/nv/os-interface.c:180
   : warning: passing argument 1 of ‘_spin_unlock_irqrestore’ from incompat
   ible pointer type
   /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src/nv/os-interface.c:187
   : warning: passing argument 1 of ‘_spin_unlock_irqrestore’ from incompat
   ible pointer type
   /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src/nv/os-interface.c: In
   function ‘os_release_sema’:
   /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src/nv/os-interface.c:211
   : warning: passing argument 1 of ‘_spin_lock_irqsave’ from incompatible 
   pointer type
   /tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src/nv/os-interface.c:222
   : warning: passing argument 1 of ‘_spin_unlock_irqrestore’ from incompat
   ible pointer type
   make[3]: *** [/tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src/nv/os-i
   nterface.o] Error 1
   make[2]: *** [_module_/tmp/selfgz4569/NVIDIA-Linux-x86-96.43.11-pkg1/usr/src
   /nv] Error 2
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

---

### Post by StuartZ on 2009-06-01
Help?

---

