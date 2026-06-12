---
title: "Coin 3D library dependency problems on installing Ulysses v0.9.3"
date: 2008-10-18
forum: Multimedia Software
---

### Post by orphefs on 2008-10-18
Hi all,

I want to install Ulysses v0.9.3, a software for simulating electromagnetic fields of high voltage lines, as I need it for my final year project. So far there were some dependencies I installed, but there is still a problem; output of configure:

> orphefs@orph:~/Desktop/ulysses-0.9.3$ ./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking whether g++ supports -Wmissing-format-attribute... yes
checking whether g++ supports -Wundef... yes
checking whether g++ supports -Wno-long-long... yes
checking whether g++ supports -Wnon-virtual-dtor... yes
checking whether g++ supports -fno-exceptions... yes
checking whether g++ supports -fno-check-new... yes
checking whether g++ supports -fno-common... yes
checking whether g++ supports -fexceptions... yes
checking how to run the C++ preprocessor... g++ -E
not using lib directory suffix
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking for a sed that does not truncate output... 
checking whether ln -s works... yes
checking how to recognise dependant libraries... pass_all
checking for egrep... grep -E
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
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag  works... no
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... no
checking if g++ supports -c -o file.o... no
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
appending configuration tag "GCJ" to libtool
checking if gcj supports -fno-rtti -fno-exceptions... (cached) no
checking for gcj option to produce PIC... -fPIC
checking if gcj PIC flag -fPIC works... no
checking if gcj supports -c -o file.o... no
checking whether the gcj linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for strlcat... no
checking if strlcat needs custom prototype... yes - in libkdefakes
checking for strlcpy... no
checking if strlcpy needs custom prototype... yes - in libkdefakes
checking for main in -lutil... yes
checking for main in -lcompat... no
checking for crypt in -lcrypt... yes
checking for socklen_t... socklen_t
checking for dnet_ntoa in -ldnet... no
checking for dnet_ntoa in -ldnet_stub... no
checking for inet_ntoa... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking crt_externs.h usability... no
checking crt_externs.h presence... no
checking for crt_externs.h... no
checking for _NSGetEnviron... no
checking for sys/types.h... (cached) yes
checking for stdint.h... (cached) yes
checking for poll in -lpoll... no
checking CoreAudio/CoreAudio.h usability... no
checking CoreAudio/CoreAudio.h presence... no
checking for CoreAudio/CoreAudio.h... no
checking if res_init needs -lresolv... yes
checking if res_init is available... yes
checking for killpg in -lucb... no
checking for int... yes
checking size of int... 4
checking for long... yes
checking size of long... 8
checking for char *... yes
checking size of char *... 8
checking for dlopen in -ldl... yes
checking for shl_unload in -ldld... no
checking for size_t... yes
checking size of size_t... 8
checking for unsigned long... yes
checking size of unsigned long... 8
checking sizeof size_t == sizeof unsigned long... yes
checking for vsnprintf... yes
checking for snprintf... yes
checking for X... libraries /usr/lib, headers .
checking for IceConnectionNumber in -lICE... yes
checking for libXext... yes
checking for pthread_create in -lpthread... yes
checking for extra includes... no
checking for extra libs... no
checking for libz... -lz
checking for libpng... -lpng -lz -lm
checking for libjpeg6b... no
checking for libjpeg... -ljpeg
checking for Qt... libraries /usr/share/qt3/lib, headers /usr/share/qt3/include using -mt
checking if Qt compiles without flags... yes
checking for moc... /usr/share/qt3/bin/moc
checking for uic... /usr/share/qt3/bin/uic
checking whether uic supports -L ... yes
checking whether uic supports -nounload ... yes
checking if Qt needs -ljpeg... no
checking for rpath... yes
checking for KDE... libraries /usr/lib, headers /usr/include/kde
checking if UIC has KDE plugins available... yes
checking for KDE paths... defaults
checking for dcopidl... /usr/bin/dcopidl
checking for dcopidl2cpp... /usr/bin/dcopidl2cpp
checking for mcopidl... /usr/bin/mcopidl
checking for artsc-config... /usr/bin/artsc-config
checking for kde-config... /usr/bin/kde-config
checking for meinproc... /usr/bin/meinproc
checking whether byte ordering is bigendian... no
checking for MAXPATHLEN... 4096
checking for the Coin 3D graphics library... configure: error:
                Unable to link to Coin library. If you
                just installed it: try running ldconfig
                as root


