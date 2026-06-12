---
title: "Ntop install problems"
date: 2012-09-06
forum: Networking &amp; Wireless
---

### Post by mon deja vu on 2012-09-06
Hey, mates, that's what I'm doing.
```

cd /tmp
mkdir ntop
cd ntop
svn co [https://svn.ntop.org/svn/ntop/trunk/ntop/](https://svn.ntop.org/svn/ntop/trunk/ntop/)
cd ntop
./autogen.sh
``````

checking for gdbm_open in -lgdbm... yes

Plugins?
    ...(Default) Requested. Disable via ./configure command line option --disable-plugins.

Jumbo (9k) Ethernet Frames?
    ...(Default) Disabled. Request via ./configure command line option --enable-jumbo-frames.

Processing the rest of the ROOT/DIRECTORY entries

checking for an ANSI C-conforming const... yes
checking for working volatile... yes
checking for inline... inline
checking whether char is unsigned... no
checking for long double with more range or precision than double... yes
checking whether byte ordering is bigendian... no

Testing headers and functions...

checking for ANSI C header files... (cached) yes
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking for sys/wait.h that is POSIX.1 compatible... yes
checking whether time.h and sys/time.h may both be included... yes
checking float.h usability... yes
checking float.h presence... yes
checking for float.h... yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking pcre.h usability... yes
checking pcre.h presence... yes
checking for pcre.h... yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking math.h usability... yes
checking math.h presence... yes
checking for math.h... yes
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking stdarg.h usability... yes
checking stdarg.h presence... yes
checking for stdarg.h... yes
checking for unistd.h... (cached) yes
checking stdio.h usability... yes
checking stdio.h presence... yes
checking for stdio.h... yes
checking for strings.h... (cached) yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for sys/types.h... (cached) yes
checking setjmp.h usability... yes
checking setjmp.h presence... yes
checking for setjmp.h... yes
checking ieeefp.h usability... no
checking ieeefp.h presence... no
checking for ieeefp.h... no
checking shadow.h usability... yes
checking shadow.h presence... yes
checking for shadow.h... yes
checking sys/utsname.h usability... yes
checking sys/utsname.h presence... yes
checking for sys/utsname.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking arpa/nameser.h usability... yes
checking arpa/nameser.h presence... yes
checking for arpa/nameser.h... yes
checking net/ethernet.h usability... yes
checking net/ethernet.h presence... yes
checking for net/ethernet.h... yes
checking for zlibVersion in -lz... yes
checking for main in -lrrd_th... yes
checking for net/if.h... yes
checking net/if_dl.h usability... no
checking net/if_dl.h presence... no
checking for net/if_dl.h... no
checking for netinet/if_ether.h... yes
checking netinet/in_systm.h usability... yes
checking netinet/in_systm.h presence... yes
checking for netinet/in_systm.h... yes
checking for netinet/ip.h... yes
checking for netinet/ip_icmp.h... yes
checking netinet/tcp.h usability... yes
checking netinet/tcp.h presence... yes
checking for netinet/tcp.h... yes
checking for netinet/udp.h... yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking for net/if_dl.h... (cached) no
checking for sys/sysctl.h... yes
checking for net/route.h... yes
checking ethertype.h usability... no
checking ethertype.h presence... no
checking for ethertype.h... no
checking net/ppp_defs.h usability... yes
checking net/ppp_defs.h presence... yes
checking for net/ppp_defs.h... yes
checking for linux/if_pppox.h... no
checking openssl/rsa.h usability... yes
checking openssl/rsa.h presence... yes
checking for openssl/rsa.h... yes
checking openssl/crypto.h usability... yes
checking openssl/crypto.h presence... yes
checking for openssl/crypto.h... yes
checking openssl/x509.h usability... yes
checking openssl/x509.h presence... yes
checking for openssl/x509.h... yes
checking openssl/pem.h usability... yes
checking openssl/pem.h presence... yes
checking for openssl/pem.h... yes
checking openssl/ssl.h usability... yes
checking openssl/ssl.h presence... yes
checking for openssl/ssl.h... yes
checking openssl/err.h usability... yes
checking openssl/err.h presence... yes
checking for openssl/err.h... yes
checking for SSLeay_version in -lcrypto... yes
checking for SSL_accept in -lssl... yes
checking crypt.h usability... yes
checking crypt.h presence... yes
checking for crypt.h... yes
checking pwd.h usability... yes
checking pwd.h presence... yes
checking for pwd.h... yes
checking security/pam_appl.h usability... no
checking security/pam_appl.h presence... no
checking for security/pam_appl.h... no
checking for shadow.h... (cached) yes
checking dirent.h usability... yes
checking dirent.h presence... yes
checking for dirent.h... yes
checking for dlfcn.h... (cached) yes
checking dl.h usability... no
checking dl.h presence... no
checking for dl.h... no
checking getopt.h usability... yes
checking getopt.h presence... yes
checking for getopt.h... yes
checking if.h usability... no
checking if.h presence... no
checking for if.h... no
checking for inttypes.h... (cached) yes
checking for memory.h... (cached) yes
checking sys/ldr.h usability... no
checking sys/ldr.h presence... no
checking for sys/ldr.h... no
checking for sys/param.h... (cached) yes
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking sys/sockio.h usability... no
checking sys/sockio.h presence... no
checking for sys/sockio.h... no
checking for sys/stat.h... (cached) yes
checking sys/un.h usability... yes
checking sys/un.h presence... yes
checking for sys/un.h... yes
checking for sys/wait.h... (cached) yes
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking sched.h usability... yes
checking sched.h presence... yes
checking for sched.h... yes
checking sys/sched.h usability... no
checking sys/sched.h presence... no
checking for sys/sched.h... no
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking if r/w locks are supported... yes
checking sys/syslog.h usability... yes
checking sys/syslog.h presence... yes
checking for sys/syslog.h... yes
checking syslog.h usability... yes
checking syslog.h presence... yes
checking for syslog.h... yes
checking ip6.h usability... no
checking ip6.h presence... no
checking for ip6.h... no
checking icmp6.h usability... no
checking icmp6.h presence... no
checking for icmp6.h... no
checking for netinet/ip6.h... yes
checking for netinet/icmp6.h... yes
checking for sysctl... yes
checking for finite... yes
checking for isinf... yes
checking for pid_t... yes
checking for size_t... yes
checking whether time.h and sys/time.h may both be included... (cached) yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for struct tm.tm_zone... yes
checking for typedef u_int64_t... yes
checking for typedef uint64_t... no
checking for typedef u_int32_t... yes
checking for typedef uint32_t... no
checking for typedef u_int16_t... yes
checking for typedef uint16_t... no
checking for typedef u_int8_t... yes
checking for typedef uint8_t... no
checking for typedef int64_t... yes
checking for typedef int32_t... yes
checking for typedef int16_t... yes
checking for typedef int8_t... yes
checking trivial compile... ok
checking for backtrace in -lc... yes
checking for crypt in -lc... no
checking for crypt in -lcrypt... yes
checking for getopt_long in -lc... yes
checking for dlopen in -lc... no
checking for dlopen in -ldl... yes
checking for dladdr (GNU extension)... yes
checking for sin in -lc... no
checking for sin in -lm... yes
checking for ceil in -lc... yes
checking for pthread_create in -lpthread... yes
checking for sem_init in -lposix4... no
checking vfork.h usability... no
checking vfork.h presence... no
checking for vfork.h... no
checking for fork... yes
checking for vfork... yes
checking for working fork... yes
checking for working vfork... (cached) yes
checking whether gcc needs -traditional... no
checking for working memcmp... yes
checking return type of signal handlers... void
checking whether lstat correctly handles trailing slash... yes
checking whether stat accepts an empty string... no
checking for strftime... yes
checking for alarm... yes
checking for endpwent... yes
checking for gethostbyaddr... yes
checking for gethostbyname... yes
checking for gethostname... yes
checking for gethostbyaddr_r... yes
checking for getpass... yes
checking for gettimeofday... yes
checking for localtime_r... yes
checking for memchr... yes
checking for memset... yes
checking for putenv... yes
checking for select... yes
checking for socket... yes
checking for snprintf... yes
checking for sqrtf... yes
checking for strcasecmp... yes
checking for strncasecmp... yes
checking for strcasestr... yes
checking for strchr... yes
checking for strrchr... yes
checking for strcspn... yes
checking for strdup... yes
checking for strerror... yes
checking for strpbrk... yes
checking for strsignal... yes
checking for strspn... yes
checking for strstr... yes
checking for strtoul... yes
checking for uname... yes
checking for strtok_r... yes

Now, let's check for problems with what we've found...

   Testing Required libraries and headers**

checking for required C headers... ok
checking for crypt... ok
checking for dynamic load module... ok

-------------------------------------------------------------------

   **Testing Optional libraries and headers**

checking for Multithreading... ok
checking for openSSL... ok
checking for zlib... ok
checking for python-config... python-config
checking Checking python version... Python 2.6 or newer is available
checking pthread_atfork... yes
checking for pfring_open in -lpfring... no

Miscelaneous settings...

checking for gcc backtrace... found - automatic SIGSEGV backtrace enabled via -K
checking for gcc getopt_long... found - long command line options are enabled
checking for facilitynames - define SYSLOG_NAMES option... available
checking if ether_header uses ether_addr structs... no
checking if in6_addr is defined for sFlowPlugin... yes

-------------------------------------------------------------------

Removing dups and misplaced entries from LIBS and INCS...
checking for GeoIP_record_by_ipnum in -lGeoIP... yes
checking for GeoIP_name_by_ipnum_v6 in -lGeoIP... yes
GeoLiteCity.dat already present
GeoIPASNum.dat already present
checking for redisCommand in -lhiredis... no

Testing for special final configuration options for LINUX Ubuntu 12.04.1

===================================================================

This is your ntop 5.0.2 configuration:

Host System Type        : i686-pc-linux-gnu
Preprocessor (cppflags) :  -DLINUX -I/usr/local/include -I/opt/local/include
Compiler (cflags)       : gcc -g -O2 -I/usr/local/include -I/opt/local/include -Wshadow -Wpointer-arith -Wmissing-prototypes -Wmissing-declarations -Wnested-externs  -fPIC -DPIC  -I/usr/include/python2.7 -I/usr/include/python2.7 -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -g -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -Werror=format-security
Defines                 : -DHAVE_CONFIG_H
Loader (ldflags)        :  -L/usr/local/lib -L/opt/local/lib
Include path            : -I/usr/include/python2.7 -fno-strict-aliasing -DNDEBUG -fwrapv -O2 -Wall -Wstrict-prototypes -g -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -Werror=format-security 
System Libs             : -lcrypt -lc -lssl -lcrypto -lrrd_th -lpcap -lgdbm -lz -lpthread -ldl -lutil -lm -lpython2.7  -lGeoIP
Locale                  : /usr/lib/locale

External packages:

LBL pcap .h             : standard system headers
LBL pcap library        : standard system libraries
GNU gdbm .h             : standard system headers
GNU gdbm library        : standard system libraries
zlib     .h             : standard system headers
zlib     library        : standard system libraries
openSSL  .h             : standard system headers
openSSL  library        : standard system libraries

Install directories:

    Default prefix: /usr/local
    Install into:   NONE (default or via --prefix request)

    Data files are in     /usr/local/share/ntop
    Config files are in   /usr/local/etc/ntop
    Run directory is      /usr/local/var/ntop
    Plugin files are in   /usr/local/lib/ntop/plugins
    Database files are in /usr/local/var/ntop

-------------------------------------------------------------------

Creating files...

configure: creating ./config.status

version.c...


===================================================================


*******************************************************************
*
* NOTE: ./configure is now complete!
*
*       All of the obviously FATAL errors would cause you to
*       abort before this point, so while you SHOULD scroll
*       back and check for error/warning/note messages,
*       you probably will not...
*
++
++    If you like ntop, please do not forget to support its
++    development. See SUPPORT_NTOP.txt for more information.
++
++              Thanks for supporting ntop!
++
*
* NEXT STEP(S):
*
*    Building ntop requires GNU Make, so to build ntop, type
*    'make' (or on *BSD and Solaris systems, 'gmake')
*
*******************************************************************

        .... autogen.sh done
just type make to compile ntop

9. Downloading nDPI...
nDPI already available
./autogen.sh: 448: ./autogen.sh: cannot create nDPI: Is a directory
./autogen.sh: 448: ./autogen.sh: dnl: not found
10. Compiling nDPI...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
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
checking how to convert i686-pc-linux-gnu file names to i686-pc-linux-gnu format... func_convert_file_noop
checking how to convert i686-pc-linux-gnu file names to toolchain format... func_convert_file_noop
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
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
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
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking for stdint.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/lib/Makefile
config.status: creating src/include/Makefile
config.status: executing depfiles commands
config.status: executing libtool commands
Making all in src/include
make[1]: Entering directory `/tmp/ntop/ntop/nDPI/src/include'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/tmp/ntop/ntop/nDPI/src/include'
Making all in src/lib
make[1]: Entering directory `/tmp/ntop/ntop/nDPI/src/lib'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/tmp/ntop/ntop/nDPI/src/lib'
make[1]: Entering directory `/tmp/ntop/ntop/nDPI'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/tmp/ntop/ntop/nDPI'

