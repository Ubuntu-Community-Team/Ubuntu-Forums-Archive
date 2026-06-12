---
title: "Intel GMA 3100 Drivers"
date: 2007-07-06
forum: Multimedia &amp; Video
---

### Post by feeling367 on 2007-07-06
Hello, 

I've a new mobo with Intel G33 Express Chipset.
[http://www.intel.com/products/chipsets/G33/index.htm](http://www.intel.com/products/chipsets/G33/index.htm)

This chipset provide an embeded graphic solution ,  the INTEL GMA 3100.

I'm under kubuntu feisty and I've tried the 2 drivers provided by ubuntu ( intel and i810 ) but no one work with my card. (they are for GMA 9xx cards) 
and the vesa driver works, but ... vesa ... #-o

I've look to other solutions 
[http://intellinuxgraphics.org/install.html](http://intellinuxgraphics.org/install.html)

and i tried to compile them (after installation of all xserver*-dev packages .... #-o )

and I've these answer :

$ echo $PKG_CONFIG_PATH
/usr/lib/pkgconfig
$ echo $ACLOCAL
aclocal -I /usr/share/aclocal
$ echo $DOWN_ROOT
/home/feeling/intelGraphics

```

$ ./autogen.sh --prefix=${XORG_DIR}
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal -I /usr/share/aclocal
autoreconf: configure.ac: tracing
autoreconf: running: libtoolize --copy
libtoolize: `config.guess' exists: use `--force' to overwrite
libtoolize: `config.sub' exists: use `--force' to overwrite
libtoolize: `ltmain.sh' exists: use `--force' to overwrite
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy --no-force
autoreconf: Leaving directory `.'
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking whether gcc and cc understand -c and -o together... yes
checking for intel-gen4asm... no
checking if XINERAMA is defined... yes
checking if RANDR is defined... yes
checking if RENDER is defined... yes
checking if XF86DRI is defined... yes
checking if DPMSExtension is defined... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for XORG... yes
checking for PCIACCESS... no
checking for ANSI C header files... (cached) yes
checking for /usr/include/xorg/dri.h... yes
checking for /usr/include/xorg/sarea.h... yes
checking for /usr/include/xorg/dristruct.h... yes
checking for /usr/include/xorg/damage.h... yes
checking whether to include DRI support... yes
checking for xf86Modes.h... no
configure: error: Must have X server >= 1.3 source tree for mode setting code. Please specify --with-xserver-source

```

I dont find wich package provide the xf86Modes.h header file ....
$ sudo apt-file update
$ sudo apt-file search xf86Modes.h

(nothing .....)
Somebody have an idea ? (even for the 2D driver only ...)

Thanx !
laurent.

---

### Post by feeling367 on 2007-07-06
PS : My Current Xorg.0.log with the config :


```

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "be"
        Option          "XkbVariant"    "be"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "Device"
        Identifier      "Intel GMA3100"
        Driver          "intel"
#       Driver          "vesa"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "LCD_Samsung"
        Option          "DPMS"
        HorizSync       28-49
        VertRefresh     43-72
EndSection

Section "Screen"
        Identifier      "ScreenA"
        Device          "Intel GMA3100"
        Monitor         "LCD_Samsung"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "ScreenA"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection

```


log output :

```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux mediaCenter 2.6.20.3-ubuntu1 #1 SMP Thu Jul 5 20:28:56 CEST 2007 x86_64
Build Date: 04 April 2007
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jul  6 11:19:27 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "ScreenA" (0)
(**) |   |-->Monitor "LCD_Samsung"
(**) |   |-->Device "Intel GMA3100"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
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
        /usr/share/fonts/X11/misc,
        /usr/X11R6/lib/X11/fonts/misc,
        /usr/share/fonts/X11/cyrillic,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/X11R6/lib/X11/fonts/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7a16e0
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.3
        X.Org Video Driver: 1.1
        X.Org XInput driver : 0.7
        X.Org Server Extension : 0.3
        X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,29c0 card 1458,5000 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,29c2 card 1458,d000 rev 02 class 03,00,00 hdr 00
(II) PCI: 00:1a:0: chip 8086,2937 card 1458,5004 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1a:1: chip 8086,2938 card 1458,5004 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1a:2: chip 8086,2939 card 1458,5004 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1a:7: chip 8086,293c card 1458,5006 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1b:0: chip 8086,293e card 1458,a002 rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,2940 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:4: chip 8086,2948 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:5: chip 8086,294a card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2934 card 1458,5004 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2935 card 1458,5004 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,2936 card 1458,5004 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,293a card 1458,5006 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 92 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2916 card 1458,5001 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,2920 card 1458,b002 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,2930 card 1458,5001 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,2926 card 1458,b002 rev 02 class 01,01,85 hdr 00
(II) PCI: 02:00:0: chip 197b,2368 card 1458,b000 rev 00 class 01,01,85 hdr 00
(II) PCI: 03:00:0: chip 10ec,8168 card 1458,e000 rev 01 class 02,00,00 hdr 00
(II) PCI: 04:01:0: chip 109e,036e card 0000,0000 rev 11 class 04,00,00 hdr 80
(II) PCI: 04:01:1: chip 109e,0878 card 0000,0000 rev 11 class 04,80,00 hdr 80
(II) PCI: 04:07:0: chip 104c,8024 card 1458,1000 rev 00 class 0c,00,10 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
        [0] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:28:0), (0,1,1), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 1 I/O range:
        [0] -1  0       0x0000b000 - 0x0000bfff (0x1000) IX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:4), (0,2,2), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 2 I/O range:
        [0] -1  0       0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
        [0] -1  0       0xe0000000 - 0xe0ffffff (0x1000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:5), (0,3,3), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 3 I/O range:
        [0] -1  0       0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
        [0] -1  0       0xe1000000 - 0xe2ffffff (0x2000000) MX[B]
(II) Bus 3 prefetchable memory range:
        [0] -1  0       0x40000000 - 0x400fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:30:0), (0,4,4), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 4 non-prefetchable memory range:
        [0] -1  0       0xe3100000 - 0xe31fffff (0x100000) MX[B]
(II) Bus 4 prefetchable memory range:
        [0] -1  0       0xe3200000 - 0xe32fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:2:0) Intel Corporation Integrated Graphics Controller rev 2, Mem @ 0xe3300000/19, 0xd0000000/28, 0xe3000000/20, I/O @ 0xe200/3
(--) PCI: (4:1:0) Brooktree Corporation Bt878 Video Capture rev 17, Mem @ 0xe3200000/12
(II) Addressable bus resource ranges are
        [0] -1  0       0x00000000 - 0xffffffff (0x100000000) MX[B]
        [1] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
        [0] -1  0       0xe3100000 - 0xe3103fff (0x4000) MX[B]
        [1] -1  0       0xe3104000 - 0xe31047ff (0x800) MX[B]
        [2] -1  0       0xe3201000 - 0xe3201fff (0x1000) MX[B]
        [3] -1  0       0xe2000000 - 0xe2000fff (0x1000) MX[B]
        [4] -1  0       0xe3386000 - 0xe33860ff (0x100) MX[B]
        [5] -1  0       0xe3385000 - 0xe33853ff (0x400) MX[B]
        [6] -1  0       0xe3380000 - 0xe3383fff (0x4000) MX[B]
        [7] -1  0       0xe3384000 - 0xe33843ff (0x400) MX[B]
        [8] -1  0       0xe3200000 - 0xe3200fff (0x1000) MX[B](B)
        [9] -1  0       0xe3000000 - 0xe30fffff (0x100000) MX[B](B)
        [10] -1 0       0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
        [11] -1 0       0xe3300000 - 0xe337ffff (0x80000) MX[B](B)
        [12] -1 0       0x0000d000 - 0x0000d0ff (0x100) IX[B]
        [13] -1 0       0x0000c400 - 0x0000c40f (0x10) IX[B]
        [14] -1 0       0x0000c300 - 0x0000c303 (0x4) IX[B]
        [15] -1 0       0x0000c200 - 0x0000c207 (0x8) IX[B]
        [16] -1 0       0x0000c100 - 0x0000c103 (0x4) IX[B]
        [17] -1 0       0x0000c000 - 0x0000c007 (0x8) IX[B]
        [18] -1 0       0x0000ed00 - 0x0000ed0f (0x10) IX[B]
        [19] -1 0       0x0000ec00 - 0x0000ec0f (0x10) IX[B]
        [20] -1 0       0x0000eb00 - 0x0000eb03 (0x4) IX[B]
        [21] -1 0       0x0000ea00 - 0x0000ea07 (0x8) IX[B]
        [22] -1 0       0x0000e900 - 0x0000e903 (0x4) IX[B]
        [23] -1 0       0x0000e800 - 0x0000e807 (0x8) IX[B]
        [24] -1 0       0x00000500 - 0x0000051f (0x20) IX[B]
        [25] -1 0       0x0000fc00 - 0x0000fc0f (0x10) IX[B]
        [26] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [27] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [28] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [29] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [30] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [31] -1 0       0x0000e600 - 0x0000e61f (0x20) IX[B]
        [32] -1 0       0x0000e500 - 0x0000e51f (0x20) IX[B]
        [33] -1 0       0x0000e400 - 0x0000e41f (0x20) IX[B]
        [34] -1 0       0x0000e100 - 0x0000e11f (0x20) IX[B]
        [35] -1 0       0x0000e000 - 0x0000e01f (0x20) IX[B]
        [36] -1 0       0x0000e300 - 0x0000e31f (0x20) IX[B]
        [37] -1 0       0x0000e200 - 0x0000e207 (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
        [0] -1  0       0xe3100000 - 0xe3103fff (0x4000) MX[B]
        [1] -1  0       0xe3104000 - 0xe31047ff (0x800) MX[B]
        [2] -1  0       0xe3201000 - 0xe3201fff (0x1000) MX[B]
        [3] -1  0       0xe2000000 - 0xe2000fff (0x1000) MX[B]
        [4] -1  0       0xe3386000 - 0xe33860ff (0x100) MX[B]
        [5] -1  0       0xe3385000 - 0xe33853ff (0x400) MX[B]
        [6] -1  0       0xe3380000 - 0xe3383fff (0x4000) MX[B]
        [7] -1  0       0xe3384000 - 0xe33843ff (0x400) MX[B]
        [8] -1  0       0xe3200000 - 0xe3200fff (0x1000) MX[B](B)
        [9] -1  0       0xe3000000 - 0xe30fffff (0x100000) MX[B](B)
        [10] -1 0       0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
        [11] -1 0       0xe3300000 - 0xe337ffff (0x80000) MX[B](B)
        [12] -1 0       0x0000d000 - 0x0000d0ff (0x100) IX[B]
        [13] -1 0       0x0000c400 - 0x0000c40f (0x10) IX[B]
        [14] -1 0       0x0000c300 - 0x0000c303 (0x4) IX[B]
        [15] -1 0       0x0000c200 - 0x0000c207 (0x8) IX[B]
        [16] -1 0       0x0000c100 - 0x0000c103 (0x4) IX[B]
        [17] -1 0       0x0000c000 - 0x0000c007 (0x8) IX[B]
        [18] -1 0       0x0000ed00 - 0x0000ed0f (0x10) IX[B]
        [19] -1 0       0x0000ec00 - 0x0000ec0f (0x10) IX[B]
        [20] -1 0       0x0000eb00 - 0x0000eb03 (0x4) IX[B]
        [21] -1 0       0x0000ea00 - 0x0000ea07 (0x8) IX[B]
        [22] -1 0       0x0000e900 - 0x0000e903 (0x4) IX[B]
        [23] -1 0       0x0000e800 - 0x0000e807 (0x8) IX[B]
        [24] -1 0       0x00000500 - 0x0000051f (0x20) IX[B]
        [25] -1 0       0x0000fc00 - 0x0000fc0f (0x10) IX[B]
        [26] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [27] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [28] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [29] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [30] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [31] -1 0       0x0000e600 - 0x0000e61f (0x20) IX[B]
        [32] -1 0       0x0000e500 - 0x0000e51f (0x20) IX[B]
        [33] -1 0       0x0000e400 - 0x0000e41f (0x20) IX[B]
        [34] -1 0       0x0000e100 - 0x0000e11f (0x20) IX[B]
        [35] -1 0       0x0000e000 - 0x0000e01f (0x20) IX[B]
        [36] -1 0       0x0000e300 - 0x0000e31f (0x20) IX[B]
        [37] -1 0       0x0000e200 - 0x0000e207 (0x8) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xe3100000 - 0xe3103fff (0x4000) MX[B]
        [5] -1  0       0xe3104000 - 0xe31047ff (0x800) MX[B]
        [6] -1  0       0xe3201000 - 0xe3201fff (0x1000) MX[B]
        [7] -1  0       0xe2000000 - 0xe2000fff (0x1000) MX[B]
        [8] -1  0       0xe3386000 - 0xe33860ff (0x100) MX[B]
        [9] -1  0       0xe3385000 - 0xe33853ff (0x400) MX[B]
        [10] -1 0       0xe3380000 - 0xe3383fff (0x4000) MX[B]
        [11] -1 0       0xe3384000 - 0xe33843ff (0x400) MX[B]
        [12] -1 0       0xe3200000 - 0xe3200fff (0x1000) MX[B](B)
        [13] -1 0       0xe3000000 - 0xe30fffff (0x100000) MX[B](B)
        [14] -1 0       0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
        [15] -1 0       0xe3300000 - 0xe337ffff (0x80000) MX[B](B)
        [16] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [17] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [18] -1 0       0x0000d000 - 0x0000d0ff (0x100) IX[B]
        [19] -1 0       0x0000c400 - 0x0000c40f (0x10) IX[B]
        [20] -1 0       0x0000c300 - 0x0000c303 (0x4) IX[B]
        [21] -1 0       0x0000c200 - 0x0000c207 (0x8) IX[B]
        [22] -1 0       0x0000c100 - 0x0000c103 (0x4) IX[B]
        [23] -1 0       0x0000c000 - 0x0000c007 (0x8) IX[B]
        [24] -1 0       0x0000ed00 - 0x0000ed0f (0x10) IX[B]
        [25] -1 0       0x0000ec00 - 0x0000ec0f (0x10) IX[B]
        [26] -1 0       0x0000eb00 - 0x0000eb03 (0x4) IX[B]
        [27] -1 0       0x0000ea00 - 0x0000ea07 (0x8) IX[B]
        [28] -1 0       0x0000e900 - 0x0000e903 (0x4) IX[B]
        [29] -1 0       0x0000e800 - 0x0000e807 (0x8) IX[B]
        [30] -1 0       0x00000500 - 0x0000051f (0x20) IX[B]
        [31] -1 0       0x0000fc00 - 0x0000fc0f (0x10) IX[B]
        [32] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [33] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [34] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [35] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [36] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [37] -1 0       0x0000e600 - 0x0000e61f (0x20) IX[B]
        [38] -1 0       0x0000e500 - 0x0000e51f (0x20) IX[B]
        [39] -1 0       0x0000e400 - 0x0000e41f (0x20) IX[B]
        [40] -1 0       0x0000e100 - 0x0000e11f (0x20) IX[B]
        [41] -1 0       0x0000e000 - 0x0000e01f (0x20) IX[B]
        [42] -1 0       0x0000e300 - 0x0000e31f (0x20) IX[B]
        [43] -1 0       0x0000e200 - 0x0000e207 (0x8) IX[B](B)
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
        compiled for 7.2.0, module version = 2.1.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.1.0
        ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 14.94.94
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.1.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.1.1
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.7
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
        i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
        E7221 (i915), 915GM, 945G, 945GM, 965G, 965G, 965Q, 946GZ, 965GM
(II) Primary Device is: PCI 00:02:0
(EE) No devices detected.

Fatal server error:
no screens found


```

-> driver loaded but device not detected O_o

the lspci entry :

```

00:02.0 VGA compatible controller: Intel Corporation Unknown device 29c2 (rev 02) (prog-if 00 [VGA])
        Subsystem: Giga-byte Technology Unknown device d000
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 10
        Region 0: Memory at e3300000 (32-bit, non-prefetchable) [size=512K]
        Region 1: I/O ports at e200 [size=8]
        Region 2: Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Region 3: Memory at e3000000 (32-bit, non-prefetchable) [size=1M]
        Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
                Address: 00000000  Data: 0000
        Capabilities: [d0] Power Management version 2
                Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-


```

---

### Post by feeling367 on 2007-07-06
After several readings,  .... it seems that latest intel drivers comes with (K)ubuntu gusty (alpha testing rc0) ...

I will test it in a few days.

---

### Post by Voland666 on 2007-07-07
Get the latest X3100 driver released by Intel here (Feisty backport from Gutsy):

[http://ubuntuforums.org/showthread.php?t=494943](http://ubuntuforums.org/showthread.php?t=494943)

Hope this helps

---

### Post by feeling367 on 2007-07-09
ARf :-)

thanx !!

I'm running gusty since 2 days and it works fine with the intel driver ... (even in 3D)

( little bit buggy because SID but it works fine :-) )


regards,
Laurent.

---

### Post by fugitivo on 2007-07-14
Hi, I have a DG33BU motherboard and had the same problems as you. 
I still have one problem with the network card, using kernel 2.6.20 I had to compile lastest intel drivers, but with gutsy (now kernel 2.6.22-8) the network card works, but only icmp packets (that's weird). I have the same result compiling intel drivers.
Also I have to disable ACPI from boot because it freezes the computer.

Did you have this problems?

---

### Post by rmullins on 2007-08-01
> **Voland666 said:**
> Get the latest X3100 driver released by Intel here (Feisty backport from Gutsy):

[http://ubuntuforums.org/showthread.php?t=494943](http://ubuntuforums.org/showthread.php?t=494943)

Hope this helps

I was so reticent about doing this, but it really works! Thanks a ton.  I am working on a 'How to' to solve this problem in a centralized location, because I know how frustrating it is to get your system up and running.

Thanks again, I once again have a beautiful Ubuntu screen!

---