I downloaded the Coin 3D Graphics library, this is the output of Coin's configure:

> orphefs@orph:~/Desktop/Coin-3.0.0$ ./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking setup for wrapmsvc.exe... not working (as expected)
checking for distcheck mode... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking whether to enable maintainer-specific portions of Makefiles... no
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
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
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
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
checking dynamic linker characteristics... GNU/Linux ld.so
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
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking if the C++ compiler environment is ok... true
checking if the compiler handles for() loops in inlined constructors... yes
checking if the compiler handles switch statements in virtual destructors... yes
checking if this is a version of GCC with a known nasty optimization bug... false
checking for __builtin_expect()... found
checking if assert() uses __builtin_expect()... no
checking for function name variable for CPP compiler... __func__
checking for function name variable for C compiler... __func__
checking for Win32 threads... false
checking for POSIX threads... -D_REENTRANT   -lpthread
checking the struct timespec resolution... nsecs
checking for unistd.h... (cached) yes
checking for sys/types.h... (cached) yes
checking for inttypes.h... (cached) yes
checking for stdint.h... (cached) yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking sys/timeb.h usability... yes
checking sys/timeb.h presence... yes
checking for sys/timeb.h... yes
checking time.h usability... yes
checking time.h presence... yes
checking for time.h... yes
checking io.h usability... no
checking io.h presence... no
checking for io.h... no
checking windows.h usability... no
checking windows.h presence... no
checking for windows.h... no
checking libgen.h usability... yes
checking libgen.h presence... yes
checking for libgen.h... yes
checking direct.h usability... no
checking direct.h presence... no
checking for direct.h... no
checking for strings.h... (cached) yes
checking ieeefp.h usability... no
checking ieeefp.h presence... no
checking for ieeefp.h... no
checking for flex file adjustments... none
checking for tlhelp32.h... no
checking for _splitpath()... not found
checking if the Win32 API is available... no
checking for sys/unistd.h... yes
checking for IN_PATH define conflict... no
checking for netinet/in.h... true
checking for inttypes.h... (cached) yes
checking for stdint.h... (cached) yes
checking for sys/types.h... (cached) yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking standard bytesize typedefs... available
checking for fstat() function... available
checking for BSD 4.3 isinf() function... available
checking for BSD 4.3 isnan() function... available
checking for BSD 4.3 finite() function... available
checking for fpclass() function... not available
checking for _fpclass() function... not available
checking type of timeval::tv_sec... __time_t
checking type of timeval::tv_usec... __suseconds_t
checking for perl... /usr/bin/perl
checking for dpkg-buildpackage... /usr/bin/dpkg-buildpackage
checking if user is simian... probably not
checking whether g++ accepts -fno-exceptions... yes
checking whether gcc accepts -W... yes
checking whether gcc accepts -Wall... yes
checking whether gcc accepts -Wno-unused... yes
checking whether gcc accepts -Wno-multichar... yes
checking whether g++ accepts -W... yes
checking whether g++ accepts -Wall... yes
checking whether g++ accepts -Wno-unused... yes
checking whether g++ accepts -Wno-multichar... yes
checking whether g++ accepts -Woverloaded-virtual... yes
checking for project release status... release version
checking whether gcc accepts -fno-builtin... yes
checking whether g++ accepts -fno-builtin... yes
checking whether g++ accepts -fno-for-scoping... no
checking whether gcc accepts -finline-functions... yes
checking whether g++ accepts -finline-functions... yes
checking whether gcc accepts -Wreturn-type... yes
checking whether g++ accepts -Wreturn-type... yes
checking whether gcc accepts -Wchar-subscripts... yes
checking whether g++ accepts -Wchar-subscripts... yes
checking whether gcc accepts -Wparentheses... yes
checking whether g++ accepts -Wparentheses... yes
checking whether snprintf() is available... yes
checking whether vsnprintf() is available... yes
checking for va_copy() stdarg macro... yes
checking whether quoting in macros can be done with hash symbol... yes
checking for GetEnvironmentVariable() function... no
checking for timeGetTime() function... no
checking for MessageBox() function... no
checking for QueryPerformanceCounter() function... no
checking for _ftime() function... no
checking for ftime() function... yes
checking for _getcwd() function... no
checking for getcwd() function... yes
checking for gettimeofday() function... yes
checking for strncasecmp() function... yes
checking for memmove() function... available
checking for bcopy() function... available
checking for _logb() function... no
checking mach-o/dyld.h usability... no
checking mach-o/dyld.h presence... no
checking for mach-o/dyld.h... no
checking whether we can use Mach-O dyld... no
checking for dlfcn.h... (cached) yes
checking for the dl library...   -ldl
checking for math functions library... no explicit linkage necessary
checking for ilogb() function... yes
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking whether we can link against X11... yes
checking whether the X11 shared memory extension is available... yes
checking if X11 linkage is ready... true
checking how to include gl.h... #include <GL/gl.h>
checking for OpenGL library dev-kit...   -lGL 
checking how to include glext.h... #include <GL/glext.h>
checking whether WGL is on the system... false
checking whether GLX is on the system... true
checking how to include glu.h... #include <GL/glu.h>
checking if GLU is available as part of GL library... false
checking for shared library suffix... .so
checking for cmp... Yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating bin/Makefile
config.status: creating include/Makefile
config.status: creating include/Inventor/Makefile
config.status: creating include/Inventor/C/Makefile
config.status: creating include/Inventor/C/XML/Makefile
config.status: creating include/Inventor/C/base/Makefile
config.status: creating include/Inventor/C/errors/Makefile
config.status: creating include/Inventor/C/glue/Makefile
config.status: creating include/Inventor/C/threads/Makefile
config.status: creating include/Inventor/VRMLnodes/Makefile
config.status: creating include/Inventor/XML/Makefile
config.status: creating include/Inventor/actions/Makefile
config.status: creating include/Inventor/bundles/Makefile
config.status: creating include/Inventor/caches/Makefile
config.status: creating include/Inventor/collision/Makefile
config.status: creating include/Inventor/details/Makefile
config.status: creating include/Inventor/draggers/Makefile
config.status: creating include/Inventor/elements/Makefile
config.status: creating include/Inventor/engines/Makefile
config.status: creating include/Inventor/errors/Makefile
config.status: creating include/Inventor/events/Makefile
config.status: creating include/Inventor/fields/Makefile
config.status: creating include/Inventor/lists/Makefile
config.status: creating include/Inventor/lock/Makefile
config.status: creating include/Inventor/manips/Makefile
config.status: creating include/Inventor/misc/Makefile
config.status: creating include/Inventor/nodekits/Makefile
config.status: creating include/Inventor/nodes/Makefile
config.status: creating include/Inventor/projectors/Makefile
config.status: creating include/Inventor/sensors/Makefile
config.status: creating include/Inventor/system/Makefile
config.status: creating include/Inventor/threads/Makefile
config.status: creating include/Inventor/tools/Makefile
config.status: creating include/Inventor/scxml/Makefile
config.status: creating include/Inventor/annex/Makefile
config.status: creating include/Inventor/annex/HardCopy/Makefile
config.status: creating include/Inventor/annex/ForeignFiles/Makefile
config.status: creating include/Inventor/annex/FXViz/Makefile
config.status: creating include/Inventor/annex/FXViz/elements/Makefile
config.status: creating include/Inventor/annex/FXViz/nodes/Makefile
config.status: creating include/Inventor/annex/Profiler/Makefile
config.status: creating include/Inventor/annex/Profiler/elements/Makefile
config.status: creating include/Inventor/annex/Profiler/engines/Makefile
config.status: creating include/Inventor/annex/Profiler/nodes/Makefile
config.status: creating include/Inventor/annex/Profiler/nodekits/Makefile
config.status: creating include/Inventor/annex/Profiler/utils/Makefile
config.status: creating data/Makefile
config.status: creating data/draggerDefaults/Makefile
config.status: creating data/shaders/Makefile
config.status: creating data/shaders/lights/Makefile
config.status: creating data/shaders/vsm/Makefile
config.status: creating data/scxml/Makefile
config.status: creating data/scxml/navigation/Makefile
config.status: creating man/Makefile
config.status: creating man/man1/Makefile
config.status: creating man/man3/Makefile
config.status: creating html/Makefile
config.status: creating src/Makefile
config.status: creating src/base/Makefile
config.status: creating src/actions/Makefile
config.status: creating src/bundles/Makefile
config.status: creating src/caches/Makefile
config.status: creating src/collision/Makefile
config.status: creating src/details/Makefile
config.status: creating src/draggers/Makefile
config.status: creating src/elements/Makefile
config.status: creating src/elements/GL/Makefile
config.status: creating src/engines/Makefile
config.status: creating src/errors/Makefile
config.status: creating src/events/Makefile
config.status: creating src/fields/Makefile
config.status: creating src/fonts/Makefile
config.status: creating src/glue/Makefile
config.status: creating src/io/Makefile
config.status: creating src/manips/Makefile
config.status: creating src/misc/Makefile
config.status: creating src/lists/Makefile
config.status: creating src/navigation/Makefile
config.status: creating src/nodekits/Makefile
config.status: creating src/nodes/Makefile
config.status: creating src/projectors/Makefile
config.status: creating src/3ds/Makefile
config.status: creating src/sensors/Makefile
config.status: creating src/upgraders/Makefile
config.status: creating src/shapenodes/Makefile
config.status: creating src/threads/Makefile
config.status: creating src/extensions/Makefile
config.status: creating src/vrml97/Makefile
config.status: creating src/hardcopy/Makefile
config.status: creating src/shaders/Makefile
config.status: creating src/shadows/Makefile
config.status: creating src/geo/Makefile
config.status: creating src/foreignfiles/Makefile
config.status: creating src/xml/Makefile
config.status: creating src/xml/expat/Makefile
config.status: creating src/profiler/Makefile
config.status: creating src/scxml/Makefile
config.status: creating src/doc/Makefile
config.status: creating testsuite/Makefile
config.status: creating cfg/gendsp.pl
config.status: creating src/discard.h
config.status: src/discard.h is unchanged
config.status: creating src/config.h
config.status: src/config.h is unchanged
config.status: creating src/setup.h
config.status: src/setup.h is unchanged
config.status: executing depfiles commands