Now we're ready to compile ntop

``````
make
``````
&& cd . && /bin/sh ./missing --run echo -I m4
-I m4
 cd . && /bin/sh ./missing --run echo --gnu
--gnu
CDPATH="${ZSH_VERSION+.}:" && cd . && /bin/sh ./missing --run echo

 /bin/bash ./config.status
config.status: creating Makefile
config.status: creating plugins/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands
CDPATH="${ZSH_VERSION+.}:" && cd . && /bin/sh ./missing --run echo -I m4
-I m4
 cd . && /bin/sh ./missing --run echo --gnu
--gnu
CDPATH="${ZSH_VERSION+.}:" && cd . && /bin/sh ./missing --run echo

(CDPATH="${ZSH_VERSION+.}:" && cd . && /bin/sh ./missing --run echo)

rm -f stamp-h1
touch config.h.in
cd . && /bin/bash ./config.status config.h
config.status: creating config.h
config.status: config.h is unchanged
make  all-recursive
make[1]: Entering directory `/tmp/ntop/ntop'
CDPATH="${ZSH_VERSION+.}:" && cd . && /bin/sh ./missing --run echo -I m4
-I m4
 cd . && /bin/sh ./missing --run echo --gnu
--gnu
CDPATH="${ZSH_VERSION+.}:" && cd . && /bin/sh ./missing --run echo

Making all in .
make[2]: Entering directory `/tmp/ntop/ntop'
CDPATH="${ZSH_VERSION+.}:" && cd . && /bin/sh ./missing --run echo -I m4
-I m4
 cd . && /bin/sh ./missing --run echo --gnu
