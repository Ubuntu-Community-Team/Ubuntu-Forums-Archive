---
title: "Can't compile Darkice with AAC"
date: 2007-10-22
forum: Multimedia &amp; Video
---

### Post by wheezart on 2007-10-22
Hello!

I have been trying to compile [Darkice]("http://darkice.tyrell.hu/") from source so i can enable AAC support for it (since the one in the repos isn't compiled with it), but i keep getting the same error, even though i have installed all the corresponding packages from the repos ```
whiz@whiz-satellite:~/darkice-0.18.1/darkice-0.18.1$ ./configure --with-alsa --with-lame --with-faac
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/home/whiz/darkice-0.18.1/darkice-0.18.1/missing: Unknown `--run' option
Try `/home/whiz/darkice-0.18.1/darkice-0.18.1/missing --help' for more information
configure: WARNING: `missing' script is too old or missing
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
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
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking stdio.h usability... yes
checking stdio.h presence... yes
checking for stdio.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking time.h usability... yes
checking time.h presence... yes
checking for time.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for sys/types.h... (cached) yes
checking sys/wait.h usability... yes
checking sys/wait.h presence... yes
checking for sys/wait.h... yes
checking math.h usability... yes
checking math.h presence... yes
checking for math.h... yes
checking netdb.h usability... yes
checking netdb.h presence... yes
checking for netdb.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking for sys/stat.h... (cached) yes
checking sched.h usability... yes
checking sched.h presence... yes
checking for sched.h... yes
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking termios.h usability... yes
checking termios.h presence... yes
checking for termios.h... yes
checking sys/soundcard.h usability... yes
checking sys/soundcard.h presence... yes
checking for sys/soundcard.h... yes
checking sys/audio.h usability... no
checking sys/audio.h presence... no
checking for sys/audio.h... no
checking sys/audioio.h usability... no
checking sys/audioio.h presence... no
checking for sys/audioio.h... no
checking for sys/wait.h that is POSIX.1 compatible... (cached) yes
checking for pid_t... yes
checking for size_t... yes
checking whether byte ordering is bigendian... no
checking for socket in -lsocket... no
checking for gethostbyname in -lnsl... yes
checking for sched_getscheduler in -lrt... yes
checking for getaddrinfo... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for pthread-config... no
checking for the pthreads library -lpthreads... no
checking whether pthreads work without any flags... yes
checking for joinable pthread attribute... PTHREAD_CREATE_JOINABLE
checking if more special flags are required for pthreads... no
checking for cc_r... gcc
checking for lame library at /usr ... configure: WARNING: not found, building without lame
checking for vorbis libraries at /usr ... configure: WARNING: not found, building without Ogg Vorbis
checking for faac library at /usr ... configure: WARNING: not found, building without faac
checking for twolame library at /usr ... configure: WARNING: not found, building without twolame
configure: error: neither lame, Ogg Vorbis, faac nor twolame configured
whiz@whiz-satellite:~/darkice-0.18.1/darkice-0.18.1$ 
```

I don't know what am i doing wrong, any ideas?

---

### Post by wheezart on 2007-10-23
Bumpiddy-bump, does this belong here?

---

