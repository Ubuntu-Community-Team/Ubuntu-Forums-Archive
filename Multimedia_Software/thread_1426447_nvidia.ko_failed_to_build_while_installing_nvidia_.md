---
title: "nvidia.ko failed to build while installing nvidia driver for AGP 6200 card"
date: 2010-03-10
forum: Multimedia Software
---

### Post by kartik_vad on 2010-03-10
I'm trying to install the nvidia drivers for my AGP 6200 nvidia card from [http://www.nvidia.com/object/linux_display_ia32_1.0-7664.html](http://www.nvidia.com/object/linux_display_ia32_1.0-7664.html) . I checked that this driver does support the 6200, but I get the following error:

nvidia.ko failed to build!

The complete log file is below. Some details about my system:

The hardware is an AMD Athlon 64 3000+ on an Asus A8V-MX with a VIA K8M800 chipset running Ubuntu Karmic. Here's the output of uname -a:
Linux enlightenment 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010 i686 GNU/Linux

I updated my system before running the nvidia installer and, according to instructions, I shut down X with "/etc/init.d/gdm stop", and then ran the installer using sh.

**I looked for other threads on this forum, but the error messages seem to be slightly different, so I'm not sure if it's the same issue.**

I checked that I have make and cc, and I do.

Here's the complete log; can someone help me out, please? Thanks.

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Wed Mar 10 19:30:03 2010

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
  OpenGL header files     : true
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
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Kernel source path: '/lib/modules/2.6.31-20-generic/build'
-> Performing CC test with CC="cc".
-> Performing rivafb check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
   rm -f -f nv.o nv-vm.o os-agp.o os-interface.o os-registry.o nv.o nv-vm.o os-
   agp.o os-interface.o os-registry.o nvidia.mod.o
   rm -f -f build-in.o nv-linux.o *.d .*.{cmd,flags}
   rm -f -f nvidia.{o,ko,mod.{o,c}} nv_compiler.h *~
   rm -f -rf .tmp_versions
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.31-20-gener
   ic/build SYSOUT=/lib/modules/2.6.31-20-generic/build'...
  
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.31-20-generic/build SUBDIRS
   =/tmp/selfgz1993/NVIDIA-Linux-x86-1.0-7664-pkg1/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (        \
       echo;                                \
       echo "  ERROR: Kernel configuration is invalid.";        \
       echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";    \
       echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";    \
       echo;                                \
       /bin/false)
   mkdir -p /tmp/selfgz1993/NVIDIA-Linux-x86-1.0-7664-pkg1/usr/src/nv/.tmp_vers
   ions ; rm -f /tmp/selfgz1993/NVIDIA-Linux-x86-1.0-7664-pkg1/usr/src/nv/.tmp_
   versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz1993/NVIDIA-Linux-x86-1.0-7664
   -pkg1/usr/src/nv
   (cat /dev/null; ) > /tmp/selfgz1993/NVIDIA-Linux-x86-1.0-7664-pkg1/usr/src/n
   v/modules.order
   make -f /usr/src/linux-headers-2.6.31-20-generic/scripts/Makefile.modpost
     scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.31-20-generic/Modu
   le.symvers -I /tmp/selfgz1993/NVIDIA-Linux-x86-1.0-7664-pkg1/usr/src/nv/Modu
   le.symvers  -o /tmp/selfgz1993/NVIDIA-Linux-x86-1.0-7664-pkg1/usr/src/nv/Mod
   ule.symvers -S -K /usr/src/linux-headers-2.6.31-20-generic/Module.markers -M
   /tmp/selfgz1993/NVIDIA-Linux-x86-1.0-7664-pkg1/usr/src/nv/Module.markers -w
   -s
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

### Post by kartik_vad on 2010-03-10
I checked the README mentioned in the log file, but it doesn't mention this particular problem. Thanks.

---

### Post by kartik_vad on 2010-03-10
The brand of the graphics card is "Zebronics", and the included CD has only Windows drivers. Thanks.

---