--gnu
CDPATH="${ZSH_VERSION+.}:" && cd . && /bin/sh ./missing --run echo

/bin/bash ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I/usr/include/python2.7 -fno-strict-aliasing -DNDEBUG -fwrapv -O2 -Wall -Wstrict-prototypes -g -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -Werror=format-security  -I/usr/local/include -I ./nDPI/src/include/  -DLINUX -I/usr/local/include -I/opt/local/include  -g -O2 -I/usr/local/include -I/opt/local/include -Wshadow -Wpointer-arith -Wmissing-prototypes -Wmissing-declarations -Wnested-externs  -fPIC -DPIC  -I/usr/include/python2.7 -I/usr/include/python2.7 -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -g -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -Werror=format-security -MT version.lo -MD -MP -MF .deps/version.Tpo -c -o version.lo version.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I. -I/usr/include/python2.7 -fno-strict-aliasing -DNDEBUG -fwrapv -O2 -Wall -Wstrict-prototypes -g -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -Werror=format-security -I/usr/local/include -I ./nDPI/src/include/ -DLINUX -I/usr/local/include -I/opt/local/include -g -O2 -I/usr/local/include -I/opt/local/include -Wshadow -Wpointer-arith -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fPIC -DPIC -I/usr/include/python2.7 -I/usr/include/python2.7 -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -g -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -Werror=format-security -MT version.lo -MD -MP -MF .deps/version.Tpo -c version.c  -fPIC -DPIC -o .libs/version.o
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I. -I/usr/include/python2.7 -fno-strict-aliasing -DNDEBUG -fwrapv -O2 -Wall -Wstrict-prototypes -g -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -Werror=format-security -I/usr/local/include -I ./nDPI/src/include/ -DLINUX -I/usr/local/include -I/opt/local/include -g -O2 -I/usr/local/include -I/opt/local/include -Wshadow -Wpointer-arith -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fPIC -DPIC -I/usr/include/python2.7 -I/usr/include/python2.7 -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -g -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -Werror=format-security -MT version.lo -MD -MP -MF .deps/version.Tpo -c version.c -o version.o >/dev/null 2>&1
mv -f .deps/version.Tpo .deps/version.Plo
/bin/bash ./libtool --tag=CC   --mode=link gcc  -g -O2 -I/usr/local/include -I/opt/local/include -Wshadow -Wpointer-arith -Wmissing-prototypes -Wmissing-declarations -Wnested-externs  -fPIC -DPIC  -I/usr/include/python2.7 -I/usr/include/python2.7 -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -g -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -Werror=format-security  -release 5.0.2 -export-dynamic  -L/usr/local/lib -L/opt/local/lib -o libntop.la -rpath /usr/local/lib address.lo argv.lo dataFormat.lo event.lo globals-core.lo hash.lo ip.lo iface.lo initialize.lo leaks.lo ntop.lo pbuf.lo plugin.lo prefs.lo protocols.lo sessions.lo term.lo util.lo utildl.lo traffic.lo vendor.lo version.lo ntop_darwin.lo prng.lo countmin.lo -lcrypt -lc -lssl -lcrypto -lrrd_th -lpcap -lgdbm -lz -lpthread -ldl -lutil -lm -lpython2.7  -lGeoIP    ./nDPI/src/lib/.libs/libndpi.a 

