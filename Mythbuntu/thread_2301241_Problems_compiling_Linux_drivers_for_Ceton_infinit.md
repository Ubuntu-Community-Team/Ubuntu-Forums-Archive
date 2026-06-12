---
title: "Problems compiling Linux drivers for Ceton infinitv 4 usb"
date: 2015-10-31
forum: Mythbuntu
---

### Post by wideleg84 on 2015-10-31
Hello!  I've just bought a Ceton infinitv 4 USB tuner, and I'm TRYING to compile the Linux driver for it.  However, I've not even been able to perform the CONFIG successfully.  Whenever I try, it says that "libnl -l" is missing.  It also suggests that I may need to modify my "Environment Variable," whatever that may be.  (Need I say that I'm new to Linux?)  Oh, I'm using Mythbuintu 14.04.2, and I used Synaptic to try to make sure that "libnl" is properly installed.  Having said all of that, what am I doing wrong, and how do I correct it?  Many thanks in advance for any advice or assistance!

Wideleg84

---

### Post by blm-ubunet on 2015-10-31
Install "libnl-dev" or "libnl-3.dev package..

You need the shared system libs to (ultimately) run stuff & the -dev packages to provide headers for linking to the library.

---

### Post by wideleg84 on 2015-11-01
I did that, and the config seems to have run successfully.  HOWEVER--when I ran the make command, it gave me an error message saying, "Undefined reference to g_thread_init."  Here's a copy of what happened, based on my following the instructions in the README file:

```
tom@tom-G41D-M7:~$ cd Downloads
tom@tom-G41D-M7:~/Downloads$ cd infinitv-usbd-0.1.0
tom@tom-G41D-M7:~/Downloads/infinitv-usbd-0.1.0$ ./configure --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
./configure: line 2732: m4-#: command not found
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking how to print strings... printf
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking how to convert x86_64-unknown-linux-gnu file names to x86_64-unknown-linux-gnu format... func_convert_file_noop
checking how to convert x86_64-unknown-linux-gnu file names to toolchain format... func_convert_file_noop
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for dlltool... no
checking how to associate runtime and link libraries... printf %s\n
checking for ar... ar
checking for archiver @FILE support... @
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for sysroot... no
checking for mt... mt
checking if mt is a manifest tool... no
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
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GIO... yes
checking for GIO_UNIX... yes
checking for LIBNL... yes
checking for GUSB... yes
checking for stdlib.h... (cached) yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands
tom@tom-G41D-M7:~/Downloads/infinitv-usbd-0.1.0$ make
make  all-recursive
make[1]: Entering directory `/home/tom/Downloads/infinitv-usbd-0.1.0'
Making all in src
make[2]: Entering directory `/home/tom/Downloads/infinitv-usbd-0.1.0/src'
  CC     main.o
main.c: In function â&#8364;&#732;mainâ&#8364;&#8482;:
main.c:200:5: warning: â&#8364;&#732;g_thread_initâ&#8364;&#8482; is deprecated (declared at /usr/include/glib-2.0/glib/deprecated/gthread.h:261) [-Wdeprecated-declarations]
     g_thread_init(NULL);
     ^
main.c:201:5: warning: â&#8364;&#732;g_type_initâ&#8364;&#8482; is deprecated (declared at /usr/include/glib-2.0/gobject/gtype.h:667) [-Wdeprecated-declarations]
     g_type_init();
     ^
  CC     inet_util.o
  CC     rpc.o
rpc.c: In function â&#8364;&#732;rpc_readâ&#8364;&#8482;:
rpc.c:67:13: warning: format â&#8364;&#732;%dâ&#8364;&#8482; expects argument of type â&#8364;&#732;intâ&#8364;&#8482;, but argument 2 has type â&#8364;&#732;gssizeâ&#8364;&#8482; [-Wformat=]
             g_print("recv error %d\n", len);
             ^
  CC     rtp.o
rtp.c: In function â&#8364;&#732;rtp_send_packetâ&#8364;&#8482;:
rtp.c:137:9: warning: format â&#8364;&#732;%dâ&#8364;&#8482; expects argument of type â&#8364;&#732;intâ&#8364;&#8482;, but argument 2 has type â&#8364;&#732;gssizeâ&#8364;&#8482; [-Wformat=]
         g_printerr("failed to write %d %s\n", written, error->message);
         ^
  CCLD   infinitv_usbd
main.o: In function `main':
/home/tom/Downloads/infinitv-usbd-0.1.0/src/main.c:200: undefined reference to `g_thread_init'
collect2: error: ld returned 1 exit status
make[2]: *** [infinitv_usbd] Error 1
make[2]: Leaving directory `/home/tom/Downloads/infinitv-usbd-0.1.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tom/Downloads/infinitv-usbd-0.1.0'
make: *** [all] Error 2
tom@tom-G41D-M7:~/Downloads/infinitv-usbd-0.1.0$ 
```

What now?  (Thanks again for any help or advice!)

Wideleg84

---

### Post by blm-ubunet on 2015-11-01
Based on some other internet posts I'd guess there is a problem compiling against newer kernels.
But it could be (v doubtful) missing kernel headers package (the headers meta package always matches the latest  kernel meta package).
Without downloading & looking at the code the above is just guessing.

uname -r

You might have to force/pin an older kernel (if still avail in synaptic) that is supported by ceton code until someone fixes problem.
The Ceton readme should explicitly state supported kernel version but this advice might be impossible to follow.

---

### Post by wideleg84 on 2015-11-01
How would I go about doing that?  Please remember that you're talking to a Linux newbie here, so I'm gonna need at least some hand-holding (i.e., step-by-step instructions).

---

### Post by blm-ubunet on 2015-11-03
Looks like I was way off the mark..
[http://forums.fedoraforum.org/showthread.php?t=298085](http://forums.fedoraforum.org/showthread.php?t=298085)
```
./configure --prefix=/usr LIBS=-lgthread
```
would appear to be the soln.

---

### Post by wideleg84 on 2015-11-03
OK, I'll try that!  Thanks for posting it!

---

### Post by wideleg84 on 2015-11-03
Unfortunately, that didn't work either!  Here's the cong log it compiled:

This file contains any messages produced by compilers while
running configure, to aid debugging if configure makes a mistake.

It was created by infinitv-usbd configure 0.1.0, which was
generated by GNU Autoconf 2.68.  Invocation command line was

```
$ ./configure --prefix=/usr LIBS=lgthread

## --------- ##
## Platform. ##
## --------- ##

hostname = tom-G41D-M7
uname -m = x86_64
uname -r = 3.16.0-51-generic
uname -s = Linux
uname -v = #69~14.04.1-Ubuntu SMP Wed Oct 7 15:32:41 UTC 2015

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = unknown
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
/usr/bin/hostinfo      = unknown
/bin/machine           = unknown
/usr/bin/oslevel       = unknown
/bin/universe          = unknown

PATH: /usr/local/sbin
PATH: /usr/local/bin
PATH: /usr/sbin
PATH: /usr/bin
PATH: /sbin
PATH: /bin
PATH: /usr/games
PATH: /usr/local/games


## ----------- ##
## Core tests. ##
## ----------- ##

configure:2270: checking for a BSD-compatible install
configure:2338: result: /usr/bin/install -c
configure:2349: checking whether build environment is sane
configure:2399: result: yes
configure:2540: checking for a thread-safe mkdir -p
configure:2579: result: /bin/mkdir -p
configure:2592: checking for gawk
configure:2622: result: no
configure:2592: checking for mawk
configure:2608: found /usr/bin/mawk
configure:2619: result: mawk
configure:2630: checking whether make sets $(MAKE)
configure:2652: result: yes
configure:2778: checking build system type
configure:2792: result: x86_64-unknown-linux-gnu
configure:2812: checking host system type
configure:2825: result: x86_64-unknown-linux-gnu
configure:2866: checking how to print strings
configure:2893: result: printf
configure:2926: checking for style of include used by make
configure:2954: result: GNU
configure:3024: checking for gcc
configure:3040: found /usr/bin/gcc
configure:3051: result: gcc
configure:3280: checking for C compiler version
configure:3289: gcc --version >&5
gcc (Ubuntu 4.8.4-2ubuntu1~14.04) 4.8.4
Copyright (C) 2013 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:3300: $? = 0
configure:3289: gcc -v >&5
Using built-in specs.
COLLECT_GCC=gcc
COLLECT_LTO_WRAPPER=/usr/lib/gcc/x86_64-linux-gnu/4.8/lto-wrapper
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.8.4-2ubuntu1~14.04' --with-bugurl=file:///usr/share/doc/gcc-4.8/README.Bugs --enable-languages=c,c++,java,go,d,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.8 --enable-shared --enable-linker-build-id --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.8 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-gnu-unique-object --disable-libmudflap --enable-plugin --with-system-zlib --disable-browser-plugin --enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.5.0-gcj-4.8-amd64/jre --enable-java-home --with-jvm-root-dir=/usr/lib/jvm/java-1.5.0-gcj-4.8-amd64 --with-jvm-jar-dir=/usr/lib/jvm-exports/java-1.5.0-gcj-4.8-amd64 --with-arch-directory=amd64 --with-ecj-jar=/usr/share/java/eclipse-ecj.jar --enable-objc-gc --enable-multiarch --disable-werror --with-arch-32=i686 --with-abi=m64 --with-multilib-list=m32,m64,mx32 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.8.4 (Ubuntu 4.8.4-2ubuntu1~14.04) 
configure:3300: $? = 0
configure:3289: gcc -V >&5
gcc: error: unrecognized command line option '-V'
gcc: fatal error: no input files
compilation terminated.
configure:3300: $? = 4
configure:3289: gcc -qversion >&5
gcc: error: unrecognized command line option '-qversion'
gcc: fatal error: no input files
compilation terminated.
configure:3300: $? = 4
configure:3320: checking whether the C compiler works
configure:3342: gcc    conftest.c lgthread >&5
gcc: error: lgthread: No such file or directory
configure:3346: $? = 1
configure:3384: result: no
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "infinitv-usbd"
| #define PACKAGE_TARNAME "infinitv-usbd"
| #define PACKAGE_VERSION "0.1.0"
| #define PACKAGE_STRING "infinitv-usbd 0.1.0"
| #define PACKAGE_BUGREPORT "linux@cetoncorp.com"
| #define PACKAGE_URL ""
| #define PACKAGE "infinitv-usbd"
| #define VERSION "0.1.0"
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:3389: error: in `/home/tom/Downloads/infinitv-usbd-0.1.0':
configure:3391: error: C compiler cannot create executables
See `config.log' for more details

## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_build=x86_64-unknown-linux-gnu
ac_cv_env_CC_set=
ac_cv_env_CC_value=
ac_cv_env_CFLAGS_set=
ac_cv_env_CFLAGS_value=
ac_cv_env_CPPFLAGS_set=
ac_cv_env_CPPFLAGS_value=
ac_cv_env_CPP_set=
ac_cv_env_CPP_value=
ac_cv_env_GIO_CFLAGS_set=
ac_cv_env_GIO_CFLAGS_value=
ac_cv_env_GIO_LIBS_set=
ac_cv_env_GIO_LIBS_value=
ac_cv_env_GIO_UNIX_CFLAGS_set=
ac_cv_env_GIO_UNIX_CFLAGS_value=
ac_cv_env_GIO_UNIX_LIBS_set=
ac_cv_env_GIO_UNIX_LIBS_value=
ac_cv_env_GUSB_CFLAGS_set=
ac_cv_env_GUSB_CFLAGS_value=
ac_cv_env_GUSB_LIBS_set=
ac_cv_env_GUSB_LIBS_value=
ac_cv_env_LDFLAGS_set=
ac_cv_env_LDFLAGS_value=
ac_cv_env_LIBNL_CFLAGS_set=
ac_cv_env_LIBNL_CFLAGS_value=
ac_cv_env_LIBNL_LIBS_set=
ac_cv_env_LIBNL_LIBS_value=
ac_cv_env_LIBS_set=set
ac_cv_env_LIBS_value=lgthread
ac_cv_env_PKG_CONFIG_LIBDIR_set=
ac_cv_env_PKG_CONFIG_LIBDIR_value=
ac_cv_env_PKG_CONFIG_PATH_set=
ac_cv_env_PKG_CONFIG_PATH_value=
ac_cv_env_PKG_CONFIG_set=
ac_cv_env_PKG_CONFIG_value=
ac_cv_env_build_alias_set=
ac_cv_env_build_alias_value=
ac_cv_env_host_alias_set=
ac_cv_env_host_alias_value=
ac_cv_env_target_alias_set=
ac_cv_env_target_alias_value=
ac_cv_host=x86_64-unknown-linux-gnu
ac_cv_path_install='/usr/bin/install -c'
ac_cv_path_mkdir=/bin/mkdir
ac_cv_prog_AWK=mawk
ac_cv_prog_ac_ct_CC=gcc
ac_cv_prog_make_make_set=yes

## ----------------- ##
## Output variables. ##
## ----------------- ##

ACLOCAL='${SHELL} /home/tom/Downloads/infinitv-usbd-0.1.0/build-aux/missing --run aclocal-1.11'
AMDEPBACKSLASH='\'
AMDEP_FALSE='#'
AMDEP_TRUE=''
AMTAR='${SHELL} /home/tom/Downloads/infinitv-usbd-0.1.0/build-aux/missing --run tar'
AM_BACKSLASH='\'
AM_DEFAULT_VERBOSITY='0'
AR=''
AUTOCONF='${SHELL} /home/tom/Downloads/infinitv-usbd-0.1.0/build-aux/missing --run autoconf'
AUTOHEADER='${SHELL} /home/tom/Downloads/infinitv-usbd-0.1.0/build-aux/missing --run autoheader'
AUTOMAKE='${SHELL} /home/tom/Downloads/infinitv-usbd-0.1.0/build-aux/missing --run automake-1.11'
AWK='mawk'
CC='gcc'
CCDEPMODE=''
CFLAGS=''
CPP=''
CPPFLAGS=''
CYGPATH_W='echo'
DEFS=''
DEPDIR='.deps'
DLLTOOL=''
DSYMUTIL=''
DUMPBIN=''
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EGREP=''
EXEEXT=''
FGREP=''
GIO_CFLAGS=''
GIO_LIBS=''
GIO_UNIX_CFLAGS=''
GIO_UNIX_LIBS=''
GREP=''
GUSB_CFLAGS=''
GUSB_LIBS=''
INSTALL_DATA='${INSTALL} -m 644'
INSTALL_PROGRAM='${INSTALL}'
INSTALL_SCRIPT='${INSTALL}'
INSTALL_STRIP_PROGRAM='$(install_sh) -c -s'
LD=''
LDFLAGS=''
LIBNL_CFLAGS=''
LIBNL_LIBS=''
LIBOBJS=''
LIBS='lgthread'
LIBTOOL=''
LIPO=''
LN_S=''
LTLIBOBJS=''
MAKEINFO='${SHELL} /home/tom/Downloads/infinitv-usbd-0.1.0/build-aux/missing --run makeinfo'
MANIFEST_TOOL=''
MKDIR_P='/bin/mkdir -p'
NM=''
NMEDIT=''
OBJDUMP=''
OBJEXT=''
OTOOL64=''
OTOOL=''
PACKAGE='infinitv-usbd'
PACKAGE_BUGREPORT='linux@cetoncorp.com'
PACKAGE_NAME='infinitv-usbd'
PACKAGE_STRING='infinitv-usbd 0.1.0'
PACKAGE_TARNAME='infinitv-usbd'
PACKAGE_URL=''
PACKAGE_VERSION='0.1.0'
PATH_SEPARATOR=':'
PKG_CONFIG=''
PKG_CONFIG_LIBDIR=''
PKG_CONFIG_PATH=''
RANLIB=''
SED=''
SET_MAKE=''
SHELL='/bin/bash'
STRIP=''
VERSION='0.1.0'
ac_ct_AR=''
ac_ct_CC='gcc'
ac_ct_DUMPBIN=''
am__EXEEXT_FALSE=''
am__EXEEXT_TRUE=''
am__fastdepCC_FALSE=''
am__fastdepCC_TRUE=''
am__include='include'
am__isrc=''
am__leading_dot='.'
am__quote=''
am__tar='${AMTAR} chof - "$$tardir"'
am__untar='${AMTAR} xf -'
bindir='${exec_prefix}/bin'
build='x86_64-unknown-linux-gnu'
build_alias=''
build_cpu='x86_64'
build_os='linux-gnu'
build_vendor='unknown'
datadir='${datarootdir}'
datarootdir='${prefix}/share'
docdir='${datarootdir}/doc/${PACKAGE_TARNAME}'
dvidir='${docdir}'
exec_prefix='NONE'
host='x86_64-unknown-linux-gnu'
host_alias=''
host_cpu='x86_64'
host_os='linux-gnu'
host_vendor='unknown'
htmldir='${docdir}'
includedir='${prefix}/include'
infodir='${datarootdir}/info'
install_sh='${SHELL} /home/tom/Downloads/infinitv-usbd-0.1.0/build-aux/install-sh'
libdir='${exec_prefix}/lib'
libexecdir='${exec_prefix}/libexec'
localedir='${datarootdir}/locale'
localstatedir='${prefix}/var'
mandir='${datarootdir}/man'
mkdir_p='/bin/mkdir -p'
oldincludedir='/usr/include'
pdfdir='${docdir}'
prefix='/usr'
program_transform_name='s,x,x,'
psdir='${docdir}'
sbindir='${exec_prefix}/sbin'
sharedstatedir='${prefix}/com'
sysconfdir='${prefix}/etc'
target_alias=''

## ----------- ##
## confdefs.h. ##
## ----------- ##

