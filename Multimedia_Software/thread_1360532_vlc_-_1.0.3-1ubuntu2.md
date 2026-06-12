---
title: "vlc - 1.0.3-1ubuntu2"
date: 2009-12-21
forum: Multimedia Software
---

### Post by Harrison Pace on 2009-12-21
Hi I'm wondering how to install vlc - 1.0.3-1ubuntu2 it's in a tar.gz and I have no idea how to compile. Please help I'm desperate! ](*,) Reason is cario dock only works with this version of vlc. Any help is appreciated!  Im on karmic with i386 Architecture. Link [https://launchpad.net/ubuntu/+source/vlc/1.0.3-1ubuntu2](https://launchpad.net/ubuntu/+source/vlc/1.0.3-1ubuntu2)! Thanks in Advance!

---

### Post by ankur1990 on 2009-12-21
extract the file into a separate folder.
then open terminal and move in that folder using cd commands.
then type ./configure 
then make
then make install or sudo make install (depends on ur login account)
all done :) and the software gets installed :)

---

### Post by Yellow Pasque on 2009-12-21
Search PPA's for an updated version. Compiling could be a pain. If you want any shot at getting it built, run this first:
```
sudo apt-get build-dep vlc-nox
```

---

### Post by Harrison Pace on 2009-12-22
Thanks For Feedback! Sorry for taking time lost ubuntu desktop grub got corrupt then hdd failed. But I'm good now! :)  Anyway did both as you said and this is what happened.


harrison@Toshiba-Laptop:~$ sudo apt-get build-dep vlc-nox
[sudo] password for harrison: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have unmet dependencies:
  libqt4-dev: Depends: libpq-dev but it is not going to be installed
  libsmbclient-dev: Depends: libsmbclient (= 2:3.4.0-3ubuntu5.1) but 2:3.4.0-3ubuntu5.3 is to be installed