*** Warning: Linking the shared library libntop.la against the
*** static library ./nDPI/src/lib/.libs/libndpi.a is not portable!
libtool: link: rm -fr  .libs/libntop-5.0.2.so .libs/libntop.a .libs/libntop.la .libs/libntop.lai .libs/libntop.so
libtool: link: gcc -shared  -fPIC -DPIC  .libs/address.o .libs/argv.o .libs/dataFormat.o .libs/event.o .libs/globals-core.o .libs/hash.o .libs/ip.o .libs/iface.o .libs/initialize.o .libs/leaks.o .libs/ntop.o .libs/pbuf.o .libs/plugin.o .libs/prefs.o .libs/protocols.o .libs/sessions.o .libs/term.o .libs/util.o .libs/utildl.o .libs/traffic.o .libs/vendor.o .libs/version.o .libs/ntop_darwin.o .libs/prng.o .libs/countmin.o   -L/usr/local/lib -L/opt/local/lib -lcrypt -lc -lssl -lcrypto -lrrd_th -lpcap -lgdbm -lz -lpthread -ldl -lutil -lm -lpython2.7 -lGeoIP ./nDPI/src/lib/.libs/libndpi.a  -O2 -O2   -Wl,-soname -Wl,libntop-5.0.2.so -o .libs/libntop-5.0.2.so
libtool: link: (cd ".libs" && rm -f "libntop.so" && ln -s "libntop-5.0.2.so" "libntop.so")
libtool: link: ar cru .libs/libntop.a ./nDPI/src/lib/.libs/libndpi.a  address.o argv.o dataFormat.o event.o globals-core.o hash.o ip.o iface.o initialize.o leaks.o ntop.o pbuf.o plugin.o prefs.o protocols.o sessions.o term.o util.o utildl.o traffic.o vendor.o version.o ntop_darwin.o prng.o countmin.o
libtool: link: ranlib .libs/libntop.a
libtool: link: ( cd ".libs" && rm -f "libntop.la" && ln -s "../libntop.la" "libntop.la" )
/bin/bash ./libtool --tag=CC   --mode=link gcc  -g -O2 -I/usr/local/include -I/opt/local/include -Wshadow -Wpointer-arith -Wmissing-prototypes -Wmissing-declarations -Wnested-externs  -fPIC -DPIC  -I/usr/include/python2.7 -I/usr/include/python2.7 -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -g -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -Werror=format-security  -release 5.0.2 -export-dynamic  -L/usr/local/lib -L/opt/local/lib -o libntopreport.la -rpath /usr/local/lib emitter.lo globals-report.lo graph.lo httpd.lo report.lo reportUtils.lo ssl_utils.lo webInterface.lo map.lo python.lo libntop.la -lcrypt -lc -lssl -lcrypto -lrrd_th -lpcap -lgdbm -lz -lpthread -ldl -lutil -lm -lpython2.7  -lGeoIP    ./nDPI/src/lib/.libs/libndpi.a 