/* confdefs.h */
#define PACKAGE_NAME "infinitv-usbd"
#define PACKAGE_TARNAME "infinitv-usbd"
#define PACKAGE_VERSION "0.1.0"
#define PACKAGE_STRING "infinitv-usbd 0.1.0"
#define PACKAGE_BUGREPORT "linux@cetoncorp.com"
#define PACKAGE_URL ""
#define PACKAGE "infinitv-usbd"
#define VERSION "0.1.0"

configure: exit 77
```

So what next, my friend?

Wideleg84

---

### Post by blm-ubunet on 2015-11-05
There's a typo in your configure command option, a missing "-".

---

### Post by deadflowr on 2015-11-05
Please use [code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168") when posting any terminal output.
thank you

---

### Post by wideleg84 on 2015-11-05
Where does it go?

---

### Post by wideleg84 on 2015-11-05
My apologies!  I'm still new to this, and didn't know about code tags.

---

### Post by wideleg84 on 2015-11-06
I finally figured out where to put the missing "-", and here's what happened next:

```

This file contains any messages produced by compilers while
running configure, to aid debugging if configure makes a mistake.

It was created by infinitv-usbd configure 0.1.0, which was
generated by GNU Autoconf 2.68.  Invocation command line was

  $ ./configure --prefix=/usr LIBS=-lgthread

## --------- ##
## Platform. ##
## --------- ##

hostname = tom-G41D-M7
uname -m = x86_64
uname -r = 3.16.0-52-generic
uname -s = Linux
uname -v = #71~14.04.1-Ubuntu SMP Fri Oct 23 17:24:53 UTC 2015

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = unknown
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
/usr/bin/hostinfo      = unknown
/bin/machine           = unknown
/usr/bin/oslevel       = unknown
/bin/universe          = unknown

PATH: /usr/local/sbin
PATH: /usr/local/bin
PATH: /usr/sbin
PATH: /usr/bin
PATH: /sbin
PATH: /bin
PATH: /usr/games
PATH: /usr/local/games


## ----------- ##
## Core tests. ##
## ----------- ##

configure:2270: checking for a BSD-compatible install
configure:2338: result: /usr/bin/install -c
configure:2349: checking whether build environment is sane
configure:2399: result: yes
configure:2540: checking for a thread-safe mkdir -p
configure:2579: result: /bin/mkdir -p
configure:2592: checking for gawk
configure:2622: result: no
configure:2592: checking for mawk
configure:2608: found /usr/bin/mawk
configure:2619: result: mawk
configure:2630: checking whether make sets $(MAKE)
configure:2652: result: yes
configure:2778: checking build system type
configure:2792: result: x86_64-unknown-linux-gnu
configure:2812: checking host system type
configure:2825: result: x86_64-unknown-linux-gnu
configure:2866: checking how to print strings
configure:2893: result: printf
configure:2926: checking for style of include used by make
configure:2954: result: GNU
configure:3024: checking for gcc
configure:3040: found /usr/bin/gcc
configure:3051: result: gcc
configure:3280: checking for C compiler version
configure:3289: gcc --version >&5
gcc (Ubuntu 4.8.4-2ubuntu1~14.04) 4.8.4
Copyright (C) 2013 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:3300: $? = 0
configure:3289: gcc -v >&5
Using built-in specs.
COLLECT_GCC=gcc
COLLECT_LTO_WRAPPER=/usr/lib/gcc/x86_64-linux-gnu/4.8/lto-wrapper
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.8.4-2ubuntu1~14.04' --with-bugurl=file:///usr/share/doc/gcc-4.8/README.Bugs --enable-languages=c,c++,java,go,d,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.8 --enable-shared --enable-linker-build-id --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.8 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-gnu-unique-object --disable-libmudflap --enable-plugin --with-system-zlib --disable-browser-plugin --enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.5.0-gcj-4.8-amd64/jre --enable-java-home --with-jvm-root-dir=/usr/lib/jvm/java-1.5.0-gcj-4.8-amd64 --with-jvm-jar-dir=/usr/lib/jvm-exports/java-1.5.0-gcj-4.8-amd64 --with-arch-directory=amd64 --with-ecj-jar=/usr/share/java/eclipse-ecj.jar --enable-objc-gc --enable-multiarch --disable-werror --with-arch-32=i686 --with-abi=m64 --with-multilib-list=m32,m64,mx32 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.8.4 (Ubuntu 4.8.4-2ubuntu1~14.04) 
configure:3300: $? = 0
configure:3289: gcc -V >&5
gcc: error: unrecognized command line option '-V'
gcc: fatal error: no input files
compilation terminated.
configure:3300: $? = 4
configure:3289: gcc -qversion >&5
gcc: error: unrecognized command line option '-qversion'
gcc: fatal error: no input files
compilation terminated.
configure:3300: $? = 4
configure:3320: checking whether the C compiler works
configure:3342: gcc    conftest.c -lgthread >&5
/usr/bin/ld: cannot find -lgthread
collect2: error: ld returned 1 exit status
configure:3346: $? = 1
configure:3384: result: no
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "infinitv-usbd"
| #define PACKAGE_TARNAME "infinitv-usbd"
| #define PACKAGE_VERSION "0.1.0"
| #define PACKAGE_STRING "infinitv-usbd 0.1.0"
| #define PACKAGE_BUGREPORT "linux@cetoncorp.com"
| #define PACKAGE_URL ""
| #define PACKAGE "infinitv-usbd"
| #define VERSION "0.1.0"
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:3389: error: in `/home/tom/Downloads/infinitv-usbd-0.1.0':
configure:3391: error: C compiler cannot create executables
See `config.log' for more details

## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_build=x86_64-unknown-linux-gnu
ac_cv_env_CC_set=
ac_cv_env_CC_value=
ac_cv_env_CFLAGS_set=
ac_cv_env_CFLAGS_value=
ac_cv_env_CPPFLAGS_set=
ac_cv_env_CPPFLAGS_value=
ac_cv_env_CPP_set=
ac_cv_env_CPP_value=
ac_cv_env_GIO_CFLAGS_set=
ac_cv_env_GIO_CFLAGS_value=
ac_cv_env_GIO_LIBS_set=
ac_cv_env_GIO_LIBS_value=
ac_cv_env_GIO_UNIX_CFLAGS_set=
ac_cv_env_GIO_UNIX_CFLAGS_value=
ac_cv_env_GIO_UNIX_LIBS_set=
ac_cv_env_GIO_UNIX_LIBS_value=
ac_cv_env_GUSB_CFLAGS_set=
ac_cv_env_GUSB_CFLAGS_value=
ac_cv_env_GUSB_LIBS_set=
ac_cv_env_GUSB_LIBS_value=
ac_cv_env_LDFLAGS_set=
ac_cv_env_LDFLAGS_value=
ac_cv_env_LIBNL_CFLAGS_set=
ac_cv_env_LIBNL_CFLAGS_value=
ac_cv_env_LIBNL_LIBS_set=
ac_cv_env_LIBNL_LIBS_value=
ac_cv_env_LIBS_set=set
ac_cv_env_LIBS_value=-lgthread
ac_cv_env_PKG_CONFIG_LIBDIR_set=
ac_cv_env_PKG_CONFIG_LIBDIR_value=
ac_cv_env_PKG_CONFIG_PATH_set=
ac_cv_env_PKG_CONFIG_PATH_value=
ac_cv_env_PKG_CONFIG_set=
ac_cv_env_PKG_CONFIG_value=
ac_cv_env_build_alias_set=
ac_cv_env_build_alias_value=
ac_cv_env_host_alias_set=
ac_cv_env_host_alias_value=
ac_cv_env_target_alias_set=
ac_cv_env_target_alias_value=
ac_cv_host=x86_64-unknown-linux-gnu
ac_cv_path_install='/usr/bin/install -c'
ac_cv_path_mkdir=/bin/mkdir
ac_cv_prog_AWK=mawk
ac_cv_prog_ac_ct_CC=gcc
ac_cv_prog_make_make_set=yes

## ----------------- ##
## Output variables. ##
## ----------------- ##