Coin configuration settings:
  Library version:          3.0.0
  Generate Java wrapper:    No (default)
  3ds import capabilities:  No (enable with --enable-3ds-import)
  javascript capabilities:  Yes
  VRML97 support:           Yes
  System threads API:       POSIX
  Thread safe traversals:   No (enable with --enable-threadsafe)
  simage linkage:           run-time binding
  OpenAL support:           Yes, run-time binding
  Sound support:            Yes
  Fontconfig support:       Yes, run-time binding
  SpiderMonkey support:     Yes, run-time binding
  FreeType library:         Yes, run-time binding
  zlib support:             Yes, run-time binding
  bzip2 support:            Yes, run-time binding
  GLU linkage:              run-time binding
  Installation prefix:      /usr/local

Coin configuration warnings:
  * Your $PATH variable does not appear to include "/usr/local/bin"


Does the $PATH variable have to do with Ulysses configure not seeing the link to the library?

I read all INSTALL files, tried different commands that were advised, even installed practically all versions of Coin 3D library through Synaptic Package Manager, still not being able to install the software...:( I need your help, I'm a newbie!!!

Thank you for taking the time to read :)

---

### Post by orphefs on 2008-10-19
any suggestions at all? im really desperate to solve this problem!!!

---

### Post by ee7linux on 2013-02-19
10 years later lol ... 