*** Warning: Linking the shared library libntopreport.la against the
*** static library ./nDPI/src/lib/.libs/libndpi.a is not portable!
libtool: link: rm -fr  .libs/libntopreport-5.0.2.so .libs/libntopreport.a .libs/libntopreport.la .libs/libntopreport.lai .libs/libntopreport.so
libtool: link: gcc -shared  -fPIC -DPIC  .libs/emitter.o .libs/globals-report.o .libs/graph.o .libs/httpd.o .libs/report.o .libs/reportUtils.o .libs/ssl_utils.o .libs/webInterface.o .libs/map.o .libs/python.o   -Wl,-rpath -Wl,/tmp/ntop/ntop/.libs -L/usr/local/lib -L/opt/local/lib ./.libs/libntop.so -lcrypt -lc -lssl -lcrypto -lrrd_th -lpcap -lgdbm -lz -lpthread -ldl -lutil -lm -lpython2.7 -lGeoIP ./nDPI/src/lib/.libs/libndpi.a  -O2 -O2   -Wl,-soname -Wl,libntopreport-5.0.2.so -o .libs/libntopreport-5.0.2.so
libtool: link: (cd ".libs" && rm -f "libntopreport.so" && ln -s "libntopreport-5.0.2.so" "libntopreport.so")
libtool: link: ar cru .libs/libntopreport.a ./nDPI/src/lib/.libs/libndpi.a  emitter.o globals-report.o graph.o httpd.o report.o reportUtils.o ssl_utils.o webInterface.o map.o python.o
libtool: link: ranlib .libs/libntopreport.a
libtool: link: ( cd ".libs" && rm -f "libntopreport.la" && ln -s "../libntopreport.la" "libntopreport.la" )
/bin/bash ./libtool --tag=CC   --mode=link gcc  -g -O2 -I/usr/local/include -I/opt/local/include -Wshadow -Wpointer-arith -Wmissing-prototypes -Wmissing-declarations -Wnested-externs  -fPIC -DPIC  -I/usr/include/python2.7 -I/usr/include/python2.7 -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -g -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -Werror=format-security  -L/usr/local/lib -L/opt/local/lib -o ntop ntop-main.o ntop-admin.o libntopreport.la libntop.la -lcrypt -lc -lssl -lcrypto -lrrd_th -lpcap -lgdbm -lz -lpthread -ldl -lutil -lm -lpython2.7  -lGeoIP    ./nDPI/src/lib/.libs/libndpi.a 
libtool: link: gcc -g -O2 -I/usr/local/include -I/opt/local/include -Wshadow -Wpointer-arith -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fPIC -DPIC -I/usr/include/python2.7 -I/usr/include/python2.7 -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -g -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -Werror=format-security -o .libs/ntop ntop-main.o ntop-admin.o  -L/usr/local/lib -L/opt/local/lib ./.libs/libntopreport.so ./.libs/libntop.so -lcrypt -lc -lssl -lcrypto -lrrd_th -lpcap -lgdbm -lz -lpthread -ldl -lutil -lm -lpython2.7 -lGeoIP ./nDPI/src/lib/.libs/libndpi.a
make[2]: Leaving directory `/tmp/ntop/ntop'
Making all in plugins
make[2]: Entering directory `/tmp/ntop/ntop/plugins'
cd .. && make  am--refresh
make[3]: Entering directory `/tmp/ntop/ntop'
CDPATH="${ZSH_VERSION+.}:" && cd . && /bin/sh ./missing --run echo -I m4
-I m4
 cd . && /bin/sh ./missing --run echo --gnu
--gnu
CDPATH="${ZSH_VERSION+.}:" && cd . && /bin/sh ./missing --run echo

make[3]: Leaving directory `/tmp/ntop/ntop'
make[3]: Entering directory `/tmp/ntop/ntop'
CDPATH="${ZSH_VERSION+.}:" && cd . && /bin/sh ./missing --run echo -I m4
-I m4
 cd . && /bin/sh ./missing --run echo --gnu
--gnu
CDPATH="${ZSH_VERSION+.}:" && cd . && /bin/sh ./missing --run echo

make[3]: Leaving directory `/tmp/ntop/ntop'
cd .. && make  am--refresh
make[3]: Entering directory `/tmp/ntop/ntop'
CDPATH="${ZSH_VERSION+.}:" && cd . && /bin/sh ./missing --run echo -I m4
-I m4
 cd . && /bin/sh ./missing --run echo --gnu
--gnu
CDPATH="${ZSH_VERSION+.}:" && cd . && /bin/sh ./missing --run echo

make[3]: Leaving directory `/tmp/ntop/ntop'
Making all in .
make[3]: Entering directory `/tmp/ntop/ntop/plugins'
cd .. && make  am--refresh
make[4]: Entering directory `/tmp/ntop/ntop'
CDPATH="${ZSH_VERSION+.}:" && cd . && /bin/sh ./missing --run echo -I m4
-I m4
 cd . && /bin/sh ./missing --run echo --gnu
