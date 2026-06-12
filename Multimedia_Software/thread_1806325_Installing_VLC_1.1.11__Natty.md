---
title: "Installing VLC 1.1.11 || Natty"
date: 2011-07-17
forum: Multimedia Software
---

### Post by linuxyogi on 2011-07-17
Hi, 

I am trying to install vlc 1.1.11 from source. Here's the problem 

I installed lua 

```
$ aptitude search lua5.1
i A liblua5.1-0                                     - Simple, extensible, embeddable programming language   

```But .....

```
$ ./configure 
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether to enable maintainer-specific portions of Makefiles... yes
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
checking for gcc option to accept ISO C99... -std=gnu99
checking how to run the C preprocessor... gcc -std=gnu99 -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking whether it is safe to define __EXTENSIONS__... yes
checking whether gcc -std=gnu99 and cc understand -c and -o together... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C preprocessor... gcc -std=gnu99 -E
checking for gcc... gcc
checking whether we are using the GNU Objective C compiler... no
checking whether gcc accepts -g... no
checking dependency style of gcc... gcc3
checking dependency style of gcc... (cached) gcc3
checking for egrep... (cached) /bin/grep -E
checking whether make sets $(MAKE)... (cached) yes
checking dependency style of gcc -std=gnu99... gcc3
checking for ranlib... ranlib
checking for strip... strip
checking for ar... ar
checking for ld... ld
checking for dlltool... no
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for C/C++ restrict keyword... __restrict
checking for libs in /home/user0/vlc-1.1.11/./extras/contrib/hosts/i686-linux-gnu... no
checking how to print strings... printf
checking for a sed that does not truncate output... /bin/sed
checking for fgrep... /bin/grep -F
checking for ld used by gcc -std=gnu99... ld
checking if the linker (ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking how to convert i686-pc-linux-gnu file names to i686-pc-linux-gnu format... func_convert_file_noop
checking how to convert i686-pc-linux-gnu file names to toolchain format... func_convert_file_noop
checking for ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... (cached) pass_all
checking for dlltool... :
checking how to associate runtime and link libraries... printf %s\n
checking for archiver @FILE support... @
checking for strip... (cached) strip
checking for ranlib... (cached) ranlib
checking command to parse /usr/bin/nm -B output from gcc -std=gnu99 object... ok
checking for sysroot... no
checking for mt... mt
checking if mt is a manifest tool... no
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc -std=gnu99 supports -fno-rtti -fno-exceptions... no
checking for gcc -std=gnu99 option to produce PIC... -fPIC -DPIC
checking if gcc -std=gnu99 PIC flag -fPIC -DPIC works... yes
checking if gcc -std=gnu99 static flag -static works... yes
checking if gcc -std=gnu99 supports -c -o file.o... yes
checking if gcc -std=gnu99 supports -c -o file.o... (cached) yes
checking whether the gcc -std=gnu99 linker (ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... no
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking how to run the C++ preprocessor... g++ -E
checking for ld used by g++... ld
checking if the linker (ld) is GNU ld... yes
checking whether the g++ linker (ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (ld) supports shared libraries... yes
checking dynamic linker characteristics... (cached) GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for ld used by GCC... ld
checking if the linker (ld) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for iconv... yes
checking for working iconv... yes
checking for iconv declaration... 
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking for buggy GNU/libc versions... not present
checking for shared objects suffix... .so
checking for ctime_r... yes
checking for daemon... yes
checking for fcntl... yes
checking for fdopendir... yes
checking for fstatvfs... yes
checking for fork... yes
checking for getenv... yes
checking for getpwuid_r... yes
checking for gettimeofday... yes
checking for isatty... yes
checking for lstat... yes
checking for memalign... yes
checking for openat... yes
checking for posix_fadvise... yes
checking for posix_madvise... yes
checking for posix_memalign... yes
checking for setenv... yes
checking for setlocale... yes
checking for stricmp... no
checking for strnicmp... no
checking for tdestroy... yes
checking for uselocale... yes
checking for asprintf... yes
checking for atof... yes
checking for atoll... yes
checking for getcwd... yes
checking for getdelim... yes
checking for getpid... yes
checking for gmtime_r... yes
checking for lldiv... yes
checking for localtime_r... yes
checking for nrand48... yes
checking for rewind... yes
checking for strcasecmp... yes
checking for strcasestr... yes
checking for strdup... yes
checking for strlcpy... no
checking for strncasecmp... yes
checking for strndup... yes
checking for strnlen... yes
checking for strsep... yes
checking for strtof... yes
checking for strtok_r... yes
checking for strtoll... yes
checking for swab... yes
checking for vasprintf... yes
checking for fdatasync... yes
checking for accept4... yes
checking for dup3... yes
checking for eventfd... yes
checking for vmsplice... yes
checking for mmap... yes
checking for connect... yes
checking for send... yes
checking for socklen_t in sys/socket.h... yes
checking for struct sockaddr_storage... yes
checking for library containing getaddrinfo... none required
checking for getnameinfo... yes
checking for gai_strerror... yes
checking for struct addrinfo... yes
checking for va_copy... yes
checking for __va_copy... yes
checking for inet_aton... yes
checking for getopt_long... yes
checking for cos in -lm... yes
checking for pow in -lm... yes
checking for sqrt in -lm... yes
checking for ceil in -lm... yes
checking for exp in -lm... yes
checking for round in -lm... yes
checking for sqrtf in -lm... yes
checking for lrintf in -lm... yes
checking dl.h usability... no
checking dl.h presence... no
checking for dl.h... no
checking for shl_load... (cached) no
checking image.h usability... no
checking image.h presence... no
checking for image.h... no
checking for load_add_on... no
checking for dlfcn.h... (cached) yes
checking sys/dl.h usability... no
checking sys/dl.h presence... no
checking for sys/dl.h... no
checking for dlopen... (cached) no
checking for dlopen in -ldl... (cached) yes
checking for main in -lpthread... yes
checking for clock_nanosleep in -lrt... yes
checking for nanosleep... yes
checking for strncasecmp in strings.h... yes
checking getopt.h usability... yes
checking getopt.h presence... yes
checking for getopt.h... yes
checking for strings.h... (cached) yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking xlocale.h usability... yes
checking xlocale.h presence... yes
checking for xlocale.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking for sys/stat.h... (cached) yes
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking netinet/udplite.h usability... no
checking netinet/udplite.h presence... no
checking for netinet/udplite.h... no
checking sys/eventfd.h usability... yes
checking sys/eventfd.h presence... yes
checking for sys/eventfd.h... yes
checking for net/if.h... yes
checking for sys/mount.h... yes
checking machine/param.h usability... no
checking machine/param.h presence... no
checking for machine/param.h... no
checking sys/shm.h usability... yes
checking sys/shm.h presence... yes
checking for sys/shm.h... yes
checking linux/version.h usability... yes
checking linux/version.h presence... yes
checking for linux/version.h... yes
checking linux/dccp.h usability... yes
checking linux/dccp.h presence... yes
checking for linux/dccp.h... yes
checking scsi/scsi.h usability... yes
checking scsi/scsi.h presence... yes
checking for scsi/scsi.h... yes
checking linux/magic.h usability... yes
checking linux/magic.h presence... yes
checking for linux/magic.h... yes
checking syslog.h usability... yes
checking syslog.h presence... yes
checking for syslog.h... yes
checking for ssize_t... yes
checking for library containing poll... none required
checking dirent.h usability... yes
checking dirent.h presence... yes
checking for dirent.h... yes
checking for nanosleep in time.h... yes
checking for timespec in sys/time.h... yes
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for MINIZIP... no
checking unzip.h usability... no
checking unzip.h presence... no
checking for unzip.h... no
checking for DBUS... yes
checking for ntohl in sys/param.h... no
checking if gcc -std=gnu99 accepts -Wall... yes
checking if gcc -std=gnu99 accepts -Wextra... yes
checking if gcc -std=gnu99 accepts -Wsign-compare... yes
checking if gcc -std=gnu99 accepts -Wundef... yes
checking if gcc -std=gnu99 accepts -Wpointer-arith... yes
checking if gcc -std=gnu99 accepts -Wbad-function-cast... yes
checking if gcc -std=gnu99 accepts -Wwrite-strings... yes
checking if gcc -std=gnu99 accepts -Wmissing-prototypes... yes
checking if gcc -std=gnu99 accepts -Wvolatile-register-var... yes
checking if gcc -std=gnu99 accepts -Werror-implicit-function-declaration... yes
checking if gcc -std=gnu99 accepts -pipe... yes
checking if $CC accepts -Os... yes
checking if $CC accepts -O4... yes
checking if $CC accepts -O3... yes
checking if $CC accepts -O2... yes
checking if $CC accepts -O0... yes
checking if $CC accepts -ffast-math... yes
checking if $CC accepts -funroll-loops... yes
checking if $CC accepts -fomit-frame-pointer... yes
checking if $CC accepts -bundle -undefined error... no
checking __attribute__ ((aligned ())) support... 64
checking for __attribute__((packed))... yes
checking execinfo.h usability... yes
checking execinfo.h presence... yes
checking for execinfo.h... yes
checking for backtrace... yes
checking if gcc -std=gnu99 groks MMX intrinsics... yes
checking if gcc -std=gnu99 groks MMX inline assembly... yes
checking if gcc -std=gnu99 groks MMX EXT inline assembly... yes
checking if gcc -std=gnu99 groks SSE2 intrinsics... yes
checking if gcc -std=gnu99 groks SSE inline assembly... yes
checking if gcc -std=gnu99 groks SSE2 inline assembly... yes
checking if gcc -std=gnu99 groks SSE3 inline assembly... yes
checking if gcc -std=gnu99 groks SSSE3 inline assembly... yes
checking if gcc -std=gnu99 groks SSE4.1 inline assembly... yes
checking if gcc -std=gnu99 groks SSE4.2 inline assembly... yes
checking if gcc -std=gnu99 groks SSE4A inline assembly... yes
checking if gcc -std=gnu99 groks 3D Now! inline assembly... yes
checking whether gcc -std=gnu99 accepts -mtune=pentium2... yes
checking for LUA... no
configure: WARNING: lua5.1 not found, trying lua >= 5.1 instead
checking for LUA... no
checking lua.h usability... no
checking lua.h presence... no
checking for lua.h... no
checking lauxlib.h usability... no
checking lauxlib.h presence... no
checking for lauxlib.h... no
checking lualib.h usability... no
checking lualib.h presence... no
checking for lualib.h... no
checking for luaL_newstate in -llua5.1 ... no
checking for luaL_newstate in -llua51 ... no
checking for luaL_newstate in -llua ... no
configure: error: Could not find lua. Lua is needed for some interfaces (rc, telnet, http) as well as many other custom scripts. Use --disable-lua to ignore this error.

```I tried the --disable-lua  but no matter what deps I install ./configure can't find it.