I had the same problem (plus other one) installing Coin3D-3.1.3, so I will post the solution ;)  

· The first problem ... 
```

Coin configuration warnings:
* Your $PATH variable does not appear to include "/usr/local/bin" 

```
... can be solved by executing "configure" with two tags
```

./configure --prefix=/usr/local --bindir=/usr/local/bin 

```
(Source: [http://mailst.org/thread-45463.html]("http://mailst.org/thread-45463.html") + Google Translate)

· The second issue (at least in the version 3.1.3) is a very ugly error while "making" 
```

In file included from ../../include/Inventor/actions/SoAction.h:27:0,
                 from SoAction.cpp:197:
../../include/Inventor/SbBasic.h: In instantiation of ‘void SbDividerChk(const char*, Type) [with Type = float]’:
../../include/Inventor/SbVec3f.h:78:81:   required from here
../../include/Inventor/SbBasic.h:99:5: error: ‘cc_debugerror_post’ was not declared in this scope, and no declarations were found by argument-dependent lookup at the point of instantiation [-fpermissive]
In file included from ../../include/Inventor/errors/SoDebugError.h:28:0,
                 from ../../include/Inventor/SbVec3f.h:31,
                 from ../../include/Inventor/SbColor.h:28,
                 from ../../include/Inventor/elements/SoLazyElement.h:29,
                 from ../../include/Inventor/nodes/SoLightModel.h:29,
                 from ../../include/Inventor/actions/SoCallbackAction.h:35,
                 from ../../include/Inventor/actions/SoActions.h:27,
                 from SoAction.cpp:206:
../../include/Inventor/C/errors/debugerror.h:59:19: note: ‘void cc_debugerror_post(const char*, const char*, ...)’ declared here, later in the translation unit
In file included from ../../include/Inventor/actions/SoAction.h:27:0,
                 from SoAction.cpp:197:
../../include/Inventor/SbBasic.h: In instantiation of ‘void SbDividerChk(const char*, Type) [with Type = int]’:
../../include/Inventor/SbVec2s.h:71:77:   required from here
../../include/Inventor/SbBasic.h:99:5: error: ‘cc_debugerror_post’ was not declared in this scope, and no declarations were found by argument-dependent lookup at the point of instantiation [-fpermissive]
In file included from ../../include/Inventor/errors/SoDebugError.h:28:0,
                 from ../../include/Inventor/SbVec3f.h:31,
                 from ../../include/Inventor/SbColor.h:28,
                 from ../../include/Inventor/elements/SoLazyElement.h:29,
                 from ../../include/Inventor/nodes/SoLightModel.h:29,
                 from ../../include/Inventor/actions/SoCallbackAction.h:35,
                 from ../../include/Inventor/actions/SoActions.h:27,
                 from SoAction.cpp:206:
../../include/Inventor/C/errors/debugerror.h:59:19: note: ‘void cc_debugerror_post(const char*, const char*, ...)’ declared here, later in the translation unit
In file included from ../../include/Inventor/actions/SoAction.h:27:0,
                 from SoAction.cpp:197:
../../include/Inventor/SbBasic.h: In instantiation of ‘void SbDividerChk(const char*, Type) [with Type = double]’:
../../include/Inventor/SbVec2s.h:72:83:   required from here
../../include/Inventor/SbBasic.h:99:5: error: ‘cc_debugerror_post’ was not declared in this scope, and no declarations were found by argument-dependent lookup at the point of instantiation [-fpermissive]
In file included from ../../include/Inventor/errors/SoDebugError.h:28:0,
                 from ../../include/Inventor/SbVec3f.h:31,
                 from ../../include/Inventor/SbColor.h:28,
                 from ../../include/Inventor/elements/SoLazyElement.h:29,
                 from ../../include/Inventor/nodes/SoLightModel.h:29,
                 from ../../include/Inventor/actions/SoCallbackAction.h:35,
                 from ../../include/Inventor/actions/SoActions.h:27,
                 from SoAction.cpp:206:
../../include/Inventor/C/errors/debugerror.h:59:19: note: ‘void cc_debugerror_post(const char*, const char*, ...)’ declared here, later in the translation unit
make[4]: *** [SoAction.lo] Error 1
make[4]: Leaving directory `/home/warren/geant4/CompressedFiles/Coin-3.1.3/src/actions'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/warren/geant4/CompressedFiles/Coin-3.1.3/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/warren/geant4/CompressedFiles/Coin-3.1.3/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/warren/geant4/CompressedFiles/Coin-3.1.3'
make: *** [all] Error 2

```

To fix this I only include the header
```

#include <Inventor/C/errors/debugerror.h>

``` 
... at the begin of the file Coin-3.1.3/include/Inventor/SbBasic.h ... and problem solved :D

I hope this will be useful for someone else,
Gratings!
Warren.

---

### Post by wildmanne39 on 2013-02-19
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

