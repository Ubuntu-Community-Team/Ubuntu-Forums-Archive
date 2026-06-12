---
title: "Manually installed Nvidia driver fails to load when adding higher resolutions"
date: 2010-08-28
forum: Multimedia Software
---

### Post by WarGaleon on 2010-08-28
I'm having problems with the Nvidia driver (71.86.14) that I manually installed for my Nvidia Riva TNT2 Model 64 video card. It woks if the screen size is 800x600. The 1024x768 res. is now not in System > Preferences > Monitors. To fix it, I added this modeline to /etc/X11/xorg.conf that I got using "cvt 1024 768" (I created an xorg.conf because it doesn't exists):

```
ModeLine     "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
```And now it fails with the following error in Xorg.0.log:

```
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux galeon-desktop 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:12:52 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=16455729-9855-4e63-9356-ffb0d90aeab2 ro quiet splash
Build Date: 21 July 2010  12:47:34PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Aug 29 07:58:28 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "X.org Configured"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Card0"
(**) |-->Input Device "Mouse0"
(**) |-->Input Device "Keyboard0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(**) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins,
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(**) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Mouse0
(WW) Disabling Keyboard0
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(--) using VT number 7

(--) PCI:*(0:1:0:0) 10de:002d:0000:0000 nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] rev 21, Mem @ 0xe0000000/16777216, 0xe2000000/33554432, BIOS @ 0x????????/65536
(II) Open ACPI successful (/var/run/acpid.socket)
(WW) "dri" will not be loaded unless you've specified it to be loaded elsewhere.
(WW) "dri2" will not be loaded unless you've specified it to be loaded elsewhere.
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri" will be loaded even though the default is to disable it.
(II) "dri2" will be loaded even though the default is to disable it.
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: XFree86 Server Extension
    ABI class: XFree86 Server Extension, version 0.1
(II) NVIDIA GLX Module  71.86.14  Mon Jul 12 21:19:44 PDT 2010
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
[B](II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
dlopen: /usr/lib/xorg/modules/drivers/nvidia_drv.so: undefined symbol: AllocateScreenPrivateIndex
(EE) Failed to load /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) UnloadModule: "nvidia"
(EE) Failed to load module "nvidia" (loader failed, 7)
(EE) No drivers available.
[/B]
Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

```Here is my xorg.conf file:
```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
#    Load  "dri"
#    Load  "dri2"
    Disable  "dri"
    Disable  "dri2"
    Load  "extmod"
    Load  "dbe"
    Load  "glx"
    Load  "record"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
    **ModeLine     "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync**
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "HWcursor"               # [<bool>]
        #Option     "NoAccel"                # [<bool>]
        #Option     "ShadowFB"               # [<bool>]
        #Option     "VideoKey"               # <i>
        #Option     "EXAPixmaps"             # [<bool>]
    Identifier  "Card0"
    Driver      "nvidia"
    VendorName  "nVidia Corporation"
    BoardName   "NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```I tried changing this part:
```
#    Load  "dri"
#    Load  "dri2"
    Disable  "dri"
    Disable  "dri2"
```to different things like
```
#    Load  "dri"
    Disable  "dri"
    Load "dri2"
```and no changes have happened.

I also tried using "Virtual 1024 768" in Display subsections instead of the modeline, but the display is garbage.

I have installed the driver following the instructions in [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual). The differences are that I installed the Linux kernel source using "sudo apt-get install linux-source" because "sudo apt-get install linux-source" returns "E: Couldn't find package linux-source-2.6.32-24-generic", and that I uninstalled nouveau as said in [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia). Also, a message showed up while installing the driver: "The distribution-provided pre-install script failed! Continue installation anyway?" and then I selected yes.

I also reinstalled it afterwards but it still haven't fixed the problem.