I am not really used to build stuff from source.

How to solve this ?

---

### Post by linuxyogi on 2011-07-17
Did

```
sudo apt-get build-dep vlc && sudo apt-get install libtool build-essential 
```Then 

./configure 
sudo make 
sudo make install

Now, vlc is installed.

But 

```
$ vlc
VLC media player 1.1.9 The Luggage (revision exported)
[0x91c8914] main libvlc error: No modules were found, refusing to start. Check that you properly gave a module path with --plugin-path.
```So I am doing 

```
$ vlc --plugin-path=/usr/local/lib/vlcVLC media player 1.1.9 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x8623914] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
```Problem is I cant play any videos with vlc ATM, only audio plays.

```
$ vlc --plugin-path=/usr/local/lib/vlc /home/user0/test.mp4 
VLC media player 1.1.9 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x80fb914] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
libva: libva version 0.31.1
Xlib:  extension "XFree86-DRI" missing on display ":0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/dri/nvidia_drv_video.so
libva: va_openDriver() returns -1
[0x8358174] main video output error: video output creation failed
[0x8293acc] main decoder error: failed to create video output
[0x83ad4bc] main video output error: video output creation failed
[0x8293acc] main decoder error: failed to create video output


```




[IMG]http://dl.dropbox.com/u/30630174/Screenshot-Preferences.png[/IMG]

---

### Post by ron999 on 2011-07-17
Hi
Maybe you should use the tutorial here:- [http://ubuntuforums.org/showthread.php?t=1398119]("http://ubuntuforums.org/showthread.php?t=1398119")

---

### Post by linuxyogi on 2011-07-17
> **ron999 said:**
> Hi
Maybe you should use the tutorial here:- [http://ubuntuforums.org/showthread.php?t=1398119](http://ubuntuforums.org/showthread.php?t=1398119)

Thanks for the link. 

Reinstalled the package libgl1-mesa-glx and again did 

sudo make
sudo make install

No more isssues. :grin:

---