ACLOCAL='${SHELL} /home/tom/Downloads/infinitv-usbd-0.1.0/build-aux/missing --run aclocal-1.11'
AMDEPBACKSLASH='\'
AMDEP_FALSE='#'
AMDEP_TRUE=''
AMTAR='${SHELL} /home/tom/Downloads/infinitv-usbd-0.1.0/build-aux/missing --run tar'
AM_BACKSLASH='\'
AM_DEFAULT_VERBOSITY='0'
AR=''
AUTOCONF='${SHELL} /home/tom/Downloads/infinitv-usbd-0.1.0/build-aux/missing --run autoconf'
AUTOHEADER='${SHELL} /home/tom/Downloads/infinitv-usbd-0.1.0/build-aux/missing --run autoheader'
AUTOMAKE='${SHELL} /home/tom/Downloads/infinitv-usbd-0.1.0/build-aux/missing --run automake-1.11'
AWK='mawk'
CC='gcc'
CCDEPMODE=''
CFLAGS=''
CPP=''
CPPFLAGS=''
CYGPATH_W='echo'
DEFS=''
DEPDIR='.deps'
DLLTOOL=''
DSYMUTIL=''
DUMPBIN=''
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EGREP=''
EXEEXT=''
FGREP=''
GIO_CFLAGS=''
GIO_LIBS=''
GIO_UNIX_CFLAGS=''
GIO_UNIX_LIBS=''
GREP=''
GUSB_CFLAGS=''
GUSB_LIBS=''
INSTALL_DATA='${INSTALL} -m 644'
INSTALL_PROGRAM='${INSTALL}'
INSTALL_SCRIPT='${INSTALL}'
INSTALL_STRIP_PROGRAM='$(install_sh) -c -s'
LD=''
LDFLAGS=''
LIBNL_CFLAGS=''
LIBNL_LIBS=''
LIBOBJS=''
LIBS='-lgthread'
LIBTOOL=''
LIPO=''
LN_S=''
LTLIBOBJS=''
MAKEINFO='${SHELL} /home/tom/Downloads/infinitv-usbd-0.1.0/build-aux/missing --run makeinfo'
MANIFEST_TOOL=''
MKDIR_P='/bin/mkdir -p'
NM=''
NMEDIT=''
OBJDUMP=''
OBJEXT=''
OTOOL64=''
OTOOL=''
PACKAGE='infinitv-usbd'
PACKAGE_BUGREPORT='linux@cetoncorp.com'
PACKAGE_NAME='infinitv-usbd'
PACKAGE_STRING='infinitv-usbd 0.1.0'
PACKAGE_TARNAME='infinitv-usbd'
PACKAGE_URL=''
PACKAGE_VERSION='0.1.0'
PATH_SEPARATOR=':'
PKG_CONFIG=''
PKG_CONFIG_LIBDIR=''
PKG_CONFIG_PATH=''
RANLIB=''
SED=''
SET_MAKE=''
SHELL='/bin/bash'
STRIP=''
VERSION='0.1.0'
ac_ct_AR=''
ac_ct_CC='gcc'
ac_ct_DUMPBIN=''
am__EXEEXT_FALSE=''
am__EXEEXT_TRUE=''
am__fastdepCC_FALSE=''
am__fastdepCC_TRUE=''
am__include='include'
am__isrc=''
am__leading_dot='.'
am__quote=''
am__tar='${AMTAR} chof - "$$tardir"'
am__untar='${AMTAR} xf -'
bindir='${exec_prefix}/bin'
build='x86_64-unknown-linux-gnu'
build_alias=''
build_cpu='x86_64'
build_os='linux-gnu'
build_vendor='unknown'
datadir='${datarootdir}'
datarootdir='${prefix}/share'
docdir='${datarootdir}/doc/${PACKAGE_TARNAME}'
dvidir='${docdir}'
exec_prefix='NONE'
host='x86_64-unknown-linux-gnu'
host_alias=''
host_cpu='x86_64'
host_os='linux-gnu'
host_vendor='unknown'
htmldir='${docdir}'
includedir='${prefix}/include'
infodir='${datarootdir}/info'
install_sh='${SHELL} /home/tom/Downloads/infinitv-usbd-0.1.0/build-aux/install-sh'
libdir='${exec_prefix}/lib'
libexecdir='${exec_prefix}/libexec'
localedir='${datarootdir}/locale'
localstatedir='${prefix}/var'
mandir='${datarootdir}/man'
mkdir_p='/bin/mkdir -p'
oldincludedir='/usr/include'
pdfdir='${docdir}'
prefix='/usr'
program_transform_name='s,x,x,'
psdir='${docdir}'
sbindir='${exec_prefix}/sbin'
sharedstatedir='${prefix}/com'
sysconfdir='${prefix}/etc'
target_alias=''

## ----------- ##
## confdefs.h. ##
## ----------- ##

/* confdefs.h */
#define PACKAGE_NAME "infinitv-usbd"
#define PACKAGE_TARNAME "infinitv-usbd"
#define PACKAGE_VERSION "0.1.0"
#define PACKAGE_STRING "infinitv-usbd 0.1.0"
#define PACKAGE_BUGREPORT "linux@cetoncorp.com"
#define PACKAGE_URL ""
#define PACKAGE "infinitv-usbd"
#define VERSION "0.1.0"

configure: exit 77

```

So now what should I do?  Again, thanks for your patience and your assistance!

Wideleg84

---

### Post by blm-ubunet on 2015-11-06
Try
```
make clean
make distclean
 ./configure --prefix=/usr LIBS=-lgthread-2.0
make
```

that compiles on my 64bit PC (there are compiler warnings but no errors)

---

### Post by matt_symes on 2015-11-06
Hi

> **blm-ubunet said:**
> Try
```
make clean
make distclean
 ./configure --prefix=/usr LIBS=-lgthread-2.0
make
```

that compiles on my 64bit PC (there are compiler warnings but no errors)

You beat me to it.

I was trying to build it when you posted.

For the record, here were my steps (condensed slightly)
```

sudo apt-get install libnl-dev libgusb-dev

cd ~
mkdir temp && cd $_
wget http://cetoncorp.com/downloads/infinitv-usbd-0.1.0.tar.gz

tar xvf infinitv-usbd-0.1.0.tar.gz

cd infinitv-usbd-0.1.0

./configure --prefix=/usr LIBS=-lgthread-2.0

make

matthew-laptop:/home/matthew/temp/infinitv-usbd-0.1.0:1 % ls src 
inet_util.c  inet_util.o     infinitv_usbd.h  main.o    Makefile.am  rpc.c  rpc.o  rtp.h
inet_util.h  infinitv_usbd*  main.c           Makefile  Makefile.in  rpc.h  rtp.c  rtp.o
matthew-laptop:/home/matthew/temp/infinitv-usbd-0.1.0:1 %

matthew-laptop:/home/matthew/temp/infinitv-usbd-0.1.0:1 % file src/infinitv_usbd
src/infinitv_usbd: ELF 64-bit LSB  executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.24, BuildID[sha1]=7ce7b4809cf7f8aea64dc91f3b1f4fab68b00169, not stripped
matthew-laptop:/home/matthew/temp/infinitv-usbd-0.1.0: 
```

Might want to strip the binary if it works.

EDIT:

FYI

```
matthew-laptop:/home/matthew/temp/infinitv-usbd-0.1.0:1 % uname -pm && cat /etc/lsb-release
x86_64 x86_64
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.3 LTS"
matthew-laptop:/home/matthew/temp/infinitv-usbd-0.1.0:1 %
```

Kind regards

---

### Post by wideleg84 on 2015-11-06
The 'make clean' and 'make distclean' commands did NOT work!  However, the revised 'configure' command did seem to work OK.  When I tried the 'make' and 'make install' commands, this was the result:

```

This file contains any messages produced by compilers while
running configure, to aid debugging if configure makes a mistake.

It was created by infinitv-usbd configure 0.1.0, which was
generated by GNU Autoconf 2.68.  Invocation command line was

  $ ./configure --prefix=/usr LIBS=-lgthread-2.0

## --------- ##
## Platform. ##
## --------- ##

hostname = tom-G41D-M7
uname -m = x86_64
uname -r = 3.16.0-52-generic
uname -s = Linux
uname -v = #71~14.04.1-Ubuntu SMP Fri Oct 23 17:24:53 UTC 2015

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = unknown
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
/usr/bin/hostinfo      = unknown
/bin/machine           = unknown
/usr/bin/oslevel       = unknown
/bin/universe          = unknown

PATH: /usr/local/sbin
PATH: /usr/local/bin
PATH: /usr/sbin
PATH: /usr/bin
PATH: /sbin
PATH: /bin
PATH: /usr/games
PATH: /usr/local/games


## ----------- ##
## Core tests. ##
## ----------- ##

