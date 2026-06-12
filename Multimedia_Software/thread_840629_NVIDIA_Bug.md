---
title: "NVIDIA Bug"
date: 2008-06-25
forum: Multimedia Software
---

### Post by solracsuii on 2008-06-25
Ubuntu Studio 8.04
I tried almost everything to make it work, it seems there's a problem creating the kernel module while installing from root. i downloaded the EnvyNG utility and won't work with any of the 3 versions of drivers...

any help ?:(

**here is the intaller report:**

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Wed Jun 25 14:44:07 2008
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
-> You appear to be running in runlevel 1; this may cause problems.  For exampl
   e: some distributions that use devfs do not run the devfs daemon in runlevel
   1, making it difficult for `nvidia-installer` to correctly setup the kernel 
   module configuration files.  It is recommended that you quit installation no
   w and switch to runlevel 3 (`telinit 3`) before installing.
   
   Quit installation now? (select 'No' to continue installation) (Answer: No)
-> License accepted.
-> Installing NVIDIA driver version 173.14.09.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: No)
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.24-19-rt/build'
-> Kernel output path: '/lib/modules/2.6.24-19-rt/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.24-19-rt/bu
   ild SYSOUT=/lib/modules/2.6.24-19-rt/build'...
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.24-19-rt/build SUBDIRS=/tmp
   /selfgz5724/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz5724/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/.tmp_ver
   sions ; rm -f /tmp/selfgz5724/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/.tm
   p_versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz5724/NVIDIA-Linux-x86-173.14.0
   9-pkg1/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz5724/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/.nv.
   o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D__KERNEL
   __  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prot
   otypes -Wno-trigraphs -fno-stric
   t-aliasing -fno-common -Werror-implicit-function-declaration -O2 -pipe -msof
   t-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2  -march
   =i586 -mtune=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/a
   sm-x86/mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclarat
   ion-after-statement -Wno-pointer-sign   -I/tmp/selfgz5724/NVIDIA-Linux-x86-1
   73.14.09-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -W
   char-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -MD   -
   Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VE
   RSION_STRING=\"173.14.09\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR
   (s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KBUILD_STR(nvi
   dia)" -c -o /tmp/selfgz5724/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/.tmp_
   nv.o /tmp/selfgz5724/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/nv.c
   In file included from include/linux/list.h:8,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:85,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:53,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5724/NVIDIA-Linux-x86-173.14.09-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz5724/NVIDIA-Linux-x86-173.14.09-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/prefetch.h: In function 'prefetch_range':
   include/linux/prefetch.h:57: warning: pointer of type 'void *' used in arith
   metic
   In file included from include/asm/dma-mapping_32.h:5,
                    from include/asm/dma-mapping.h:2,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz5724/NVIDIA-Linux-x86-173.14.09-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz5724/NVIDIA-Linux-x86-173.14.09-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/scatterlist.h: In function 'sg_virt':
   include/linux/scatterlist.h:293: warning: pointer of type 'void *' used in a
   rithmetic
   /tmp/selfgz5724/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/nv.c: In function
   'nv_alloc_file_private':
   /tmp/selfgz5724/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/nv.c:1887: error:
   implicit declaration of function '__SEMAPHORE_INITIALIZER'
   /tmp/selfgz5724/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/nv.c:1887: error:
   invalid initializer
   /tmp/selfgz5724/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/nv.c: In function
   'nv_lock_init_locks':
   /tmp/selfgz5724/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/nv.c:3808: error:
   invalid initializer
   /tmp/selfgz5724/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/nv.c:3809: error:
   invalid initializer
   make[3]: *** [/tmp/selfgz5724/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/nv.
   o] Error 1
   make[2]: *** [_module_/tmp/selfgz5724/NVIDIA-Linux-x86-173.14.09-pkg1/usr/sr
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

---

### Post by GhettoYhetti on 2008-07-13
I can't remember the exact title of the thread but StarCannon posted the following and it worked for me just fine, however I ran into problems with sound.

<<BEGIN STARCANNON>>
Print out this guide, you will be in pure CLI for part of the install.

1)  Download the driver for your Nvidia Card from [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
    1.a) Make sure its in your home directory, this will make it so we don't have to change directories later when were in terminal.

2) Open a terminal: Applications--> Accessories--> Terminal

3) sudo apt-get install build-essential

4) gksudo gedit /etc/modules
    4.a) Add "nvidia" without quotes to the list.
    4.b) Save and Exit

5) gksudo gedit /etc/default/linux-restricted-modules-common
    5.a) Add "nv" without quotes to the restricted list. It should look exactly like this: DISABLED_MODULES="nv"
    5.b) Save and Exit

6) sudo cp /etc/X11/xorg.conf ./xorg.conf.backup

7) sudo rm /etc/X11/xorg.conf
    7.a) Were just deleting your old xorg.conf file, we backed it up in step 6 just in case we ever need it back again.
    7.b) Getting rid of old drivers, use one or more of the sections that apply to you:
        -------------------------------------------------------------------------------------------------------
        If you used Envy to attempt a previous nvidia install please run this command now before you go on:

               sudo envy --uninstall-all 
        sudo dpkg -P envy 

        -------------------------------------------------------------------------------------------------------
        If you have some old Ubuntu repository/restricted driver manager attempts installed please run this command before you go on:

        sudo apt-get remove --purge nvidia*
                sudo rm /lib/restricted-modules/.nvidia*

        -------------------------------------------------------------------------------------------------------
        If you have a failed NVIDIA*.run (drivers from the nvidia.com site) run this command before you go on:

        sudo nvidia-installer --uninstall

        -------------------------------------------------------------------------------------------------------
####################################################################################
##................................................................................##
## Alright Now Assuming That You are starting with a clean slate lets move forward##
##................................................................................##
####################################################################################

8) CTRL-ALT-F1
    8.a) Okay were in Command Line only now, we have a little left to do in here.
    8.b)login:
    8.c)Password:

9) sudo /etc/init.d/gdm stop
    9.a) This step shuts down the x-server and gnome desktop manager

10) sudo chmod a+x ./NVIDIA*.run
    10.a) We made the nvidia installer executable.

11) sudo ./NVIDIA*.run
    11.a) Answer to the affirmative for all questions.
    11.b) Be sure to specifically say you DO WANT it to write a new xorg.conf
    11.c) If you somehow answered incorrectly on the last question in the installer then:
        c.I) sudo nvidia-xconfig #this will write a new or attempt repair of an xorg.conf file for you.

12) sudo /etc/init.d/gdm start
    12.a) You should see an Nvidia Logo, and then be put at your login screen, you should also be able to enable desktop effects.

<<END STARCANNON>>

Hopefully this works for you.

---

