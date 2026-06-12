---
title: "Troubles installing nvidia drivers from nvidia.com"
date: 2005-12-30
forum: Multimedia &amp; Video
---

### Post by Sai on 2005-12-30
Hi!
I have troubles installing nvidia drivers from nvidia.com. I want to try to install nvidia drivers 6629 version, because drivers from repository freezes my xorg with RenderAccel "On".
I've downloaded NVIDIA-Linux-x86-1.0-6629-pkg1.run, installed build-essentials, gcc-3.4, kernel sources and headers (2.6.12.10), removed all nvidia stuff from my system (nvidia-kernel-common and restricted modules).
After that i switch to console, stop kdm (i use kubuntu), `CC=gcc-3.4`, `export CC`, and run `sudo sh NVIDIA-Linux-x86-1.0-6629-pkg1.run`. But when it comes to compile kernel module installer gives me an error and quits.
Here are my /var/log/nvidia-installer.log:
```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Fri Dec 30 23:33:53 2005

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  no precompiled interface: false
  no ncurses color        : false
  query latest driver ver : false
  OpenGL header files     : false
  no questions            : false
  silent                  : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : /usr/X11R6
  OpenGL install prefix   : /usr
  compat32 install prefix : (not specified)
  installer install prefix: /usr
  utility install prefix  : /usr
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
-> Kernel source path: '/lib/modules/2.6.12-10-386/build'
-> Performing CC test with CC="/usr/bin/gcc-3.4".
-> Performing rivafb check.
-> Performing rivafb module check.
WARNING: Your kernel was configured to include rivafb support as
         a loadable kernel module.
         
         The rivafb driver conflicts with the NVIDIA driver; the
         NVIDIA kernel module will still be built and installed,
         but be aware that the NVIDIA driver will not be able to
         function properly if the rivafb module is loaded!
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
   rm -f -f nv.o nv-vm.o os-agp.o os-interface.o os-registry.o nv.o nv-vm.o os-
   agp.o os-interface.o os-registry.o nvidia.mod.o
   rm -f -f build-in.o nv-linux.o *.d .*.{cmd,flags}
   rm -f -f nvidia.{o,ko,mod.{o,c}} nv_compiler.h *~
   rm -f -rf .tmp_versions
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.12-10-386/b
   uild SYSOUT=/lib/modules/2.6.12-10-386/build'...
   Your kernel was configured to include rivafb support as
   a loadable kernel module.
   
   The rivafb driver conflicts with the NVIDIA driver; the
   NVIDIA kernel module will still be built and installed,
   but be aware that the NVIDIA driver will not be able to
   function properly if the rivafb module is loaded!
   
   *** Failed rivafb module sanity check, but continuing! ***
   
   
   NVIDIA: calling KBUILD...
   make CC=/usr/bin/gcc-3.4  KBUILD_VERBOSE=1 -C /lib/modules/2.6.12-10-386/bui
   ld SUBDIRS=/tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv modules
   mkdir -p /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/.tmp_vers
   ions
   make -f scripts/Makefile.build obj=/tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629
   -pkg1/usr/src/nv
   echo \#define NV_COMPILER \"`/usr/bin/gcc-3.4 -v 2>&1 | tail -n 1`\" > /tmp/
   selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/nv_compiler.h
     /usr/bin/gcc-3.4 -Wp,-MD,/tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/us
   r/src/nv/.nv.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/3.4.5/inclu
   de -D__KERNEL__ -Iinclude  -Wall -Wstrict-prototypes -Wno-trigraphs -fno-str
   ict-aliasing -fno-common -ffreestanding -Os     -fomit-frame-pointer -pipe -
   msoft-float -mpreferred-stack-boundary=2 -fno-unit-at-a-time -march=i386 -Ii
   nclude/asm-i386/mach-default -Wdeclaration-after-statement  -I/tmp/selfgz130
   2/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -
   Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith  -Wno-multi
   char  -Werror -O -fno-common -MD   -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL
   _NAMES -D__KERNEL__ -DMODULE  -DNTRM -D_GNU_SOURCE -D_LOOSE_KERNEL_NAMES -D_
   _KERNEL__ -DMODULE  -DNV_MAJOR_VERSION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVE
   L=6629  -DNV_UNIX   -DNV_LINUX   -DNV_INT64_OK   -DNVCPU_X86      -UDEBUG -U
   _DEBUG -DNDEBUG -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -
   DNV_PCI_DISABLE_DEVICE_PRESENT -DNV_CLASS_SIMPLE_CREATE_PRESENT -DNV_PCI_GET
   _CLASS_PRESENT  -DMODULE -DKBUILD_BASENAME=nv -DKBUILD_MODNAME=nvidia -c -o 
   /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/u
   sr/src/nv/.tmp_nv.o /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/n
   v/nv.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:20,
                    from include/linux/module.h:10,
                    from /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src
   /nv/nv-linux.h:52,
                    from /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src
   /nv/nv.c:14:
   include/linux/prefetch.h: In function `prefetch_range':
   include/linux/prefetch.h:62: warning: pointer of type `void *' used in arith
   metic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:864,
                    from /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src
   /nv/nv-linux.h:75,
                    from /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src
   /nv/nv.c:14:
   include/asm/io.h: In function `check_signature':
   include/asm/io.h:253: warning: wrong type argument to increment
   /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/nv.c: In function 
   `nvidia_init_module':
   /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/nv.c:930: warning:
   `pm_register' is deprecated (declared at include/linux/pm.h:106)
   /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/nv.c: In function 
   `nvidia_exit_module':
   /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/nv.c:1051: warning
   : `pm_unregister' is deprecated (declared at include/linux/pm.h:111)
   /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/nv.c: In function 
   `_get_phys_address':
   /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/nv.c:2509: warning
   : passing arg 1 of `pmd_offset' from incompatible pointer type
   /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/nv.c: In function 
   `nv_agp_init':
   /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/nv.c:2991: warning
   : implicit declaration of function `inter_module_get'
   /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/nv.c:2992: warning
   : `inter_module_put' is deprecated (declared at include/linux/module.h:568)
     /usr/bin/gcc-3.4 -Wp,-MD,/tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/us
   r/src/nv/.nv-vm.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/3.4.5/in
   clude -D__KERNEL__ -Iinclude  -Wall -Wstrict-prototypes -Wno-trigraphs -fno-
   strict-aliasing -fno-common -ffreestanding -Os     -fomit-frame-pointer -pip
   e -msoft-float -mpreferred-stack-boundary=2 -fno-unit-at-a-time -march=i386 
   -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement  -I/tmp/selfgz
   1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-typ
   e -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith  -Wno-mu
   ltichar  -Werror -O -fno-common -MD   -Wno-cast-qual -Wno-error -D_LOOSE_KER
   NEL_NAMES -D__KERNEL__ -DMODULE  -DNTRM -D_GNU_SOURCE -D_LOOSE_KERNEL_NAMES 
   -D__KERNEL__ -DMODULE  -DNV_MAJOR_VERSION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHL
   EVEL=6629  -DNV_UNIX   -DNV_LINUX   -DNV_INT64_OK   -DNVCPU_X86      -UDEBUG
   -U_DEBUG -DNDEBUG -DNV_REMAP
   _PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DNV_PCI_DISABLE_DEVICE_PRE
   SENT -DNV_CLASS_SIMPLE_CREATE_PRESENT -DNV_PCI_GET_CLASS_PRESENT  -DMODULE -
   DKBUILD_BASENAME=nv_vm -DKBUILD_MODNAME=nvidia -c -o /tmp/selfgz1302/NVIDIA-
   Linux-x86-1.0-6629-pkg1/usr/src/nv/.tmp_nv-vm.o /tmp/selfgz1302/NVIDIA-Linux
   -x86-1.0-6629-pkg1/usr/src/nv/nv-vm.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:20,
                    from include/linux/module.h:10,
                    from /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src
   /nv/nv-linux.h:52,
                    from /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src
   /nv/nv-vm.c:14:
   include/linux/prefetch.h: In function `prefetch_range':
   include/linux/prefetch.h:62: warning: pointer of type `void *' used in arith
   metic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:864,
                    from /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src
   /nv/nv-linux.h:75,
                    from /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src
   /nv/nv-vm.c:14:
   include/asm/io.h: In function `check_signature':
   include/asm/io.h:253: warning: wrong type argument to increment
   /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/nv-vm.c: At top le
   vel:
   /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/nv-vm.c:59: warnin
   g: 'cache_flush' defined but not used
     /usr/bin/gcc-3.4 -Wp,-MD,/tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/us
   r/src/nv/.os-agp.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/3.4.5/i
   nclude -D__KERNEL__ -Iinclude  -Wall -Wstrict-prototypes -Wno-trigraphs -fno
   -strict-aliasing -fno-common -ffreestanding -Os     -fomit-frame-pointer -pi
   pe -msoft-float -mpreferred-stack-boundary=2 -fno-unit-at-a-time -march=i386
   -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement  -I/tmp/selfgz
   1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-typ
   e -Wswitch -Wfor
   mat -Wchar-subscripts -Wparentheses -Wpointer-arith  -Wno-multichar  -Werror
   -O -fno-common -MD   -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -D__KER
   NEL__ -DMODULE  -DNTRM -D_GNU_SOURCE -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMO
   DULE  -DNV_MAJOR_VERSION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=6629  -DNV_U
   NIX   -DNV_LINUX   -DNV_INT64_OK   -DNVCPU_X86      -UDEBUG -U_DEBUG -DNDEBU
   G -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DNV_PCI_DISABL
   E_DEVICE_PRESENT -DNV_CLASS_SIMPLE_CREATE_PRESENT -DNV_PCI_GET_CLASS_PRESENT
    -DMODULE -DKBUILD_BASENAME=os_agp -DKBUILD_MODNAME=nvidia -c -o /tmp/selfgz
   1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/.tmp_os-agp.o /tmp/selfgz1302
   /NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:20,
                    from include/linux/module.h:10,
                    from /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src
   /nv/nv-linux.h:52,
                    from /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src
   /nv/os-agp.c:24:
   include/linux/prefetch.h: In function `prefetch_range':
   include/linux/prefetch.h:62: warning: pointer of type `void *' used in arith
   metic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:864,
                    from /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src
   /nv/nv-linux.h:75,
                    from /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src
   /nv/os-agp.c:24:
   include/asm/io.h: In function `check_signature':
   include/asm/io.h:253: warning: wrong type argument to increment
   /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c: At top l
   evel:
   /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c:48: error
   : parse error before '*' token
   /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c:48: warni
   ng: type defaults to `int' in declaration of `drm_agp_p'
   /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c:48: warni
   ng: data definition has no type or storage class
   /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c: In funct
   ion `KernInitAGP':
   /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c:76: warni
   ng: assignment discards qualifiers from pointer target type
   /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c:85: error
   : request for member `acquire' in something not a structure or union
   /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c:88: warni
   ng: `inter_module_put' is deprecated (declared at include/linux/module.h:568
   )
   /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c:113: erro
   r: request for member `copy_info' in something not a structure or union
   /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c:173: erro
   r: request for member `enable' in something not a structure or union
   /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c:185: erro
   r: request for member `release' in something not a structure or union
   /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c:186: warn
   ing: `inter_module_put' is deprecated (declared at include/linux/module.h:56
   8)
   /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c: In funct
   ion `KernTeardownAGP':
   /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c:216: erro
   r: request for member `release' in something not a structure or union
   /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c:218: warn
   ing: `inter_module_put' is deprecated (declared at include/linux/module.h:56
   8)
   /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c: In funct
   ion `KernAllocAGPPages':
   /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c:265: erro
   r: request for member `allocate_memory' in something not a structure or unio
   n
   /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c:273: erro
   r: request for member `bind_memory' in something not a structure or union
   /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c:290: erro
   r: request for member `unbind_memory' in something not a structure or union
   /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c:305: erro
   r: request for member `free_memory' in something not a structure or union
   /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c: In funct
   ion `KernMapAGPPages':
   /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c:345: erro
   r: request for member `unbind_memory' in something not a structure or union
   /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c: In funct
   ion `KernFreeAGPPages':
   /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c:444: erro
   r: request for member `unbind_memory' in something not a structure or union
   /tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-agp.c:445: erro
   r: request for member `free_memory' in something not a structure or union
   make[3]: *** [/tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src/nv/os-a
   gp.o] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 1
   make[2]: *** [_module_/tmp/selfgz1302/NVIDIA-Linux-x86-1.0-6629-pkg1/usr/src
   /nv] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 2
   NVIDIA: left KBUILD.
   nvidia.ko failed to build!
   make[1]: *** [module] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 1
   make: *** [module] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 2
-> Error.
ERROR: Unable to build the NVIDIA kernel module.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.

```
Please, tell me what i'm doing wrong?

And please sorry for my english.

---

### Post by Sai on 2005-12-31
Anyone tell me please how to finish installation of drivers and build this kernel module.

---