configure:2270: checking for a BSD-compatible install
configure:2338: result: /usr/bin/install -c
configure:2349: checking whether build environment is sane
configure:2399: result: yes
configure:2540: checking for a thread-safe mkdir -p
configure:2579: result: /bin/mkdir -p
configure:2592: checking for gawk
configure:2622: result: no
configure:2592: checking for mawk
configure:2608: found /usr/bin/mawk
configure:2619: result: mawk
configure:2630: checking whether make sets $(MAKE)
configure:2652: result: yes
configure:2778: checking build system type
configure:2792: result: x86_64-unknown-linux-gnu
configure:2812: checking host system type
configure:2825: result: x86_64-unknown-linux-gnu
configure:2866: checking how to print strings
configure:2893: result: printf
configure:2926: checking for style of include used by make
configure:2954: result: GNU
configure:3024: checking for gcc
configure:3040: found /usr/bin/gcc
configure:3051: result: gcc
configure:3280: checking for C compiler version
configure:3289: gcc --version >&5
gcc (Ubuntu 4.8.4-2ubuntu1~14.04) 4.8.4
Copyright (C) 2013 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:3300: $? = 0
configure:3289: gcc -v >&5
Using built-in specs.
COLLECT_GCC=gcc
COLLECT_LTO_WRAPPER=/usr/lib/gcc/x86_64-linux-gnu/4.8/lto-wrapper
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.8.4-2ubuntu1~14.04' --with-bugurl=file:///usr/share/doc/gcc-4.8/README.Bugs --enable-languages=c,c++,java,go,d,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.8 --enable-shared --enable-linker-build-id --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.8 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-gnu-unique-object --disable-libmudflap --enable-plugin --with-system-zlib --disable-browser-plugin --enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.5.0-gcj-4.8-amd64/jre --enable-java-home --with-jvm-root-dir=/usr/lib/jvm/java-1.5.0-gcj-4.8-amd64 --with-jvm-jar-dir=/usr/lib/jvm-exports/java-1.5.0-gcj-4.8-amd64 --with-arch-directory=amd64 --with-ecj-jar=/usr/share/java/eclipse-ecj.jar --enable-objc-gc --enable-multiarch --disable-werror --with-arch-32=i686 --with-abi=m64 --with-multilib-list=m32,m64,mx32 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.8.4 (Ubuntu 4.8.4-2ubuntu1~14.04) 
configure:3300: $? = 0
configure:3289: gcc -V >&5
gcc: error: unrecognized command line option '-V'
gcc: fatal error: no input files
compilation terminated.
configure:3300: $? = 4
configure:3289: gcc -qversion >&5
gcc: error: unrecognized command line option '-qversion'
gcc: fatal error: no input files
compilation terminated.
configure:3300: $? = 4
configure:3320: checking whether the C compiler works
configure:3342: gcc    conftest.c -lgthread-2.0 >&5
configure:3346: $? = 0
configure:3394: result: yes
configure:3397: checking for C compiler default output file name
configure:3399: result: a.out
configure:3405: checking for suffix of executables
configure:3412: gcc -o conftest    conftest.c -lgthread-2.0 >&5
configure:3416: $? = 0
configure:3438: result: 
configure:3460: checking whether we are cross compiling
configure:3468: gcc -o conftest    conftest.c -lgthread-2.0 >&5
configure:3472: $? = 0
configure:3479: ./conftest
configure:3483: $? = 0
configure:3498: result: no
configure:3503: checking for suffix of object files
configure:3525: gcc -c   conftest.c >&5
configure:3529: $? = 0
configure:3550: result: o
configure:3554: checking whether we are using the GNU C compiler
configure:3573: gcc -c   conftest.c >&5
configure:3573: $? = 0
configure:3582: result: yes
configure:3591: checking whether gcc accepts -g
configure:3611: gcc -c -g  conftest.c >&5
configure:3611: $? = 0
configure:3652: result: yes
configure:3669: checking for gcc option to accept ISO C89
configure:3733: gcc  -c -g -O2  conftest.c >&5
configure:3733: $? = 0
configure:3746: result: none needed
configure:3768: checking dependency style of gcc
configure:3878: result: gcc3
configure:3893: checking for a sed that does not truncate output
configure:3957: result: /bin/sed
configure:3975: checking for grep that handles long lines and -e
configure:4033: result: /bin/grep
configure:4038: checking for egrep
configure:4100: result: /bin/grep -E
configure:4105: checking for fgrep
configure:4167: result: /bin/grep -F
configure:4202: checking for ld used by gcc
configure:4269: result: /usr/bin/ld
configure:4276: checking if the linker (/usr/bin/ld) is GNU ld
configure:4291: result: yes
configure:4303: checking for BSD- or MS-compatible name lister (nm)
configure:4352: result: /usr/bin/nm -B
configure:4482: checking the name lister (/usr/bin/nm -B) interface
configure:4489: gcc -c -g -O2  conftest.c >&5
configure:4492: /usr/bin/nm -B "conftest.o"
configure:4495: output
0000000000000000 B some_variable
configure:4502: result: BSD nm
configure:4505: checking whether ln -s works
configure:4509: result: yes
configure:4517: checking the maximum length of command line arguments
configure:4642: result: 1572864
configure:4659: checking whether the shell understands some XSI constructs
configure:4669: result: yes
configure:4673: checking whether the shell understands "+="
configure:4679: result: yes
configure:4714: checking how to convert x86_64-unknown-linux-gnu file names to x86_64-unknown-linux-gnu format
configure:4754: result: func_convert_file_noop
configure:4761: checking how to convert x86_64-unknown-linux-gnu file names to toolchain format
configure:4781: result: func_convert_file_noop
configure:4788: checking for /usr/bin/ld option to reload object files
configure:4795: result: -r
configure:4869: checking for objdump
configure:4885: found /usr/bin/objdump
configure:4896: result: objdump
configure:4928: checking how to recognize dependent libraries
configure:5130: result: pass_all
configure:5215: checking for dlltool
configure:5245: result: no
configure:5275: checking how to associate runtime and link libraries
configure:5302: result: printf %s\n
configure:5363: checking for ar
configure:5379: found /usr/bin/ar
configure:5390: result: ar
configure:5427: checking for archiver @FILE support
configure:5444: gcc -c -g -O2  conftest.c >&5
configure:5444: $? = 0
configure:5447: ar cru libconftest.a @conftest.lst >&5
configure:5450: $? = 0
configure:5455: ar cru libconftest.a @conftest.lst >&5
ar: conftest.o: No such file or directory
configure:5458: $? = 1
configure:5470: result: @
configure:5528: checking for strip
configure:5544: found /usr/bin/strip
configure:5555: result: strip
configure:5627: checking for ranlib
configure:5643: found /usr/bin/ranlib
configure:5654: result: ranlib
configure:5756: checking command to parse /usr/bin/nm -B output from gcc object
configure:5875: gcc -c -g -O2  conftest.c >&5
configure:5878: $? = 0
configure:5882: /usr/bin/nm -B conftest.o \| sed -n -e 's/^.*[ ]\([ABCDGIRSTW][ABCDGIRSTW]*\)[ ][ ]*\([_A-Za-z][_A-Za-z0-9]*\)$/\1 \2 \2/p' | sed '/ __gnu_lto/d' \> conftest.nm
configure:5885: $? = 0
configure:5951: gcc -o conftest -g -O2   conftest.c conftstm.o >&5
configure:5954: $? = 0
configure:5992: result: ok
configure:6029: checking for sysroot
configure:6059: result: no
configure:6136: gcc -c -g -O2  conftest.c >&5
configure:6139: $? = 0
configure:6302: checking for mt
configure:6318: found /bin/mt
configure:6329: result: mt
configure:6352: checking if mt is a manifest tool
configure:6358: mt '-?'
configure:6366: result: no
configure:6998: checking how to run the C preprocessor
configure:7029: gcc -E  conftest.c
configure:7029: $? = 0
configure:7043: gcc -E  conftest.c
conftest.c:11:28: fatal error: ac_nonexistent.h: No such file or directory
 #include <ac_nonexistent.h>
                            ^
compilation terminated.
configure:7043: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "infinitv-usbd"
| #define PACKAGE_TARNAME "infinitv-usbd"
| #define PACKAGE_VERSION "0.1.0"
| #define PACKAGE_STRING "infinitv-usbd 0.1.0"
| #define PACKAGE_BUGREPORT "linux@cetoncorp.com"
| #define PACKAGE_URL ""
| #define PACKAGE "infinitv-usbd"
| #define VERSION "0.1.0"
| /* end confdefs.h.  */
| #include <ac_nonexistent.h>
configure:7068: result: gcc -E
configure:7088: gcc -E  conftest.c
configure:7088: $? = 0
configure:7102: gcc -E  conftest.c
conftest.c:11:28: fatal error: ac_nonexistent.h: No such file or directory
 #include <ac_nonexistent.h>
                            ^
