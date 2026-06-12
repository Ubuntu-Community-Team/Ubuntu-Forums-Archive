---
title: "Help! Cannot Install BETA Nvidia Drivers on Gutsy Gibbon..."
date: 2007-10-27
forum: Multimedia &amp; Video
---

### Post by Slaco on 2007-10-27
As the title says, I cannot manage to install the BETA Nvidia drivers downloaded from their website. In the part where it says it is compiling a kernel module, the progress bar would reach 100%, then it would spontaneously fail with a generic error. Here is the log of the install: 

```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Fri Oct 26 22:44:50 2007

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
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: No)
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.22-14-generic/build'
-> Kernel output path: '/lib/modules/2.6.22-14-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
   rm -f -f nv.o nv-vm.o os-agp.o os-interface.o os-registry.o nv-i2c.o nv.o nv
   -vm.o os-agp.o os-interface.o os-registry.o nv-i2c.o nvidia.mod.o
   rm -f -f build-in.o nv-linux.o *.d .*.{cmd,flags}
   rm -f -f nvidia.{o,ko,mod.{o,c}} nv_compiler.h *~
   rm -f -f stprof stprof.o symtab.h Modules.symvers
   rm -f -rf .tmp_versions
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.22-14-gener
   ic/build SYSOUT=/lib/modules/2.6.22-14-generic/build'...
   
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.22-14-generic/build SUBDIRS
   =/tmp/selfgz5635/NVIDIA-Linux-x86-1.0-9625-pkg1/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz5635/NVIDIA-Linux-x86-1.0-9625-pkg1/usr/src/nv/.tmp_vers
   ions
   rm -f /tmp/selfgz5635/NVIDIA-Linux-x86-1.0-9625-pkg1/usr/src/nv/.tmp_version
   s/*
   make -f scripts/Makefile.build obj=/tmp/selfgz5635/NVIDIA-Linux-x86-1.0-9625
   -pkg1/usr/src/nv
   echo \#define NV_COMPILER \"`cc -v 2>&1 | tail -n 1`\" > /tmp/selfgz5635/NVI
   DIA-Linux-x86-1.0-9625-pkg1/usr/src/nv/nv_compiler.h
     cc -Wp,-MD,/tmp/selfgz5635/NVIDIA-Linux-x86-1.0-9625-pkg1/usr/src/nv/.nv.o
   .d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.3/include -D__KERNEL_
   _ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-protot
   ypes -Wno-trigraphs -fno-strict-aliasing -fno-common -O2 -pipe -msoft-float 
   -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2  -march=i586 -m
   tune=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-i386/
   mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-aft
   er-statement -Wno-pointer-sign -I/tmp/selfgz5635/NVIDIA-Linux-x86-1.0-9625-p
   kg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subsc
   ripts -Wparentheses -Wpointer-arith  -Wno-multichar  -Werror -O -fno-common 
   -msoft-float -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_
   NAMES -D__KERNEL__ -DMODULE  -DNVRM -DNV_MAJOR_VERSION=1 -DNV_MINOR_VERSION=
   0 -DNV_PATCHLEVEL=9625  -UDEBUG -U_DEBUG -DNDEBUG -DNV_SIGNAL_STRUCT_RLIM -D
   NV_MULTIPLE_BRIDGE_AGPGART_PRESENT -DNV_PCI_GET_CLASS_PRESENT -DNV_SYSCTL_MA
   X_MAP_COUNT_PRESENT -DNV_PM_MESSAGE_T_PRESENT -DNV_PCI_CHOOSE_STATE_PRESENT 
   -DNV_VM_INSERT_
   PAGE_PRESENT -DNV_OLD_MM_KGDB_BREAKPOINT_PRESENT -DNV_REMAP_PFN_RANGE_PRESEN
   T -DNV_CHANGE_PAGE_ATTR_PRESENT -DNV_VMAP_4_PRESENT  -DMODULE -D"KBUILD_STR(
   s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KBUILD_STR(nvid
   ia)" -c -o /tmp/selfgz5635/NVIDIA-Linux-x86-1.0-9625-pkg1/usr/src/nv/.tmp_nv
   .o /tmp/selfgz5635/NVIDIA-Linux-x86-1.0-9625-pkg1/usr/src/nv/nv.c
   In file included from /tmp/selfgz5635/NVIDIA-Linux-x86-1.0-9625-pkg1/usr/src
   /nv/nv.c:14:
   /tmp/selfgz5635/NVIDIA-Linux-x86-1.0-9625-pkg1/usr/src/nv/nv-linux.h:17:26: 
   error: linux/config.h: No such file or directory
   In file included from include/linux/list.h:8,
                    from include/linux/wait.h:22,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:59,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5635/NVIDIA-Linux-x86-1.0-9625-pkg1/usr/src
   /nv/nv-linux.h:19,
                    from /tmp/selfgz5635/NVIDIA-Linux-x86-1.0-9625-pkg1/usr/src
   /nv/nv.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
   /tmp/selfgz5635/NVIDIA-Linux-x86-1.0-9625-pkg1/usr/src/nv/nv.c: At top level
   :
   /tmp/selfgz5635/NVIDIA-Linux-x86-1.0-9625-pkg1/usr/src/nv/nv.c:110: warning:
   ‘kmem_cache_t’ is deprecated
   /tmp/selfgz5635/NVIDIA-Linux-x86-1.0-9625-pkg1/usr/src/nv/nv.c: In function 
   ‘nv_kern_open’:
   /tmp/selfgz5635/NVIDIA-Linux-x86-1.0-9625-pkg1/usr/src/nv/nv.c:1844: warning
   : ‘deprecated_irq_flag’ is deprecated (declared at include/linux/interru
   pt.h:66)
   /tmp/selfgz5635/NVIDIA-Linux-x86-1.0-9625-pkg1/usr/src/nv/nv.c:1844: warning
   : ‘deprecated_irq_flag’ is deprecated (declared at include/linux/interru
   pt.h:66)
   /tmp/selfgz5635/NVIDIA-Linux-x86-1.0-9625-pkg1/usr/src/nv/nv.c:1845: warning
   : passing argument 2 of ‘request_irq’ from incompatible pointer type
   make[3]: *** [/tmp/selfgz5635/NVIDIA-Linux-x86-1.0-9625-pkg1/usr/src/nv/nv.o
   ] Error 1
   make[2]: *** [_module_/tmp/selfgz5635/NVIDIA-Linux-x86-1.0-9625-pkg1/usr/src
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
       driver download page at www.nvidia.com.
```

Any help would be much appreciated!

---

### Post by Slaco on 2007-10-27
Anyone please?!?

---