Here is the nvidia-installer log file:
```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sun Aug 29 07:04:34 2010
installer version: 1.0.7

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : false
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
-> Installing NVIDIA driver version 71.86.14.
-> There appears to already be a driver installed on your system (version: 71.8
   6.14).  As part of installing this driver (version: 71.86.14), the existing 
   driver will be uninstalled.  Are you sure you want to continue? ('no' will a
   bort installation) (Answer: Yes)
-> Running distribution scripts
   executing: '/usr/lib/nvidia/pre-install'...
-> done.
-> The distribution-provided pre-install script failed!  Continue installation 
   anyway? (Answer: Yes)
-> Not probing for precompiled kernel interfaces.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.32-24-generic/build'
-> Kernel output path: '/lib/modules/2.6.32-24-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.32-24-gener
   ic/build SYSOUT=/lib/modules/2.6.32-24-generic/build'...
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.32-24-generic/build SUBDIRS
   =/tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (        \
       echo;                                \
       echo "  ERROR: Kernel configuration is invalid.";        \
       echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";    \
       echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";    \
       echo;                                \
       /bin/false)
   mkdir -p /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src/nv/.tmp_vers
   ions ; rm -f /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src/nv/.tmp_
   versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14
   -pkg1/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src/nv/.nv.o
   .d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iinclude 
   -I/usr/src/linux-headers-2.6.32-24-generic/arch/x86/include -include include
   /linux/autoconf.h -Iubuntu/inc
   lude  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-str
   ict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-s
   ecurity -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -f
   reg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -m
   accumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protect
   or -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare 
   -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wfra
   me-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg 
   -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dw
   arf2-cfi-asm -fconserve-stack -I/tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pk
   g1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscr
   ipts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -MD -Wsign-compare
   -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE -DNTRM
   -D_GNU_SOURCE -D_LOOSE_KERNEL_NAME
   S -D__KERNEL__ -DMODULE -DNV_VERSION_STRING=\"71.86.14\" -DNV_UNIX -DNV_LINU
   X -DNV_INT64_OK -DNVCPU_X86 -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_ST
   R(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KBUILD_STR(nv
   idia)"  -c -o /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src/nv/.tmp
   _nv.o /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src/nv/nv.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-linux.h:25,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv.c:13:
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:56,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-linux.h:25,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv.c:13:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:56,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-linux.h:25,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv.c:13:
   include/linux/list.h: In function ‘list_del’:
   include/linux/list.h:106: warning: pointer of type ‘void *’ used in arit
   hmetic
   include/linux/list.h:107: warning: pointer of type ‘void *’ used in arit
   hmetic
   include/linux/list.h: In function ‘hlist_del’:
   include/linux/list.h:579: warning: pointer of type ‘void *’ used in arit
   hmetic
   include/linux/list.h:580: warning: pointer of type ‘void *’ used in arit
   hmetic
   In file included from include/linux/sched.h:82,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-linux.h:25,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv.c:13:
   include/linux/rculist.h: In function ‘list_del_rcu’:
   include/linux/rculist.h:97: warning: pointer of type ‘void *’ used in ar
   ithmetic
   include/linux/rculist.h: In function ‘list_replace_rcu’:
   include/linux/rculist.h:143: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/rculist.h: In function ‘hlist_del_rcu’:
   include/linux/rculist.h:286: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/rculist.h: In function ‘hlist_replace_rcu’:
   include/linux/rculist.h:306: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-linux.h:25,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv.c:13:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2281: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-linux.h:86,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv.c:13:
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/io.h: In funct
   ion ‘writeq’:
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-24-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1131,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-linux.h:86,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv.c:13:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.32-24-generic/arch/x86/incl
   ude/asm/dma-mapping.h:42,
                    from include/linux/dma-mapping.h:103,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-24-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1131,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-linux.h:86,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv.c:13:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-linux.h:117,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv.c:13:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
     set -e ; perl /usr/src/linux-headers-2.6.32-24-generic/scripts/recordmcoun
   t.pl "i386" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz30
   04/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src/nv/nv.o";
     cc -Wp,-MD,/tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src/nv/.nv-v
   m.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iinclu
   de  -I/usr/src/linux-headers-2.6.32-24-generic/arch/x86/include -include inc
   lude/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-
   prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-
   function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O
   2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-bounda
   ry=2 -march=i586 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generi
   c32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNA
   L_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -
   mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointe
   r -fno-optimize-sibling-calls -pg 
   -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dw
   arf2-cfi-asm -fconserve-stack -I/tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pk
   g1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscr
   ipts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -MD -Wsign-compare
   -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE -DNTRM
   -D_GNU_SOURCE -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE -DNV_VERSION_STRIN
   G=\"71.86.14\" -DNV_UNIX -DNV_LINUX -DNV_INT64_OK -DNVCPU_X86 -UDEBUG -U_DEB
   UG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_
   vm)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz3004/NVIDIA-Li
   nux-x86-71.86.14-pkg1/usr/src/nv/.tmp_nv-vm.o /tmp/selfgz3004/NVIDIA-Linux-x
   86-71.86.14-pkg1/usr/src/nv/nv-vm.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-linux.h:25,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-vm.c:14:
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:56,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-linux.h:25,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-vm.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:56,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-linux.h:25,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-vm.c:14:
   include/linux/list.h: In function ‘list_del’:
   include/linux/list.h:106: warning: pointer of type ‘void *’ used in arit
   hmetic
   include/linux/list.h:107: warning: pointer of type ‘void *’ used in arit
   hmetic
   include/linux/list.h: In function ‘hlist_del’:
   include/linux/list.h:579: warning: pointer of type ‘void *’ used in arit
   hmetic
   include/linux/list.h:580: warning: pointer of type ‘void *’ used in arit
   hmetic
   In file included from include/linux/sched.h:82,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-linux.h:25,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-vm.c:14:
   include/linux/rculist.h: In function ‘list_del_rcu’:
   include/linux/rculist.h:97: warning: pointer of type ‘void *’ used in ar
   ithmetic
   include/linux/rculist.h: In function ‘list_replace_rcu’:
   include/linux/rculist.h:143: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/rculist.h: In function ‘hlist_del_rcu’:
   include/linux/rculist.h:286: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/rculist.h: In function ‘hlist_replace_rcu’:
   include/linux/rculist.h:306: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-linux.h:25,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-vm.c:14:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2281: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-linux.h:86,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-vm.c:14:
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/io.h: In funct
   ion ‘writeq’:
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-24-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1131,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-linux.h:86,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-vm.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.32-24-generic/arch/x86/incl
   ude/asm/dma-mapping.h:42,
                    from include/linux/dma-mapping.h:103,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-24-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1131,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-linux.h:86,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-vm.c:14:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-linux.h:117,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-vm.c:14:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
     set -e ; perl /usr/src/linux-headers-2.6.32-24-generic/scripts/recordmcoun
   t.pl "i386" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz30
   04/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src/nv/nv-vm.o";
     cc -Wp,-MD,/tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src/nv/.os-a
   gp.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iincl
   ude  -I/usr/src/linux-headers-2.6.32-24-generic/arch/x86/include -include in
   clude/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict
   -prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit
   -function-declaration -Wno-format-s
   ecurity -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -f
   reg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -m
   accumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protect
   or -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare 
   -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wfra
   me-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg 
   -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dw
   arf2-cfi-asm -fconserve-stack -I/tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pk
   g1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscr
   ipts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -MD -Wsign-compare
   -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE -DNTRM
   -D_GNU_SOURCE -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE -DNV_VERSION_STRIN
   G=\"71.86.14\" -DNV_UNIX -DNV_LINUX -DNV_INT64_OK -DNVCPU_X86 -UDEBUG -U_DEB
   UG -DNDEBUG  -DMODULE -D"KBUILD_ST
   R(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_agp)"  -D"KBUILD_MODNAME=KBUILD_ST
   R(nvidia)"  -c -o /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src/nv/
   .tmp_os-agp.o /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src/nv/os-a
   gp.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-linux.h:25,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/os-agp.c:24:
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:56,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-linux.h:25,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/os-agp.c:24:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:56,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-linux.h:25,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/os-agp.c:24:
   include/linux/list.h: In function ‘list_del’:
   include/linux/list.h:106: warning: pointer of type ‘void *’ used in arit
   hmetic
   include/linux/list.h:107: warning: pointer of type ‘void *’ used in arit
   hmetic
   include/linux/list.h: In function ‘hlist_del’:
   include/linux/list.h:579: warning: pointer of type ‘void *’ used in arit
   hmetic
   include/linux/list.h:580: warning: pointer of type ‘void *’ used in arit
   hmetic
   In file included from include/linux/sched.h:82,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-linux.h:25,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/os-agp.c:24:
   include/linux/rculist.h: In function ‘list_del_rcu’:
   include/linux/rculist.h:97: warning: pointer of type ‘void *’ used in ar
   ithmetic
   include/linux/rculist.h: In function ‘list_replace_rcu’:
   include/linux/rculist.h:143: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/rculist.h: In function ‘hlist_del_rcu’:
   include/linux/rculist.h:286: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/rculist.h: In function ‘hlist_replace_rcu’:
   include/linux/rculist.h:306: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-linux.h:25,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/os-agp.c:24:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2281: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-linux.h:86,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/os-agp.c:24:
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/io.h: In funct
   ion ‘writeq’:
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-24-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1131,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-linux.h:86,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/os-agp.c:24:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.32-24-generic/arch/x86/incl
   ude/asm/dma-mapping.h:42,
                    from include/linux/dma-mapping.h:103,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-24-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1131,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-linux.h:86,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/os-agp.c:24:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-linux.h:117,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/os-agp.c:24:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
     set -e ; perl /usr/src/linux-headers-2.6.32-24-generic/scripts/recordmcoun
   t.pl "i386" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz30
   04/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src/nv/os-agp.o";
     cc -Wp,-MD,/tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src/nv/.os-i
   nterface.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  
   -Iinclude  -I/usr/src/linux-headers-2.6.32-24-generic/arch/x86/include -incl
   ude include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -W
   strict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-im
   plicit-function-declaration -Wno-format-security -fno-delete-null-pointer-ch
   ecks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack
   -boundary=2 -march=i586 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune
   =generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CF
   I_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mn
   o-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame
   -pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-
   pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fco
   nserve-stack -I/tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src/nv -Wa
   ll -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparenthese
   s -Wpointer-arith -Wno-multichar -Werror -MD -Wsign-compare -Wno-cast-qual -
   Wno-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE -DNTRM -D_GNU_SOURCE -
   D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE -DNV_VERSION_STRING=\"71.86.14\" 
   -DNV_UNIX -DNV_LINUX -DNV_INT64_OK -DNVCPU_X86 -UDEBUG -U_DEBUG -DNDEBUG  -D
   MODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_interface)"  -D
   "KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz3004/NVIDIA-Linux-x86-
   71.86.14-pkg1/usr/src/nv/.tmp_os-interface.o /tmp/selfgz3004/NVIDIA-Linux-x8
   6-71.86.14-pkg1/usr/src/nv/os-interface.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-linux.h:25,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/os-interface.c:26:
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:56,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-linux.h:25,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/os-interface.c:26:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:56,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-linux.h:25,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/os-interface.c:26:
   include/linux/list.h: In function ‘list_del’:
   include/linux/list.h:106: warning: pointer of type ‘void *’ used in arit
   hmetic
   include/linux/list.h:107: warning: pointer of type ‘void *’ used in arit
   hmetic
   include/linux/list.h: In function ‘hlist_del’:
   include/linux/list.h:579: warning: pointer of type ‘void *’ used in arit
   hmetic
   include/linux/list.h:580: warning: pointer of type ‘void *’ used in arit
   hmetic
   In file included from include/linux/sched.h:82,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-linux.h:25,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/os-interface.c:26:
   include/linux/rculist.h: In function ‘list_del_rcu’:
   include/linux/rculist.h:97: warning: pointer of type ‘void *’ used in ar
   ithmetic
   include/linux/rculist.h: In function ‘list_replace_rcu’:
   include/linux/rculist.h:143: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/rculist.h: In function ‘hlist_del_rcu’:
   include/linux/rculist.h:286: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/rculist.h: In function ‘hlist_replace_rcu’:
   include/linux/rculist.h:306: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-linux.h:25,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/os-interface.c:26:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2281: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-linux.h:86,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/os-interface.c:26:
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/io.h: In funct
   ion ‘writeq’:
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-24-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1131,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-linux.h:86,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/os-interface.c:26:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.32-24-generic/arch/x86/incl
   ude/asm/dma-mapping.h:42,
                    from include/linux/dma-mapping.h:103,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-24-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1131,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-linux.h:86,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/os-interface.c:26:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-linux.h:117,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/os-interface.c:26:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
     set -e ; perl /usr/src/linux-headers-2.6.32-24-generic/scripts/recordmcoun
   t.pl "i386" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz30
   04/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src/nv/os-interface.o";
     cc -Wp,-MD,/tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src/nv/.os-r
   egistry.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -
   Iinclude  -I/usr/src/linux-headers-2.6.32-24-generic/arch/x86/include -inclu
   de include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Ws
   trict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-imp
   licit-function-declaration -Wno-forma
   t-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3
   -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic 
   -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-prote
   ctor -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compar
   e -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wf
   rame-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -p
   g -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-
   dwarf2-cfi-asm -fconserve-stack -I/tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-
   pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subs
   cripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -MD -Wsign-compa
   re -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE -DN
   TRM -D_GNU_SOURCE -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE -DNV_VERSION_S
   TRING=\"71.86.14\" -DNV_UNIX -DNV_LINUX -DNV_INT64_OK -DNVCPU_X86 -UDEBUG -U
   _DEBUG -DNDEBUG  -DMODULE -D"KBUILD
   _STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_registry)"  -D"KBUILD_MODNAME=K
   BUILD_STR(nvidia)"  -c -o /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr
   /src/nv/.tmp_os-registry.o /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/us
   r/src/nv/os-registry.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-linux.h:25,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/os-registry.c:14:
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:56,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-linux.h:25,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/os-registry.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:56,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-linux.h:25,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/os-registry.c:14:
   include/linux/list.h: In function ‘list_del’:
   include/linux/list.h:106: warning: pointer of type ‘void *’ used in arit
   hmetic
   include/linux/list.h:107: warning: pointer of type ‘void *’ used in arit
   hmetic
   include/linux/list.h: In function ‘hlist_del’:
   include/linux/list.h:579: warning: pointer of type ‘void *’ used in arit
   hmetic
   include/linux/list.h:580: warning: pointer of type ‘void *’ used in arit
   hmetic
   In file included from include/linux/sched.h:82,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-linux.h:25,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/os-registry.c:14:
   include/linux/rculist.h: In function ‘list_del_rcu’:
   include/linux/rculist.h:97: warning: pointer of type ‘void *’ used in ar
   ithmetic
   include/linux/rculist.h: In function ‘list_replace_rcu’:
   include/linux/rculist.h:143: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/rculist.h: In function ‘hlist_del_rcu’:
   include/linux/rculist.h:286: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/rculist.h: In function ‘hlist_replace_rcu’:
   include/linux/rculist.h:306: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-linux.h:25,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/os-registry.c:14:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2281: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-linux.h:86,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/os-registry.c:14:
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/io.h: In funct
   ion ‘writeq’:
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-24-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1131,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-linux.h:86,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/os-registry.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.32-24-generic/arch/x86/incl
   ude/asm/dma-mapping.h:42,
                    from include/linux/dma-mapping.h:103,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-24-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1131,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-linux.h:86,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/os-registry.c:14:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nv-linux.h:117,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/os-registry.c:14:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
     set -e ; perl /usr/src/linux-headers-2.6.32-24-generic/scripts/recordmcoun
   t.pl "i386" "32" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz30
   04/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src/nv/os-registry.o";
     ld -m elf_i386   -r -o /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/
   src/nv/nvidia.o /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src/nv/nv
   -kernel.o /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src/nv/nv.o /tm
   p/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src/nv/nv-vm.o /tmp/selfgz30
   04/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src/nv/os-agp.o /tmp/selfgz3004/NVIDIA
   -Linux-x86-71.86.14-pkg1/usr/src/nv/os-interface.o /tmp/selfgz3004/NVIDIA-Li
   nux-x86-71.86.14-pkg1/usr/src/nv/os-registry.o 
   (cat /dev/null;   echo kernel//tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1
   /usr/src/nv/nvidia.ko;) > /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr
   /src/nv/modules.order
   make -f /usr/src/linux-headers-2.6.32-24-generic/scripts/Makefile.modpost
     scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.32-24-generic/Modu
   le.symvers -I /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src/nv/Modu
   le.symvers  -o /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src/nv/Mod
   ule.symvers -S -w  -s
   WARNING: could not find /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/s
   rc/nv/.nv-kernel.o.cmd for /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/us
   r/src/nv/nv-kernel.o
     cc -Wp,-MD,/tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src/nv/.nvid
   ia.mod.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -I
   include  -I/usr/src/linux-headers-2.6.32-24-generic/arch/x86/include -includ
   e include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wst
   rict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-impl
   icit-function-declaration -Wno-format-security -fno-delete-null-pointer-chec
   ks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-b
   oundary=2 -march=i586 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=g
   eneric32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_
   SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tab
   les -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omi
   t-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statemen
   t -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stac
   k -I/tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src/nv -Wall -Wimplic
   it -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer
   -arith -Wno-multichar -Werror -MD -Wsign-compare -Wno-cast-qual -Wno-error -
   D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE -DNTRM -D_GNU_SOURCE -D_LOOSE_KER
   NEL_NAMES -D__KERNEL__ -DMODULE -DNV_VERSION_STRING=\"71.86.14\" -DNV_UNIX -
   DNV_LINUX -DNV_INT64_OK -DNVCPU_X86 -UDEBUG -U_DEBUG -DNDEBUG  -D"KBUILD_STR
   (s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nvidia.mod)"  -D"KBUILD_MODNAME=KBUILD
   _STR(nvidia)"  -DMODULE -c -o /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1
   /usr/src/nv/nvidia.mod.o /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/
   src/nv/nvidia.mod.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from /usr/src/linux-headers-2.6.32-24-generic/arch/x86/incl
   ude/asm/percpu.h:45,
                    from /usr/src/linux-headers-2.6.32-24-generic/arch/x86/incl
   ude/asm/current.h:5,
                    from /usr/src/linux-headers-2.6.32-24-generic/arch/x86/incl
   ude/asm/processor.h:15,
                    from include/linux/prefetch.h:14,
                    from include/linux/list.h:6,
                    from include/linux/module.h:9,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nvidia.mod.c:1:
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/module.h:9,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nvidia.mod.c:1:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/module.h:9,
                    from /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src
   /nv/nvidia.mod.c:1:
   include/linux/list.h: In function ‘list_del’:
   include/linux/list.h:106: warning: pointer of type ‘void *’ used in arit
   hmetic
   include/linux/list.h:107: warning: pointer of type ‘void *’ used in arit
   hmetic
   include/linux/list.h: In function ‘hlist_del’:
   include/linux/list.h:579: warning: pointer of type ‘void *’ used in arit
   hmetic
   include/linux/list.h:580: warning: pointer of type ‘void *’ used in arit
   hmetic
     ld -r -m elf_i386 -T /usr/src/linux-headers-2.6.32-24-generic/scripts/modu
   le-common.lds --build-id -o /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/u
   sr/src/nv/nvidia.ko /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src/n
   v/nvidia.o /tmp/selfgz3004/NVIDIA-Linux-x86-71.86.14-pkg1/usr/src/nv/nvidia.
   mod.o
   NVIDIA: left KBUILD.
-> done.
-> Kernel module compilation complete.
-> Kernel messages:
   [  122.050579] type=1505 audit(1283033478.145:9):  operation="profile_load"
   pid=608 name="/usr/bin/evince"
   [  122.084250] nvidia: module license 'NVIDIA' taints kernel.
   [  122.084265] Disabling lock debugging due to kernel taint
   [  122.620501] type=1505 audit(1283033478.716:10):  operation="profile_load"
   pid=608 name="/usr/bin/evince-previewer"
   [  122.636334] type=1505 audit(1283033478.732:11):  operation="profile_load"
   pid=608 name="/usr/bin/evince-thumbnailer"
   [  122.758939] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
   [  122.758953] PCI: setting IRQ 11 as level-triggered
   [  122.758968] nvidia 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11
   (level, low) -> IRQ 11
   [  122.758997] vgaarb: device changed decodes:
   PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
   [  122.788910] NVRM: loading NVIDIA Linux x86 Kernel Module  71.86.14  Mon
   Jul 12 21:10:38 PDT 2010
   [  124.664844] Yamaha DS-1 PCI 0000:00:0d.0: PCI INT A -> Link[LNKD] -> GSI
   5 (level, low) -> IRQ 5
   [  124.668913] Yamaha DS-1 PCI 0000:00:0d.0: firmware: requesting
   yamaha/ds1_dsp.fw
   [  124.804258] Yamaha DS-1 PCI 0000:00:0d.0: firmware: requesting
   yamaha/ds1e_ctrl.fw
   [  124.871711] vboxdrv: Trying to deactivate the NMI watchdog permanently...
   [  124.871728] vboxdrv: Successfully done.
   [  124.871736] vboxdrv: Found 1 processor cores.
   [  124.883626] vboxdrv: TSC mode is 'synchronous', kernel timer mode is
   'normal'.
   [  124.883642] vboxdrv: Successfully loaded version 3.1.6_OSE (interface
   0x00100001).
   [  132.408038] eth0: no IPv6 routers present
   [  155.997578] [drm] Initialized drm 1.1.0 20060810
   [  190.049924] UDF-fs: Partition marked readonly; forcing readonly mount
   [  190.081039] UDF-fs INFO UDF: Mounting volume 'GTA_SAN_ANDREAS', timestamp
   2005/06/08 00:05 (11e0)
   [ 2323.664282] eth0: link down
   [ 3390.778583] vgaarb: device changed decodes:
   PCI:0000:01:00.0,olddecodes=none,decodes=none:owns=io+mem
   [ 3390.783006] NVRM: loading NVIDIA Linux x86 Kernel Module  71.86.14  Mon
   Jul 12 21:10:38 PDT 2010
-> Installing both new and classic TLS OpenGL libraries.
-> Parsing log file:
-> done.
-> Validating previous installation:
-> Unable to access previously installed file '/usr/include/GL/gl.h' (No such
   file or directory).
-> Unable to access previously installed file '/usr/include/GL/glext.h' (No
   such file or directory).
-> Unable to access previously installed file '/usr/include/GL/glx.h' (No such
   file or directory).
-> The previously installed symlink '/usr/lib/libGL.so' has target
   '/usr/lib/libGL.so.71.86.14', but it was installed with target 'libGL.so.1'.
   /usr/lib/libGL.so will not be uninstalled.
-> done.
WARNING: Your driver installation has been altered since it was initially
         installed; this may happen, for example, if you have since installed
         the NVIDIA driver through a mechanism other than nvidia-installer
         (such as your distribution's native package management system). 
         nvidia-installer will attempt to uninstall as best it can.  Please see
         the file '/var/log/nvidia-installer.log' for details.
-> Uninstalling NVIDIA Accelerated Graphics Driver for Linux-x86 (1.0-718614
   (71.86.14)):
ERROR: Unable to create '/usr/include/GL/gl.h' for copying (No such file or
       directory)
WARNING: Unable to restore file '/usr/include/GL/gl.h'.
ERROR: Unable to create '/usr/include/GL/glext.h' for copying (No such file or
       directory)
WARNING: Unable to restore file '/usr/include/GL/glext.h'.
ERROR: Unable to create '/usr/include/GL/glx.h' for copying (No such file or
       directory)
WARNING: Unable to restore file '/usr/include/GL/glx.h'.
-> done.
-> Uninstallation of existing driver: NVIDIA Accelerated Graphics Driver for
   Linux-x86 (71.86.14) is complete.
-> Searching for conflicting X files:
-> done.
-> Searching for conflicting OpenGL files:
-> done.
-> Installing 'NVIDIA Accelerated Graphics Driver for Linux-x86' (71.86.14):
   executing: '/sbin/ldconfig'...
   executing: '/sbin/depmod -aq'...
-> done.
-> Driver file installation is complete.
-> Running post-install sanity check:
-> done.
-> Post-install sanity check passed.
-> Shared memory test passed.
-> Running runtime sanity check:
-> done.
-> Runtime sanity check passed.
-> Installation of the NVIDIA Accelerated Graphics Driver for Linux-x86
   (version: 71.86.14) is now complete.  Please update your XF86Config or
   xorg.conf file as appropriate; see the file
   /usr/share/doc/NVIDIA_GLX-1.0/README for details.

```System specs:
Ubuntu Linux 10.04.1 LTS
Linux 2.6.32-24-generic
Pentium III: 650mhz
768mb RAM
Nvidia Riva TNT2 Model 64 (32MB) video card

---

### Post by WarGaleon on 2010-08-29
I found out that 71.x.x nVidia drivers do not support x.org > 1.4. I think there should be a note in Community Ubuntu Documentation especially in these pages:
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
so others won't have to spend a lot of time fixing this without knowing that it is currently almost impossible

Also a note for uninstalling nouveau first in [NvidiaManual]("https://help.ubuntu.com/community/NvidiaManual") because some may not read [BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") first, they might already know that there is no 71.x.x drivers in Synaptic and try installing the driver from nVidia.

---