--gnu
CDPATH="${ZSH_VERSION+.}:" && cd . && /bin/sh ./missing --run echo

make[4]: Leaving directory `/tmp/ntop/ntop'
make[4]: Entering directory `/tmp/ntop/ntop'
CDPATH="${ZSH_VERSION+.}:" && cd . && /bin/sh ./missing --run echo -I m4
-I m4
 cd . && /bin/sh ./missing --run echo --gnu
--gnu
CDPATH="${ZSH_VERSION+.}:" && cd . && /bin/sh ./missing --run echo

make[4]: Leaving directory `/tmp/ntop/ntop'
cd .. && make  am--refresh
make[4]: Entering directory `/tmp/ntop/ntop'
CDPATH="${ZSH_VERSION+.}:" && cd . && /bin/sh ./missing --run echo -I m4
-I m4
 cd . && /bin/sh ./missing --run echo --gnu
--gnu
CDPATH="${ZSH_VERSION+.}:" && cd . && /bin/sh ./missing --run echo

make[4]: Leaving directory `/tmp/ntop/ntop'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/tmp/ntop/ntop/plugins'
make[2]: Leaving directory `/tmp/ntop/ntop/plugins'
make[1]: Leaving directory `/tmp/ntop/ntop'

``````
make install
``````
CDPATH="${ZSH_VERSION+.}:" && cd . && /bin/sh ./missing --run echo -I m4
-I m4
 cd . && /bin/sh ./missing --run echo --gnu
--gnu
CDPATH="${ZSH_VERSION+.}:" && cd . && /bin/sh ./missing --run echo

Making install in .
make[1]: Entering directory `/tmp/ntop/ntop'
CDPATH="${ZSH_VERSION+.}:" && cd . && /bin/sh ./missing --run echo -I m4
-I m4
 cd . && /bin/sh ./missing --run echo --gnu