compilation terminated.
configure:7102: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME "infinitv-usbd"
| #define PACKAGE_TARNAME "infinitv-usbd"
| #define PACKAGE_VERSION "0.1.0"
| #define PACKAGE_STRING "infinitv-usbd 0.1.0"
| #define PACKAGE_BUGREPORT "linux@cetoncorp.com"
| #define PACKAGE_URL ""
| #define PACKAGE "infinitv-usbd"
| #define VERSION "0.1.0"
| /* end confdefs.h.  */
| #include <ac_nonexistent.h>
configure:7131: checking for ANSI C header files
configure:7151: gcc -c -g -O2  conftest.c >&5
configure:7151: $? = 0
configure:7224: gcc -o conftest -g -O2   conftest.c -lgthread-2.0 >&5
configure:7224: $? = 0
configure:7224: ./conftest
configure:7224: $? = 0
configure:7235: result: yes
configure:7248: checking for sys/types.h
configure:7248: gcc -c -g -O2  conftest.c >&5
configure:7248: $? = 0
configure:7248: result: yes
configure:7248: checking for sys/stat.h
configure:7248: gcc -c -g -O2  conftest.c >&5
configure:7248: $? = 0
configure:7248: result: yes
configure:7248: checking for stdlib.h
configure:7248: gcc -c -g -O2  conftest.c >&5
configure:7248: $? = 0
configure:7248: result: yes
configure:7248: checking for string.h
configure:7248: gcc -c -g -O2  conftest.c >&5
configure:7248: $? = 0
configure:7248: result: yes
configure:7248: checking for memory.h
configure:7248: gcc -c -g -O2  conftest.c >&5
configure:7248: $? = 0
configure:7248: result: yes
configure:7248: checking for strings.h
configure:7248: gcc -c -g -O2  conftest.c >&5
configure:7248: $? = 0
configure:7248: result: yes
configure:7248: checking for inttypes.h
configure:7248: gcc -c -g -O2  conftest.c >&5
configure:7248: $? = 0
configure:7248: result: yes
configure:7248: checking for stdint.h
configure:7248: gcc -c -g -O2  conftest.c >&5
configure:7248: $? = 0
configure:7248: result: yes
configure:7248: checking for unistd.h
configure:7248: gcc -c -g -O2  conftest.c >&5
configure:7248: $? = 0
configure:7248: result: yes
configure:7262: checking for dlfcn.h
configure:7262: gcc -c -g -O2  conftest.c >&5
configure:7262: $? = 0
configure:7262: result: yes
configure:7449: checking for objdir
configure:7464: result: .libs
configure:7735: checking if gcc supports -fno-rtti -fno-exceptions
configure:7753: gcc -c -g -O2  -fno-rtti -fno-exceptions conftest.c >&5
cc1: warning: command line option '-fno-rtti' is valid for C++/ObjC++ but not for C [enabled by default]
configure:7757: $? = 0
configure:7770: result: no
configure:8080: checking for gcc option to produce PIC
configure:8087: result: -fPIC -DPIC
configure:8095: checking if gcc PIC flag -fPIC -DPIC works
configure:8113: gcc -c -g -O2  -fPIC -DPIC -DPIC conftest.c >&5
configure:8117: $? = 0
configure:8130: result: yes
configure:8159: checking if gcc static flag -static works
configure:8187: result: yes
configure:8202: checking if gcc supports -c -o file.o
configure:8223: gcc -c -g -O2  -o out/conftest2.o conftest.c >&5
configure:8227: $? = 0
configure:8249: result: yes
configure:8257: checking if gcc supports -c -o file.o
configure:8304: result: yes
configure:8337: checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries
configure:9495: result: yes
configure:9532: checking whether -lc should be explicitly linked in
configure:9540: gcc -c -g -O2  conftest.c >&5
configure:9543: $? = 0
configure:9558: gcc -shared  -fPIC -DPIC conftest.o  -v -Wl,-soname -Wl,conftest -o conftest 2\>\&1 \| /bin/grep  -lc  \>/dev/null 2\>\&1
configure:9561: $? = 0
configure:9575: result: no
configure:9740: checking dynamic linker characteristics
configure:10254: gcc -o conftest -g -O2   -Wl,-rpath -Wl,/foo conftest.c -lgthread-2.0 >&5
configure:10254: $? = 0
configure:10480: result: GNU/Linux ld.so
configure:10587: checking how to hardcode library paths into programs
configure:10612: result: immediate
configure:11152: checking whether stripping libraries is possible
configure:11157: result: yes
configure:11192: checking if libtool supports shared libraries
configure:11194: result: yes
configure:11197: checking whether to build shared libraries
configure:11218: result: yes
configure:11221: checking whether to build static libraries
configure:11225: result: yes
configure:11309: checking for gcc
configure:11336: result: gcc
configure:11565: checking for C compiler version
configure:11574: gcc --version >&5
gcc (Ubuntu 4.8.4-2ubuntu1~14.04) 4.8.4
Copyright (C) 2013 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:11585: $? = 0
configure:11574: gcc -v >&5
Using built-in specs.
COLLECT_GCC=gcc
COLLECT_LTO_WRAPPER=/usr/lib/gcc/x86_64-linux-gnu/4.8/lto-wrapper
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.8.4-2ubuntu1~14.04' --with-bugurl=file:///usr/share/doc/gcc-4.8/README.Bugs --enable-languages=c,c++,java,go,d,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.8 --enable-shared --enable-linker-build-id --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.8 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-gnu-unique-object --disable-libmudflap --enable-plugin --with-system-zlib --disable-browser-plugin --enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.5.0-gcj-4.8-amd64/jre --enable-java-home --with-jvm-root-dir=/usr/lib/jvm/java-1.5.0-gcj-4.8-amd64 --with-jvm-jar-dir=/usr/lib/jvm-exports/java-1.5.0-gcj-4.8-amd64 --with-arch-directory=amd64 --with-ecj-jar=/usr/share/java/eclipse-ecj.jar --enable-objc-gc --enable-multiarch --disable-werror --with-arch-32=i686 --with-abi=m64 --with-multilib-list=m32,m64,mx32 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.8.4 (Ubuntu 4.8.4-2ubuntu1~14.04) 
configure:11585: $? = 0
configure:11574: gcc -V >&5
gcc: error: unrecognized command line option '-V'
gcc: fatal error: no input files
compilation terminated.
configure:11585: $? = 4
configure:11574: gcc -qversion >&5
gcc: error: unrecognized command line option '-qversion'
gcc: fatal error: no input files
compilation terminated.
configure:11585: $? = 4
configure:11589: checking whether we are using the GNU C compiler
configure:11617: result: yes
configure:11626: checking whether gcc accepts -g
configure:11687: result: yes
configure:11704: checking for gcc option to accept ISO C89
configure:11781: result: none needed
configure:11803: checking dependency style of gcc
configure:11913: result: gcc3
configure:11982: checking for pkg-config
configure:12000: found /usr/bin/pkg-config
configure:12012: result: /usr/bin/pkg-config
configure:12037: checking pkg-config is at least version 0.9.0
configure:12040: result: yes
configure:12050: checking for GIO
configure:12057: $PKG_CONFIG --exists --print-errors "gio-2.0"
configure:12060: $? = 0
configure:12073: $PKG_CONFIG --exists --print-errors "gio-2.0"
configure:12076: $? = 0
configure:12135: result: yes
configure:12141: checking for GIO_UNIX
configure:12148: $PKG_CONFIG --exists --print-errors "gio-unix-2.0"
configure:12151: $? = 0
configure:12164: $PKG_CONFIG --exists --print-errors "gio-unix-2.0"
configure:12167: $? = 0
configure:12226: result: yes
configure:12232: checking for LIBNL
configure:12239: $PKG_CONFIG --exists --print-errors "libnl-1"
configure:12242: $? = 0
configure:12255: $PKG_CONFIG --exists --print-errors "libnl-1"
configure:12258: $? = 0
configure:12317: result: yes
configure:12323: checking for GUSB
configure:12330: $PKG_CONFIG --exists --print-errors "gusb"
configure:12333: $? = 0
configure:12346: $PKG_CONFIG --exists --print-errors "gusb"
configure:12349: $? = 0
configure:12408: result: yes
configure:12415: checking for stdlib.h
configure:12415: result: yes
configure:12560: creating ./config.status

## ---------------------- ##
## Running config.status. ##
## ---------------------- ##

This file was extended by infinitv-usbd config.status 0.1.0, which was
generated by GNU Autoconf 2.68.  Invocation command line was

  CONFIG_FILES    = 
  CONFIG_HEADERS  = 
  CONFIG_LINKS    = 
  CONFIG_COMMANDS = 
  $ ./config.status 

on tom-G41D-M7

config.status:1102: creating Makefile
config.status:1102: creating src/Makefile
config.status:1102: creating config.h
config.status:1331: executing depfiles commands
config.status:1331: executing libtool commands

## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_build=x86_64-unknown-linux-gnu
ac_cv_c_compiler_gnu=yes
ac_cv_env_CC_set=
ac_cv_env_CC_value=
ac_cv_env_CFLAGS_set=
ac_cv_env_CFLAGS_value=
ac_cv_env_CPPFLAGS_set=
ac_cv_env_CPPFLAGS_value=
ac_cv_env_CPP_set=
ac_cv_env_CPP_value=
ac_cv_env_GIO_CFLAGS_set=
ac_cv_env_GIO_CFLAGS_value=
ac_cv_env_GIO_LIBS_set=
ac_cv_env_GIO_LIBS_value=
ac_cv_env_GIO_UNIX_CFLAGS_set=
ac_cv_env_GIO_UNIX_CFLAGS_value=
ac_cv_env_GIO_UNIX_LIBS_set=
ac_cv_env_GIO_UNIX_LIBS_value=
ac_cv_env_GUSB_CFLAGS_set=
ac_cv_env_GUSB_CFLAGS_value=
ac_cv_env_GUSB_LIBS_set=
ac_cv_env_GUSB_LIBS_value=
ac_cv_env_LDFLAGS_set=
ac_cv_env_LDFLAGS_value=
ac_cv_env_LIBNL_CFLAGS_set=
ac_cv_env_LIBNL_CFLAGS_value=
ac_cv_env_LIBNL_LIBS_set=
ac_cv_env_LIBNL_LIBS_value=
ac_cv_env_LIBS_set=set
ac_cv_env_LIBS_value=-lgthread-2.0
ac_cv_env_PKG_CONFIG_LIBDIR_set=
ac_cv_env_PKG_CONFIG_LIBDIR_value=
ac_cv_env_PKG_CONFIG_PATH_set=
ac_cv_env_PKG_CONFIG_PATH_value=
ac_cv_env_PKG_CONFIG_set=
ac_cv_env_PKG_CONFIG_value=
ac_cv_env_build_alias_set=
ac_cv_env_build_alias_value=
ac_cv_env_host_alias_set=
ac_cv_env_host_alias_value=
ac_cv_env_target_alias_set=
ac_cv_env_target_alias_value=
ac_cv_header_dlfcn_h=yes
ac_cv_header_inttypes_h=yes
ac_cv_header_memory_h=yes
ac_cv_header_stdc=yes
ac_cv_header_stdint_h=yes
ac_cv_header_stdlib_h=yes
ac_cv_header_string_h=yes
ac_cv_header_strings_h=yes
ac_cv_header_sys_stat_h=yes
ac_cv_header_sys_types_h=yes
ac_cv_header_unistd_h=yes
ac_cv_host=x86_64-unknown-linux-gnu
ac_cv_objext=o
ac_cv_path_EGREP='/bin/grep -E'
ac_cv_path_FGREP='/bin/grep -F'
ac_cv_path_GREP=/bin/grep
ac_cv_path_SED=/bin/sed
ac_cv_path_ac_pt_PKG_CONFIG=/usr/bin/pkg-config
ac_cv_path_install='/usr/bin/install -c'
ac_cv_path_mkdir=/bin/mkdir
ac_cv_prog_AWK=mawk
ac_cv_prog_CPP='gcc -E'
ac_cv_prog_ac_ct_AR=ar
ac_cv_prog_ac_ct_CC=gcc
ac_cv_prog_ac_ct_MANIFEST_TOOL=mt
ac_cv_prog_ac_ct_OBJDUMP=objdump
ac_cv_prog_ac_ct_RANLIB=ranlib
ac_cv_prog_ac_ct_STRIP=strip
ac_cv_prog_cc_c89=
ac_cv_prog_cc_g=yes
ac_cv_prog_make_make_set=yes
am_cv_CC_dependencies_compiler_type=gcc3
lt_cv_ar_at_file=@
lt_cv_archive_cmds_need_lc=no
lt_cv_deplibs_check_method=pass_all
lt_cv_file_magic_cmd='$MAGIC_CMD'
lt_cv_file_magic_test_file=
lt_cv_ld_reload_flag=-r
lt_cv_nm_interface='BSD nm'
lt_cv_objdir=.libs
lt_cv_path_LD=/usr/bin/ld
lt_cv_path_NM='/usr/bin/nm -B'
lt_cv_path_mainfest_tool=no
lt_cv_prog_compiler_c_o=yes
lt_cv_prog_compiler_pic='-fPIC -DPIC'
lt_cv_prog_compiler_pic_works=yes
lt_cv_prog_compiler_rtti_exceptions=no
lt_cv_prog_compiler_static_works=yes
lt_cv_prog_gnu_ld=yes
lt_cv_sharedlib_from_linklib_cmd='printf %s\n'
lt_cv_shlibpath_overrides_runpath=no
lt_cv_sys_global_symbol_pipe='sed -n -e '\''s/^.*[     ]\([ABCDGIRSTW][ABCDGIRSTW]*\)[     ][     ]*\([_A-Za-z][_A-Za-z0-9]*\)$/\1 \2 \2/p'\'' | sed '\''/ __gnu_lto/d'\'''
lt_cv_sys_global_symbol_to_c_name_address='sed -n -e '\''s/^: \([^ ]*\)[ ]*$/  {\"\1\", (void *) 0},/p'\'' -e '\''s/^[ABCDGIRSTW]* \([^ ]*\) \([^ ]*\)$/  {"\2", (void *) \&\2},/p'\'''
lt_cv_sys_global_symbol_to_c_name_address_lib_prefix='sed -n -e '\''s/^: \([^ ]*\)[ ]*$/  {\"\1\", (void *) 0},/p'\'' -e '\''s/^[ABCDGIRSTW]* \([^ ]*\) \(lib[^ ]*\)$/  {"\2", (void *) \&\2},/p'\'' -e '\''s/^[ABCDGIRSTW]* \([^ ]*\) \([^ ]*\)$/  {"lib\2", (void *) \&\2},/p'\'''
lt_cv_sys_global_symbol_to_cdecl='sed -n -e '\''s/^T .* \(.*\)$/extern int \1();/p'\'' -e '\''s/^[ABCDGIRSTW]* .* \(.*\)$/extern char \1;/p'\'''
lt_cv_sys_max_cmd_len=1572864
lt_cv_to_host_file_cmd=func_convert_file_noop
lt_cv_to_tool_file_cmd=func_convert_file_noop
pkg_cv_GIO_CFLAGS='-pthread -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include  '
pkg_cv_GIO_LIBS='-lgio-2.0 -lgobject-2.0 -lglib-2.0  '
pkg_cv_GIO_UNIX_CFLAGS='-pthread -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include  '
pkg_cv_GIO_UNIX_LIBS='-lgio-2.0 -lgobject-2.0 -lglib-2.0  '
pkg_cv_GUSB_CFLAGS='-pthread -I/usr/include/gusb-1 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/libusb-1.0  '
pkg_cv_GUSB_LIBS='-lgusb -lgobject-2.0 -lusb-1.0 -lglib-2.0  '
pkg_cv_LIBNL_CFLAGS=' '
pkg_cv_LIBNL_LIBS='-lnl  '

## ----------------- ##
## Output variables. ##
## ----------------- ##

ACLOCAL='${SHELL} /home/tom/Downloads/infinitv-usbd-0.1.0/build-aux/missing --run aclocal-1.11'
AMDEPBACKSLASH='\'
AMDEP_FALSE='#'
AMDEP_TRUE=''
AMTAR='${SHELL} /home/tom/Downloads/infinitv-usbd-0.1.0/build-aux/missing --run tar'
AM_BACKSLASH='\'
AM_DEFAULT_VERBOSITY='0'
AR='ar'
AUTOCONF='${SHELL} /home/tom/Downloads/infinitv-usbd-0.1.0/build-aux/missing --run autoconf'
AUTOHEADER='${SHELL} /home/tom/Downloads/infinitv-usbd-0.1.0/build-aux/missing --run autoheader'
AUTOMAKE='${SHELL} /home/tom/Downloads/infinitv-usbd-0.1.0/build-aux/missing --run automake-1.11'
AWK='mawk'
CC='gcc'
CCDEPMODE='depmode=gcc3'
CFLAGS='-g -O2'
CPP='gcc -E'
CPPFLAGS=''
CYGPATH_W='echo'
DEFS='-DHAVE_CONFIG_H'
DEPDIR='.deps'
DLLTOOL='false'
DSYMUTIL=''
DUMPBIN=''
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EGREP='/bin/grep -E'
EXEEXT=''
FGREP='/bin/grep -F'
GIO_CFLAGS='-pthread -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include  '
GIO_LIBS='-lgio-2.0 -lgobject-2.0 -lglib-2.0  '
GIO_UNIX_CFLAGS='-pthread -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include  '
GIO_UNIX_LIBS='-lgio-2.0 -lgobject-2.0 -lglib-2.0  '
GREP='/bin/grep'
GUSB_CFLAGS='-pthread -I/usr/include/gusb-1 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/libusb-1.0  '
GUSB_LIBS='-lgusb -lgobject-2.0 -lusb-1.0 -lglib-2.0  '
INSTALL_DATA='${INSTALL} -m 644'
INSTALL_PROGRAM='${INSTALL}'
INSTALL_SCRIPT='${INSTALL}'
INSTALL_STRIP_PROGRAM='$(install_sh) -c -s'
LD='/usr/bin/ld -m elf_x86_64'
LDFLAGS=''
LIBNL_CFLAGS=' '
LIBNL_LIBS='-lnl  '
LIBOBJS=''
LIBS='-lgthread-2.0'
LIBTOOL='$(SHELL) $(top_builddir)/libtool'
LIPO=''
LN_S='ln -s'
LTLIBOBJS=''
MAKEINFO='${SHELL} /home/tom/Downloads/infinitv-usbd-0.1.0/build-aux/missing --run makeinfo'
MANIFEST_TOOL=':'
MKDIR_P='/bin/mkdir -p'
NM='/usr/bin/nm -B'
NMEDIT=''
OBJDUMP='objdump'
OBJEXT='o'
OTOOL64=''
OTOOL=''
PACKAGE='infinitv-usbd'
PACKAGE_BUGREPORT='linux@cetoncorp.com'
PACKAGE_NAME='infinitv-usbd'
PACKAGE_STRING='infinitv-usbd 0.1.0'
PACKAGE_TARNAME='infinitv-usbd'
PACKAGE_URL=''
PACKAGE_VERSION='0.1.0'
PATH_SEPARATOR=':'
PKG_CONFIG='/usr/bin/pkg-config'
PKG_CONFIG_LIBDIR=''
PKG_CONFIG_PATH=''
RANLIB='ranlib'
SED='/bin/sed'
SET_MAKE=''
SHELL='/bin/bash'
STRIP='strip'
VERSION='0.1.0'
ac_ct_AR='ar'
ac_ct_CC='gcc'
ac_ct_DUMPBIN=''
am__EXEEXT_FALSE=''
am__EXEEXT_TRUE='#'
am__fastdepCC_FALSE='#'
am__fastdepCC_TRUE=''
am__include='include'
am__isrc=''
am__leading_dot='.'
am__quote=''
am__tar='${AMTAR} chof - "$$tardir"'
am__untar='${AMTAR} xf -'
bindir='${exec_prefix}/bin'
build='x86_64-unknown-linux-gnu'
build_alias=''
build_cpu='x86_64'
build_os='linux-gnu'
build_vendor='unknown'
datadir='${datarootdir}'
datarootdir='${prefix}/share'
docdir='${datarootdir}/doc/${PACKAGE_TARNAME}'
dvidir='${docdir}'
exec_prefix='${prefix}'
host='x86_64-unknown-linux-gnu'
host_alias=''
host_cpu='x86_64'
host_os='linux-gnu'
host_vendor='unknown'
htmldir='${docdir}'
includedir='${prefix}/include'
infodir='${datarootdir}/info'
install_sh='${SHELL} /home/tom/Downloads/infinitv-usbd-0.1.0/build-aux/install-sh'
libdir='${exec_prefix}/lib'
libexecdir='${exec_prefix}/libexec'
localedir='${datarootdir}/locale'
localstatedir='${prefix}/var'
mandir='${datarootdir}/man'
mkdir_p='/bin/mkdir -p'
oldincludedir='/usr/include'
pdfdir='${docdir}'
prefix='/usr'
program_transform_name='s,x,x,'
psdir='${docdir}'
sbindir='${exec_prefix}/sbin'
sharedstatedir='${prefix}/com'
sysconfdir='${prefix}/etc'
target_alias=''

## ----------- ##
## confdefs.h. ##
## ----------- ##

/* confdefs.h */
#define PACKAGE_NAME "infinitv-usbd"
#define PACKAGE_TARNAME "infinitv-usbd"
#define PACKAGE_VERSION "0.1.0"
#define PACKAGE_STRING "infinitv-usbd 0.1.0"
#define PACKAGE_BUGREPORT "linux@cetoncorp.com"
#define PACKAGE_URL ""
#define PACKAGE "infinitv-usbd"
#define VERSION "0.1.0"
#define STDC_HEADERS 1
#define HAVE_SYS_TYPES_H 1
#define HAVE_SYS_STAT_H 1
#define HAVE_STDLIB_H 1
#define HAVE_STRING_H 1
#define HAVE_MEMORY_H 1
#define HAVE_STRINGS_H 1
#define HAVE_INTTYPES_H 1
#define HAVE_STDINT_H 1
#define HAVE_UNISTD_H 1
#define HAVE_DLFCN_H 1
#define LT_OBJDIR ".libs/"
#define HAVE_STDLIB_H 1

configure: exit 0

```

Now what?

Wideleg84

---

### Post by blm-ubunet on 2015-11-07
Can you post the "stdout" from the make command only..
(stdout is just the text output in terminal)
Use mouse highlight & then <ctrl>+<shift>+<c>

<ctrl>+<v> in the browser or anywhere except terminal.

You don't have to run "./configure blah"  .. again unless you run "make distclean" or alter your library paths etc.

"make clean" removes object code
"make distclean" removes the makefiles & object code etc

---

### Post by wideleg84 on 2015-11-07
Here is the output you requested:

```

tom@tom-G41D-M7:~$ cd Downloads
tom@tom-G41D-M7:~/Downloads$ cd infinitv-usbd-0.1.0
tom@tom-G41D-M7:~/Downloads/infinitv-usbd-0.1.0$ make
make  all-recursive
make[1]: Entering directory `/home/tom/Downloads/infinitv-usbd-0.1.0'
Making all in src
make[2]: Entering directory `/home/tom/Downloads/infinitv-usbd-0.1.0/src'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/tom/Downloads/infinitv-usbd-0.1.0/src'
make[2]: Entering directory `/home/tom/Downloads/infinitv-usbd-0.1.0'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/tom/Downloads/infinitv-usbd-0.1.0'
make[1]: Leaving directory `/home/tom/Downloads/infinitv-usbd-0.1.0'
tom@tom-G41D-M7:~/Downloads/infinitv-usbd-0.1.0$ sudo make install
[sudo] password for tom: 
Making install in src
make[1]: Entering directory `/home/tom/Downloads/infinitv-usbd-0.1.0/src'
make[2]: Entering directory `/home/tom/Downloads/infinitv-usbd-0.1.0/src'
test -z "/usr/bin" || /bin/mkdir -p "/usr/bin"
  /bin/bash ../libtool   --mode=install /usr/bin/install -c infinitv_usbd '/usr/bin'
libtool: install: /usr/bin/install -c infinitv_usbd /usr/bin/infinitv_usbd
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/tom/Downloads/infinitv-usbd-0.1.0/src'
make[1]: Leaving directory `/home/tom/Downloads/infinitv-usbd-0.1.0/src'
make[1]: Entering directory `/home/tom/Downloads/infinitv-usbd-0.1.0'
make[2]: Entering directory `/home/tom/Downloads/infinitv-usbd-0.1.0'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/tom/Downloads/infinitv-usbd-0.1.0'
make[1]: Leaving directory `/home/tom/Downloads/infinitv-usbd-0.1.0'
tom@tom-G41D-M7:~/Downloads/infinitv-usbd-0.1.0$ 


```

Wideleg84

---

### Post by blm-ubunet on 2015-11-07
Success then!
Try Matt's test if you have doubts..
```
file src/infinitv_usbd
```

I would unplug the USB stick & reboot the PC.
Plug the stick in and then run
```
dmesg
```
looking for stuff about usb, Ceton, cablecard, firmware loaded etc..

You did download the firmware from Ceton website & copy it into the right place ??

Good instructions here
[https://www.mythtv.org/wiki/Ceton_InfiniTV_4](https://www.mythtv.org/wiki/Ceton_InfiniTV_4)

---

### Post by wideleg84 on 2015-11-07
I have the image file for the firmware, but I have no idea how to install the dumb thing!  Also, in the backend setup, although the program promptly began fetching listings from Schedules Direct, when I attempted to connect the video source to the input, I got an error message saying, "Failed to open the card."  Advice, please?  (BTW, the driver appears to have installed perfectly--at LONG last!)

Wideleg84

---

### Post by blm-ubunet on 2015-11-08
The Ceton download webpage states there are instructions contained in each archive, so read them!

The questions & web-link in post #19 still apply.
There is no point trying to debug the tuner driver/firmware loading using MythTV.

---

### Post by wideleg84 on 2015-11-08
I'm sorry if I said something to upset you.  I am deeply grateful for your assistance!  As it turned out, the IP number assigned to the tuner my my system was a little bit off.  On a hunch, I tried decrementing that number by one digit--and the tuner began to work!  I have not yet tried uploading the firmware to that address, but I intend to do so later this evening.  I'll let you know the results.  Thanks again for your help!

Wideleg84

UPDATE:  When I did attempt to upload the firmware to the tuner, the browser reported an interruption in the network  Should I try using the Python script to reset the network, or what?

---

### Post by blm-ubunet on 2015-11-10
The firmware uploading is probably just a distraction. I thought it was more critical to initial operation.

I wouldn't be surprised if the DHCP server/IP allocation has some part to play.
I would just use static IPs for all mythtv BEs & the tuner stick/card.
The wiki states you need to use the python script to reset/restart the network after fiddling with IP numbers etc.

The MythTV wiki & then Ron Frasier's web resource is the best & only advice I have.

Note: AFAIK These devices create a network interface across USB, there will be an IP address for **each end** of this connection & not (1) IP address, by default the ceton device acts as DHCP for this link.

---

### Post by wpcprez on 2015-11-22
I just finished an install but with the pcie ceton infinitv4 and the drivers compiled with no issues on a fresh 14.04 mythbuntu.

---

