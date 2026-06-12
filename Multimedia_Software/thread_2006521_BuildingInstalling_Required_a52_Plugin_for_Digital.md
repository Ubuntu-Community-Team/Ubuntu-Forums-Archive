---
title: "Building/Installing Required a52 Plugin for DigitalAC-3Pulseaudio"
date: 2012-06-19
forum: Multimedia Software
---

### Post by Terror1980 on 2012-06-19
I am trying to compile and install the a52 plugin following the instructions from here:

[https://help.ubuntu.com/community/DigitalAC-3Pulseaudio](https://help.ubuntu.com/community/DigitalAC-3Pulseaudio)

This worked on Ubuntu 11.10 but gives me some errors when I try to compile the plugin on Ubuntu 12.04. I've searched for a solution however I couldn't find much on this topic in general, not to talk about a solution. I would really appreciate some help on this:

```
bogdan@bogdan-desktop:~$ cd ~/tmp/
bogdan@bogdan-desktop:~/tmp$ cd alsa-plugins-1.0.25/
bogdan@bogdan-desktop:~/tmp/alsa-plugins-1.0.25$ make
make  all-recursive
make[1]: Entering directory `/home/bogdan/tmp/alsa-plugins-1.0.25'
Making all in oss
make[2]: Entering directory `/home/bogdan/tmp/alsa-plugins-1.0.25/oss'
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..    -Wall -g -I/usr/include/alsa   -g -O2 -MT ctl_oss.lo -MD -MP -MF .deps/ctl_oss.Tpo -c -o ctl_oss.lo ctl_oss.c
../libtool: line 831: X--tag=CC: command not found
../libtool: line 864: libtool: ignoring unknown tag : command not found
../libtool: line 831: X--mode=compile: command not found
../libtool: line 997: *** Warning: inferring the mode of operation is deprecated.: command not found
../libtool: line 998: *** Future versions of Libtool will require --mode=MODE be specified.: command not found
../libtool: line 1141: Xgcc: command not found
../libtool: line 1141: X-DHAVE_CONFIG_H: command not found
../libtool: line 1141: X-I.: command not found
../libtool: line 1141: X-I..: command not found
../libtool: line 1141: X-Wall: command not found
../libtool: line 1141: X-g: command not found
../libtool: line 1141: X-I/usr/include/alsa: No such file or directory
../libtool: line 1141: X-g: command not found
../libtool: line 1141: X-O2: command not found
../libtool: line 1141: X-MT: command not found
../libtool: line 1141: Xctl_oss.lo: command not found
../libtool: line 1141: X-MD: command not found
../libtool: line 1141: X-MP: command not found
../libtool: line 1141: X-MF: command not found
../libtool: line 1141: X.deps/ctl_oss.Tpo: No such file or directory
../libtool: line 1141: X-c: command not found
../libtool: line 1192: Xctl_oss.lo: command not found
../libtool: line 1197: libtool: compile: cannot determine name of library object from `': command not found
make[2]: *** [ctl_oss.lo] Error 1
make[2]: Leaving directory `/home/bogdan/tmp/alsa-plugins-1.0.25/oss'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/bogdan/tmp/alsa-plugins-1.0.25'
make: *** [all] Error 2
bogdan@bogdan-desktop:~/tmp/alsa-plugins-1.0.25$
```

---

### Post by BicyclerBoy on 2012-06-19
You have to run 
./configure
to create all the makefiles etc for your platform &/or build options.
Then try 
make

Your tmp folder has r/w permissions for your user ?

---

### Post by Terror1980 on 2012-06-20
> **BicyclerBoy said:**
> You have to run 
./configure
to create all the makefiles etc for your platform &/or build options.
Then try 
make

Your tmp folder has r/w permissions for your user ?

I did run ./configure. The reason I didn't include the output for it was because it executed OK without errors 

The permissions for my user for tmp folder (in ~/tmp):

drwxrwxr-x 3 bogdan bogdan   4096 Jun 14 15:39 tmp

See below the output of ./configure:

```
bogdan@bogdan-desktop:~/tmp/alsa-plugins-1.0.25$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking how to print strings... printf
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
checking whether to build static libraries... no
checking for ANSI C header files... (cached) yes
checking if gcc supports -Wl,--no-undefined flag... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for ALSA... yes
checking for snd_pcm_ioplug_create in -lasound... yes
checking for JACK... no
checking for pulseaudio... yes
checking for samplerate... yes
checking for AVCODEC... yes
checking ffmpeg/avcodec.h usability... no
checking ffmpeg/avcodec.h presence... no
checking for ffmpeg/avcodec.h... no
checking libavcodec/avcodec.h usability... yes
checking libavcodec/avcodec.h presence... yes
checking for libavcodec/avcodec.h... yes
checking for speexdsp... yes
checking for speex_resampler_init in -lspeexdsp... yes
checking for plugins version... 1.0.25
configure: creating ./config.status
config.status: creating Makefile
config.status: creating oss/Makefile
config.status: creating pph/Makefile
config.status: creating jack/Makefile
config.status: creating pulse/Makefile
config.status: creating mix/Makefile
config.status: creating rate/Makefile
config.status: creating a52/Makefile
config.status: creating rate-lavc/Makefile
config.status: creating maemo/Makefile
config.status: creating doc/Makefile
config.status: creating usb_stream/Makefile
config.status: creating speex/Makefile
config.status: creating arcam-av/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands

Plugin directory: /usr/lib/alsa-lib
ALSA_CFLAGS: -I/usr/include/alsa  
ALSA_LIBS: -lasound  
JACK plugin:        no
Pulseaudio plugin:  yes
  pulseaudio_CFLAGS: -D_REENTRANT  
  pulseaudio_LIBS: -lpulse  
Samplerate plugin:  yes
  samplerate_CFLAGS:  
  samplerate_LIBS: -lsamplerate  
Maemo plugin:       no
  Using Osso resource manager: no
A52, lavc plugins:  yes
  AVCODEC_CFLAGS:  
  AVCODEC_LIBS: -lavcodec -lavutil  
  AVCODEC_HEADER: <libavcodec/avcodec.h>
Speex rate plugin:  lib
Speex preprocess plugin:  yes
bogdan@bogdan-desktop:~/tmp/alsa-plugins-1.0.25$
```

---

### Post by Terror1980 on 2012-06-20
Found the solution to this problem!

The solution:

> libtoolize --force --copy; aclocal; autoconf; automake; make
(source: [http://geeklymusings.blogspot.ro/2009/04/libtool-problems-on-ubuntu.html](http://geeklymusings.blogspot.ro/2009/04/libtool-problems-on-ubuntu.html) )

---