--gnu
CDPATH="${ZSH_VERSION+.}:" && cd . && /bin/sh ./missing --run echo

make[2]: Entering directory `/tmp/ntop/ntop'
CDPATH="${ZSH_VERSION+.}:" && cd . && /bin/sh ./missing --run echo -I m4
-I m4
 cd . && /bin/sh ./missing --run echo --gnu
--gnu
CDPATH="${ZSH_VERSION+.}:" && cd . && /bin/sh ./missing --run echo

test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib"
 /bin/bash ./libtool   --mode=install /usr/bin/install -c   libntop.la libntopreport.la '/usr/local/lib'
libtool: install: /usr/bin/install -c .libs/libntop-5.0.2.so /usr/local/lib/libntop-5.0.2.so
/usr/bin/install: cannot create regular file `/usr/local/lib/libntop-5.0.2.so': Permission denied
make[2]: *** [install-libLTLIBRARIES] Error 1
make[2]: Leaving directory `/tmp/ntop/ntop'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/tmp/ntop/ntop'
make: *** [install-recursive] Error 1

```So, what did I do wrong?
I also tried ```
sudo apt-get install ntop
```I can login to older version but still cant make it display charts.
Missing something?
Thanks for your time.

---

### Post by steeldriver on 2012-09-06
I don't know why the version from the repository is not working for you, but

```
make install
```failed because without 'sudo' you do not have permission to write to /usr/local/lib - you would need to do 

```
sudo make install
```Perhaps if you describe exactly what issue you are having with the precompiled ntop someone can chime in and help with that though - before you resort to using the source build

---

### Post by mon deja vu on 2012-09-06
> **steeldriver said:**
> ... without 'sudo' you do not have  permission to write to /usr/local/lib - you would need to do 
```
sudo make install
```