E: Build-dependencies for vlc-nox could not be satisfied.
harrison@Toshiba-Laptop:~$ cd /home/harrison/Desktop/vlc-1.0.3
harrison@Toshiba-Laptop:~/Desktop/vlc-1.0.3$ ./configure 
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether to enable maintainer-specific portions of Makefiles... yes
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
checking for libs in /home/harrison/Desktop/vlc-1.0.3/./extras/contrib... no
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
checking for ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... (cached) pass_all
checking for ar... (cached) ar
checking for strip... (cached) strip
checking for ranlib... (cached) ranlib
checking command to parse /usr/bin/nm -B output from gcc -std=gnu99 object... ok
checking for dlfcn.h... yes
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking how to run the C++ preprocessor... g++ -E
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
checking for ld used by g++... ld
checking if the linker (ld) is GNU ld... yes
checking whether the g++ linker (ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether NLS is requested... yes
checking for msgfmt... no
checking for gmsgfmt... :
checking for xgettext... no
checking for msgmerge... no
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
checking for iconv declaration... install-shextern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking for buggy GNU/libc versions... not present
checking for shared objects suffix... .so
checking for gettimeofday... yes
checking for isatty... yes
checking for sigrelse... yes
checking for getpwuid_r... yes
checking for memalign... yes
checking for posix_memalign... yes
checking for if_nametoindex... yes
checking for getenv... yes
checking for putenv... yes
checking for setenv... yes
checking for ctime_r... yes
checking for lrintf... no
checking for daemon... yes
checking for fork... yes
checking for lstat... yes
checking for posix_fadvise... yes
checking for posix_madvise... yes
checking for uselocale... yes
checking for working alloca.h... yes
checking for alloca... yes
checking for fcntl... yes
checking for asprintf... yes
checking for atof... yes
checking for atoll... yes
checking for getcwd... yes
checking for gmtime_r... yes
checking for lldiv... yes
checking for localtime_r... yes
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
checking for strtoll... yes
checking for vasprintf... yes
checking for swab... yes
checking for stricmp... no
checking for strnicmp... no
checking for fdatasync... yes
checking for vmsplice... yes
checking for eventfd... yes
checking for fstatfs... yes
checking for mmap... yes
checking for setlocale... yes
checking langinfo.h usability... yes
checking langinfo.h presence... yes
checking for langinfo.h... yes
checking for nl_langinfo... yes
checking for nl_langinfo and CODESET... yes
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
checking return type of signal handlers... void
checking for cos in -lm... yes
checking for pow in -lm... yes
checking for sqrt in -lm... yes
checking for ceil in -lm... yes
checking for exp in -lm... yes
checking for round in -lm... yes
checking for sqrtf in -lm... yes
checking for lrintf in -lm... yes
checking mach-o/dyld.h usability... no
checking mach-o/dyld.h presence... no
checking for mach-o/dyld.h... no
checking dl.h usability... no
checking dl.h presence... no
checking for dl.h... no
checking for shl_load... (cached) no
checking for dld_link in -ldld... no
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
checking for sys/types.h... (cached) yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking sys/times.h usability... yes
checking sys/times.h presence... yes
checking for sys/times.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking for sys/stat.h... (cached) yes
checking sys/mount.h usability... yes
checking sys/mount.h presence... yes
checking for sys/mount.h... yes
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
checking syslog.h usability... yes
checking syslog.h presence... yes
checking for syslog.h... yes
checking whether time.h and sys/time.h may both be included... yes
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
checking zlib.h usability... no
checking zlib.h presence... no
checking for zlib.h... no
checking for HAL... no
configure: WARNING: libhal >= 0.5.0 was not found. Install libhal-dev ?
checking for UDEV... no
checking for MTP... no
configure: WARNING: MTP library not found
checking for DBUS... no
configure: error: Couldn't find DBus >= 1.0.0, install libdbus-dev ?
harrison@Toshiba-Laptop:~/Desktop/vlc-1.0.3$ make
make: *** No targets specified and no makefile found.  Stop.
harrison@Toshiba-Laptop:~/Desktop/vlc-1.0.3$ sudo make install
make: *** No rule to make target `install'.  Stop.
harrison@Toshiba-Laptop:~/Desktop/vlc-1.0.3$ 





No ppa updated version as well so please help anyone?:confused:

---

### Post by HappyFeet on 2009-12-23
[Here]("https://launchpad.net/~c-korn/+archive/vlc") is the PPA for it. No need to compile it.

---

### Post by mc4man on 2009-12-23
Your fairly far away from being able to build vlc and as far again for a good built.

Apparently you had the 'proposed' repo source enabled and then ran an update. It would also appear that source is no longer enabled ( which is for the best, updates to packages in proposed are generally for testing, not general use.

that's why you get this, both libsmbclient and something libpq and or libqt4 depend on has been updated to the proposed versions and the matching dev's are not available (without enabling proposed again.

> The following packages have unmet dependencies:
libqt4-dev: Depends: libpq-dev but it is not going to be installed
libsmbclient-dev: Depends: libsmbclient (= 2:3.4.0-3ubuntu5.1) but 2:3.4.0-3ubuntu5.3 is to be installed

( vlc requires about 60  -70 packages (devs) not including matching libs and build tools

The korn ppa 1.0.3 was built without the ubuntu patch for cairo-dock, if he does a new build it may have it.

Considering your present state and inexperience, maybe try adding the getdeb repo, installing the 1.0.4 version of vlc there, and **then disable** the getdeb repo.

[http://www.getdeb.net/welcome/](http://www.getdeb.net/welcome/)

edit:
It's unlikely any 1.0.3 build before 11/21 would have the cairo patch

> vlc (1.0.3-1ubuntu2) lucid; urgency=low

  [ Reinhard Tartler ]
  * don't crash when cairo-dock is running. LP: #416294
    Very ugly patch from upstream to disable ARGB channel usage 
    in libqt4
  * enable and install the fb module on Linux systems. Closes: #556228

  [ Whoopie ]
  * enable CDDB in the CDDA module (LP: #439131) and enable
    globalhotkeys module (LP: #439077)

 -- Reinhard Tartler <siretart@tauware.de>  Sat, 21 Nov 2009 22:11:48 +0100

---

### Post by HappyFeet on 2009-12-23
A weird thing happened. I completely removed vlc 1.0.2 and went to getdeb.net and installed 1.0.4 but when I launched vlc, it said the version is 1.0.2

Edit: I added the repos for getdeb manually, and was able to upgrade vlc to 1.0.4

---

### Post by mc4man on 2009-12-23
> Edit: I added the repos for getdeb manually...

I haven't tested anything from the 'new' getdeb, I gathering you found doing
> 2. Or configure the repository manually:

the way Harrison should follow if he so chooses?

---

### Post by Harrison Pace on 2009-12-23
Hi guys thanks for your time really helpful :-) Give yourself a pat on the back. Anyways I've just installed the PPA thingy and nothings happening I'm going to update manager and there is no new updates. Yea I'm a n00b when it comes to ubuntu. Not a n00b otherwise. So what do I do could you explain in easy or n00b language. Thanks (Sorry new to linux as  I just couldn't stand using windows. And moving to liux has been a really good choice BYE-BYE anti virus)   

Again Thanks in advanced! PS Rock on :guitar:

---

### Post by Harrison Pace on 2009-12-23
Anyone Please Help still having issue even from getdeb.net vlc deb file crashes straight away with any video file

---

### Post by Yellow Pasque on 2009-12-24
Maybe you didn't get all of the dependencies. See if this pulls more:
[sudo apt-get build-dep vlc[/code]

---

### Post by HappyFeet on 2009-12-24
> **Harrison Pace said:**
> Anyone Please Help still having issue even from getdeb.net vlc deb file crashes straight away with any video file

When you go to about vlc in the menus, what version is installed?

---

### Post by Harrison Pace on 2009-12-24
How do I add repo manually?

---

### Post by mc4man on 2009-12-24
Quoting from [URL="http://www.getdeb.net/updates/Ubuntu/all#how_to_install"]here
[/URL]
> Or configure the repository manually:

Go to System-Administration-Software Sources, Third-Party Software tab, Add:
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) karmic-getdeb apps

In other words  - click on the add button and paste this in the pop up box

```
deb http://archive.getdeb.net/ubuntu karmic-getdeb apps
```

Then click 'add source', 'close' and 'reload'

When that's done either run the update manager and you should see updates for vlc or search vlc in synaptic and mark for upgrade.

can't guarantee it will resolve cairo-dock, you'll have to see

Also maybe read [here]("http://ubuntuforums.org/showthread.php?t=1363568")

( I don't have cairo-dock and have no reason to install...but good luck.

---

### Post by Harrison Pace on 2009-12-25
Thanks got it working all good cya and rock on! :guitar: 

You guys or gals are awesome :KS

---