Right, *sudo *helped + was missing few packages = installed
That's what i get now
```
Thu Sep  6 09:15:51 2012  ntop v.5.0.2 (32 bit)
Thu Sep  6 09:15:51 2012  Configured on Sep  6 2012  8:30:22, built on Sep  6 2012 08:31:56.
Thu Sep  6 09:15:51 2012  Copyright 1998-2012 by Luca Deri <deri@ntop.org>
Thu Sep  6 09:15:51 2012  Get the freshest ntop from http://www.ntop.org/
Thu Sep  6 09:15:51 2012  NOTE: ntop is running from 'ntop'
Thu Sep  6 09:15:51 2012  NOTE: (but see warning on man page for the --instance parameter)
Thu Sep  6 09:15:51 2012  NOTE: ntop libraries are in '/usr/local/lib'
Thu Sep  6 09:15:51 2012  Initializing ntop
Thu Sep  6 09:15:52 2012  No default device configured. Using eth0
Thu Sep  6 09:15:52 2012  Checking eth0 for additional devices
Thu Sep  6 09:15:52 2012  Resetting traffic statistics for device eth0
Thu Sep  6 09:15:52 2012  Initializing device eth0 (0)
Thu Sep  6 09:15:52 2012  DLT: Device 0 [eth0] is 1, mtu 1514, header 14
Thu Sep  6 09:15:52 2012  Initialized events [mask: 0][path: ]
Thu Sep  6 09:15:52 2012  Initializing gdbm databases
Thu Sep  6 09:15:52 2012  VENDOR: Loading MAC address table.
Thu Sep  6 09:15:52 2012  VENDOR: Checking for MAC address table file
Thu Sep  6 09:15:52 2012  VENDOR: Loading newer file '/usr/local/etc/ntop/specialMAC.txt.gz'
Thu Sep  6 09:15:52 2012  VENDOR: ...found 61 lines
Thu Sep  6 09:15:52 2012  VENDOR: ...loaded 59 records
Thu Sep  6 09:15:52 2012  VENDOR: Checking for MAC address table file
Thu Sep  6 09:15:52 2012  VENDOR: Loading newer file '/usr/local/etc/ntop/oui.txt.gz'
Thu Sep  6 09:15:52 2012  VENDOR: ...found 103494 lines
Thu Sep  6 09:15:52 2012  VENDOR: ...loaded 16325 records
Thu Sep  6 09:15:52 2012  Fingerprint: Loading signature file
Thu Sep  6 09:15:52 2012  Fingerprint: Checking for Fingerprint file... file
Thu Sep  6 09:15:52 2012  Fingerprint: Loading file '/usr/local/etc/ntop/etter.finger.os.gz'
Thu Sep  6 09:15:52 2012  Fingerprint: ...loaded 1765 records
Thu Sep  6 09:15:52 2012  Initializing external applications
Thu Sep  6 09:15:52 2012  THREADMGMT[t3056397120]: SFP: Started thread for fingerprinting
Thu Sep  6 09:15:52 2012  THREADMGMT[t3048004416]: SIH: Started thread for idle hosts detection
Thu Sep  6 09:15:52 2012  THREADMGMT[t3039611712]: DNSAR(1): Started thread for DNS address resolution
Thu Sep  6 09:15:52 2012  THREADMGMT[t3031219008]: DNSAR(2): Started thread for DNS address resolution
Thu Sep  6 09:15:52 2012  THREADMGMT[t3022826304]: DNSAR(3): Started thread for DNS address resolution
Thu Sep  6 09:15:52 2012  Calling plugin start functions (if any)
Thu Sep  6 09:15:52 2012  GeoIP: loaded config file /usr/local/etc/ntop/GeoLiteCity.dat
Thu Sep  6 09:15:52 2012  GeoIP: loaded ASN config file /usr/local/etc/ntop/GeoIPASNum.dat
Thu Sep  6 09:15:52 2012  NOTE: Interface merge enabled by default
Thu Sep  6 09:15:52 2012  SSL is present but https is disabled: use -W <https port> for enabling it
Thu Sep  6 09:15:52 2012  INITWEB: Initializing web server
Thu Sep  6 09:15:52 2012  INITWEB: Initializing TCP/IP socket connections for web server
Thu Sep  6 09:15:52 2012  **ERROR** INITWEB: binding problem - 'Bad file descriptor'(9)
Thu Sep  6 09:15:52 2012  Check if another instance of ntop is running
Thu Sep  6 09:15:52 2012  or if the current user (-u) can bind to the specified port
Thu Sep  6 09:15:52 2012  **FATAL_ERROR** Binding problem, ntop shutting down...
Thu Sep  6 09:15:52 2012  CLEANUP[t3078392576]: ntop caught signal 2 [state=2]
Thu Sep  6 09:15:52 2012  ntop is now quitting...

```Anyways,
> **steeldriver said:**
> 
...
Perhaps if you describe exactly  what issue you are having with the precompiled ntop someone can chime in  and help with that though - before you resort to using the source  build

[IMG]http://goo.gl/8P4Ji[/IMG]
Main problem, I guess, I just don't know what am I doing

---

### Post by steeldriver on 2012-09-06
did you get any config errors during the post install setup?

how are you starting the ntop process? 

have you actually checked to see if it is already running (ps -ef | grep ntop, or sudo netstat -ntp to look at port bindings)?

fwiw I just threw 3:4.0.3+dfsg1-3build1 from the repo on my old 11.10 Xubuntu laptop and it worked right out of the box

---

### Post by mon deja vu on 2012-09-06
> **steeldriver said:**
> did you get any config errors during the post install setup?

how are you starting the ntop process? 

have you actually checked to see if it is already running (ps -ef | grep ntop, or sudo netstat -ntp to look at port bindings)?

fwiw I just threw 3:4.0.3+dfsg1-3build1 from the repo on my old 11.10 Xubuntu laptop and it worked right out of the box
```
 sudo netstat -ntp
```Didn't find ntop there
Actually, after 
```
sudo /etc/init.d/ntop restart
```I get
```
sudo: /etc/init.d/ntop: command not found
```Installation from Synaptic didn't take me anywhere either
I guess I better start from the beginning.

---

