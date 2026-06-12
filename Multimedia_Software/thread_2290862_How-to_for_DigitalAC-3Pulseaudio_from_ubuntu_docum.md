---
title: "How-to for DigitalAC-3Pulseaudio from ubuntu documentation won't compile on 15.04"
date: 2015-08-16
forum: Multimedia Software
---

### Post by marina071170 on 2015-08-16
Dear Community.

Lately, I've upgraded my system(s) from 14.04 to 15.04 on both machines (laptop and desktop) I used to have the A52 codec installed. I have followed all the steps from the help wiki: [https://help.ubuntu.com/community/DigitalAC-3Pulseaudio](https://help.ubuntu.com/community/DigitalAC-3Pulseaudio) really step-by-step, I didn't use the script. It used to work on 14.04 but now the compiling always fails at the same point.

Here is the output of the command:
 ```
libtoolize --force --copy && aclocal && autoconf && automake --add-missing && make

libtoolize: putting auxiliary files in `.'.
libtoolize: copying file `./ltmain.sh'
libtoolize: putting macros in AC_CONFIG_MACRO_DIR, `m4'.
libtoolize: copying file `m4/libtool.m4'
libtoolize: copying file `m4/ltoptions.m4'
libtoolize: copying file `m4/ltsugar.m4'
libtoolize: copying file `m4/ltversion.m4'
libtoolize: copying file `m4/lt~obsolete.m4'
configure.ac:17: warning: AC_LANG_CONFTEST: no AC_LANG_SOURCE call detected in body
../../lib/autoconf/lang.m4:193: AC_LANG_CONFTEST is expanded from...
../../lib/autoconf/general.m4:2661: _AC_LINK_IFELSE is expanded from...
../../lib/autoconf/general.m4:2678: AC_LINK_IFELSE is expanded from...
../../lib/m4sugar/m4sh.m4:639: AS_IF is expanded from...
../../lib/autoconf/general.m4:2031: AC_CACHE_VAL is expanded from...
../../lib/autoconf/general.m4:2052: AC_CACHE_CHECK is expanded from...
m4/attributes.m4:87: CC_CHECK_LDFLAGS is expanded from...
m4/attributes.m4:104: CC_NOUNDEFINED is expanded from...
configure.ac:17: the top level
configure.ac:17: warning: AC_LANG_CONFTEST: no AC_LANG_SOURCE call detected in body
../../lib/autoconf/lang.m4:193: AC_LANG_CONFTEST is expanded from...
../../lib/autoconf/general.m4:2661: _AC_LINK_IFELSE is expanded from...
../../lib/autoconf/general.m4:2678: AC_LINK_IFELSE is expanded from...
../../lib/m4sugar/m4sh.m4:639: AS_IF is expanded from...
../../lib/autoconf/general.m4:2031: AC_CACHE_VAL is expanded from...
../../lib/autoconf/general.m4:2052: AC_CACHE_CHECK is expanded from...
m4/attributes.m4:87: CC_CHECK_LDFLAGS is expanded from...
m4/attributes.m4:104: CC_NOUNDEFINED is expanded from...
configure.ac:17: the top level
configure.ac:17: warning: AC_LANG_CONFTEST: no AC_LANG_SOURCE call detected in body
../../lib/autoconf/lang.m4:193: AC_LANG_CONFTEST is expanded from...
../../lib/autoconf/general.m4:2661: _AC_LINK_IFELSE is expanded from...
../../lib/autoconf/general.m4:2678: AC_LINK_IFELSE is expanded from...
../../lib/m4sugar/m4sh.m4:639: AS_IF is expanded from...
../../lib/autoconf/general.m4:2031: AC_CACHE_VAL is expanded from...
../../lib/autoconf/general.m4:2052: AC_CACHE_CHECK is expanded from...
m4/attributes.m4:87: CC_CHECK_LDFLAGS is expanded from...
m4/attributes.m4:104: CC_NOUNDEFINED is expanded from...
configure.ac:17: the top level
configure.ac:11: installing './compile'
/bin/bash ./config.status --recheck
running CONFIG_SHELL=/bin/bash /bin/bash ./configure --no-create --no-recursion
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/home/marina711/tmp/alsa-plugins-1.0.28/missing: Unknown '--is-lightweight' option
Try '/home/marina711/tmp/alsa-plugins-1.0.28/missing --help' for more information
configure: WARNING: 'missing' script is too old or missing
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether make supports nested variables... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking whether gcc understands -c and -o together... yes
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
checking for JACK... yes
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
checking for plugins version... 1.0.28
checking that generated files are newer than configure... done
configure: creating ./config.status

Plugin directory: /usr/lib/alsa-lib
ALSA_CFLAGS: -I/usr/include/alsa 
ALSA_LIBS: -lasound 
JACK plugin:        yes
  JACK_CFLAGS: 
  JACK_LIBS: -ljack -lpthread 
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
 /bin/bash ./config.status
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
(CDPATH="${ZSH_VERSION+.}:" && cd . && autoheader)
configure.ac:17: warning: AC_LANG_CONFTEST: no AC_LANG_SOURCE call detected in body
../../lib/autoconf/lang.m4:193: AC_LANG_CONFTEST is expanded from...
../../lib/autoconf/general.m4:2661: _AC_LINK_IFELSE is expanded from...
../../lib/autoconf/general.m4:2678: AC_LINK_IFELSE is expanded from...
../../lib/m4sugar/m4sh.m4:639: AS_IF is expanded from...
../../lib/autoconf/general.m4:2031: AC_CACHE_VAL is expanded from...
../../lib/autoconf/general.m4:2052: AC_CACHE_CHECK is expanded from...
m4/attributes.m4:87: CC_CHECK_LDFLAGS is expanded from...
m4/attributes.m4:104: CC_NOUNDEFINED is expanded from...
configure.ac:17: the top level
rm -f stamp-h1
touch config.h.in
cd . && /bin/bash ./config.status config.h
config.status: creating config.h
config.status: config.h is unchanged
make  all-recursive
make[1]: Entering directory '/home/marina711/tmp/alsa-plugins-1.0.28'
Making all in oss
make[2]: Entering directory '/home/marina711/tmp/alsa-plugins-1.0.28/oss'
/bin/bash ../libtool  --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..    -Wall -g -I/usr/include/alsa  -g -O2 -MT ctl_oss.lo -MD -MP -MF .deps/ctl_oss.Tpo -c -o ctl_oss.lo ctl_oss.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -Wall -g -I/usr/include/alsa -g -O2 -MT ctl_oss.lo -MD -MP -MF .deps/ctl_oss.Tpo -c ctl_oss.c  -fPIC -DPIC -o .libs/ctl_oss.o
mv -f .deps/ctl_oss.Tpo .deps/ctl_oss.Plo
/bin/bash ../libtool  --tag=CC   --mode=link gcc -Wall -g -I/usr/include/alsa  -g -O2 -module -avoid-version -export-dynamic -no-undefined -Wl,--no-undefined  -o libasound_module_ctl_oss.la -rpath /usr/lib/alsa-lib ctl_oss.lo -lasound  -lasound 
libtool: link: gcc -shared  -fPIC -DPIC  .libs/ctl_oss.o   -lasound  -O2 -Wl,--no-undefined   -Wl,-soname -Wl,libasound_module_ctl_oss.so -o .libs/libasound_module_ctl_oss.so
libtool: link: ( cd ".libs" && rm -f "libasound_module_ctl_oss.la" && ln -s "../libasound_module_ctl_oss.la" "libasound_module_ctl_oss.la" )
/bin/bash ../libtool  --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..    -Wall -g -I/usr/include/alsa  -g -O2 -MT pcm_oss.lo -MD -MP -MF .deps/pcm_oss.Tpo -c -o pcm_oss.lo pcm_oss.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -Wall -g -I/usr/include/alsa -g -O2 -MT pcm_oss.lo -MD -MP -MF .deps/pcm_oss.Tpo -c pcm_oss.c  -fPIC -DPIC -o .libs/pcm_oss.o
pcm_oss.c: In function 'oss_start':
pcm_oss.c:100:4: warning: ignoring return value of 'read', declared with attribute warn_unused_result [-Wunused-result]
    read(oss->fd, &tmp, 0);
    ^
mv -f .deps/pcm_oss.Tpo .deps/pcm_oss.Plo
/bin/bash ../libtool  --tag=CC   --mode=link gcc -Wall -g -I/usr/include/alsa  -g -O2 -module -avoid-version -export-dynamic -no-undefined -Wl,--no-undefined  -o libasound_module_pcm_oss.la -rpath /usr/lib/alsa-lib pcm_oss.lo -lasound  -lasound 
libtool: link: gcc -shared  -fPIC -DPIC  .libs/pcm_oss.o   -lasound  -O2 -Wl,--no-undefined   -Wl,-soname -Wl,libasound_module_pcm_oss.so -o .libs/libasound_module_pcm_oss.so
libtool: link: ( cd ".libs" && rm -f "libasound_module_pcm_oss.la" && ln -s "../libasound_module_pcm_oss.la" "libasound_module_pcm_oss.la" )
make[2]: Leaving directory '/home/marina711/tmp/alsa-plugins-1.0.28/oss'
Making all in mix
make[2]: Entering directory '/home/marina711/tmp/alsa-plugins-1.0.28/mix'
/bin/bash ../libtool  --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..    -Wall -g -I/usr/include/alsa  -g -O2 -MT pcm_upmix.lo -MD -MP -MF .deps/pcm_upmix.Tpo -c -o pcm_upmix.lo pcm_upmix.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -Wall -g -I/usr/include/alsa -g -O2 -MT pcm_upmix.lo -MD -MP -MF .deps/pcm_upmix.Tpo -c pcm_upmix.c  -fPIC -DPIC -o .libs/pcm_upmix.o
mv -f .deps/pcm_upmix.Tpo .deps/pcm_upmix.Plo
/bin/bash ../libtool  --tag=CC   --mode=link gcc -Wall -g -I/usr/include/alsa  -g -O2 -module -avoid-version -export-dynamic -no-undefined -Wl,--no-undefined  -o libasound_module_pcm_upmix.la -rpath /usr/lib/alsa-lib pcm_upmix.lo -lasound  -lasound 
libtool: link: gcc -shared  -fPIC -DPIC  .libs/pcm_upmix.o   -lasound  -O2 -Wl,--no-undefined   -Wl,-soname -Wl,libasound_module_pcm_upmix.so -o .libs/libasound_module_pcm_upmix.so
libtool: link: ( cd ".libs" && rm -f "libasound_module_pcm_upmix.la" && ln -s "../libasound_module_pcm_upmix.la" "libasound_module_pcm_upmix.la" )
/bin/bash ../libtool  --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..    -Wall -g -I/usr/include/alsa  -g -O2 -MT pcm_vdownmix.lo -MD -MP -MF .deps/pcm_vdownmix.Tpo -c -o pcm_vdownmix.lo pcm_vdownmix.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -Wall -g -I/usr/include/alsa -g -O2 -MT pcm_vdownmix.lo -MD -MP -MF .deps/pcm_vdownmix.Tpo -c pcm_vdownmix.c  -fPIC -DPIC -o .libs/pcm_vdownmix.o
mv -f .deps/pcm_vdownmix.Tpo .deps/pcm_vdownmix.Plo
/bin/bash ../libtool  --tag=CC   --mode=link gcc -Wall -g -I/usr/include/alsa  -g -O2 -module -avoid-version -export-dynamic -no-undefined -Wl,--no-undefined  -o libasound_module_pcm_vdownmix.la -rpath /usr/lib/alsa-lib pcm_vdownmix.lo -lasound  -lasound 
libtool: link: gcc -shared  -fPIC -DPIC  .libs/pcm_vdownmix.o   -lasound  -O2 -Wl,--no-undefined   -Wl,-soname -Wl,libasound_module_pcm_vdownmix.so -o .libs/libasound_module_pcm_vdownmix.so
libtool: link: ( cd ".libs" && rm -f "libasound_module_pcm_vdownmix.la" && ln -s "../libasound_module_pcm_vdownmix.la" "libasound_module_pcm_vdownmix.la" )
make[2]: Leaving directory '/home/marina711/tmp/alsa-plugins-1.0.28/mix'
Making all in usb_stream
make[2]: Entering directory '/home/marina711/tmp/alsa-plugins-1.0.28/usb_stream'
/bin/bash ../libtool  --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..    -Wall -g -I/usr/include/alsa  -g -O2 -MT pcm_usb_stream.lo -MD -MP -MF .deps/pcm_usb_stream.Tpo -c -o pcm_usb_stream.lo pcm_usb_stream.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -Wall -g -I/usr/include/alsa -g -O2 -MT pcm_usb_stream.lo -MD -MP -MF .deps/pcm_usb_stream.Tpo -c pcm_usb_stream.c  -fPIC -DPIC -o .libs/pcm_usb_stream.o
mv -f .deps/pcm_usb_stream.Tpo .deps/pcm_usb_stream.Plo
/bin/bash ../libtool  --tag=CC   --mode=link gcc -Wall -g -I/usr/include/alsa  -g -O2 -module -avoid-version -export-dynamic -Wl,--no-undefined  -o libasound_module_pcm_usb_stream.la -rpath /usr/lib/alsa-lib pcm_usb_stream.lo -lasound  -lasound 
libtool: link: gcc -shared  -fPIC -DPIC  .libs/pcm_usb_stream.o   -lasound  -O2 -Wl,--no-undefined   -Wl,-soname -Wl,libasound_module_pcm_usb_stream.so -o .libs/libasound_module_pcm_usb_stream.so
libtool: link: ( cd ".libs" && rm -f "libasound_module_pcm_usb_stream.la" && ln -s "../libasound_module_pcm_usb_stream.la" "libasound_module_pcm_usb_stream.la" )
make[2]: Leaving directory '/home/marina711/tmp/alsa-plugins-1.0.28/usb_stream'
Making all in arcam-av
make[2]: Entering directory '/home/marina711/tmp/alsa-plugins-1.0.28/arcam-av'
/bin/bash ../libtool  --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..    -Wall -g -I/usr/include/alsa  -g -O2 -MT ctl_arcam_av.lo -MD -MP -MF .deps/ctl_arcam_av.Tpo -c -o ctl_arcam_av.lo ctl_arcam_av.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -Wall -g -I/usr/include/alsa -g -O2 -MT ctl_arcam_av.lo -MD -MP -MF .deps/ctl_arcam_av.Tpo -c ctl_arcam_av.c  -fPIC -DPIC -o .libs/ctl_arcam_av.o
mv -f .deps/ctl_arcam_av.Tpo .deps/ctl_arcam_av.Plo
/bin/bash ../libtool  --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..    -Wall -g -I/usr/include/alsa  -g -O2 -MT arcam_av.lo -MD -MP -MF .deps/arcam_av.Tpo -c -o arcam_av.lo arcam_av.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -Wall -g -I/usr/include/alsa -g -O2 -MT arcam_av.lo -MD -MP -MF .deps/arcam_av.Tpo -c arcam_av.c  -fPIC -DPIC -o .libs/arcam_av.o
mv -f .deps/arcam_av.Tpo .deps/arcam_av.Plo
/bin/bash ../libtool  --tag=CC   --mode=link gcc -Wall -g -I/usr/include/alsa  -g -O2 -module -avoid-version -export-dynamic -no-undefined  -o libasound_module_ctl_arcam_av.la -rpath /usr/lib/alsa-lib ctl_arcam_av.lo arcam_av.lo -lasound  -lasound 
libtool: link: gcc -shared  -fPIC -DPIC  .libs/ctl_arcam_av.o .libs/arcam_av.o   -lasound  -O2   -Wl,-soname -Wl,libasound_module_ctl_arcam_av.so -o .libs/libasound_module_ctl_arcam_av.so
libtool: link: ( cd ".libs" && rm -f "libasound_module_ctl_arcam_av.la" && ln -s "../libasound_module_ctl_arcam_av.la" "libasound_module_ctl_arcam_av.la" )
make[2]: Leaving directory '/home/marina711/tmp/alsa-plugins-1.0.28/arcam-av'
Making all in doc
make[2]: Entering directory '/home/marina711/tmp/alsa-plugins-1.0.28/doc'
make[2]: Nothing to be done for 'all'.
make[2]: Leaving directory '/home/marina711/tmp/alsa-plugins-1.0.28/doc'
Making all in jack
make[2]: Entering directory '/home/marina711/tmp/alsa-plugins-1.0.28/jack'
/bin/bash ../libtool  --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..    -Wall -g -I/usr/include/alsa   -g -O2 -MT pcm_jack.lo -MD -MP -MF .deps/pcm_jack.Tpo -c -o pcm_jack.lo pcm_jack.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -Wall -g -I/usr/include/alsa -g -O2 -MT pcm_jack.lo -MD -MP -MF .deps/pcm_jack.Tpo -c pcm_jack.c  -fPIC -DPIC -o .libs/pcm_jack.o
pcm_jack.c: In function 'pcm_poll_unblock_check':
pcm_jack.c:83:3: warning: ignoring return value of 'write', declared with attribute warn_unused_result [-Wunused-result]
   write(jack->fd, &buf, 1);
   ^
mv -f .deps/pcm_jack.Tpo .deps/pcm_jack.Plo
/bin/bash ../libtool  --tag=CC   --mode=link gcc -Wall -g -I/usr/include/alsa   -g -O2 -module -avoid-version -export-dynamic -no-undefined -Wl,--no-undefined  -o libasound_module_pcm_jack.la -rpath /usr/lib/alsa-lib pcm_jack.lo -lasound  -ljack -lpthread  -lasound 
libtool: link: gcc -shared  -fPIC -DPIC  .libs/pcm_jack.o   -ljack -lpthread -lasound  -O2 -Wl,--no-undefined   -Wl,-soname -Wl,libasound_module_pcm_jack.so -o .libs/libasound_module_pcm_jack.so
libtool: link: ( cd ".libs" && rm -f "libasound_module_pcm_jack.la" && ln -s "../libasound_module_pcm_jack.la" "libasound_module_pcm_jack.la" )
make[2]: Leaving directory '/home/marina711/tmp/alsa-plugins-1.0.28/jack'
Making all in pulse
make[2]: Entering directory '/home/marina711/tmp/alsa-plugins-1.0.28/pulse'
/bin/bash ../libtool  --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..    -Wall -g -I/usr/include/alsa   -D_REENTRANT  -D_GNU_SOURCE -g -O2 -MT conf_pulse.lo -MD -MP -MF .deps/conf_pulse.Tpo -c -o conf_pulse.lo conf_pulse.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -Wall -g -I/usr/include/alsa -D_REENTRANT -D_GNU_SOURCE -g -O2 -MT conf_pulse.lo -MD -MP -MF .deps/conf_pulse.Tpo -c conf_pulse.c  -fPIC -DPIC -o .libs/conf_pulse.o
mv -f .deps/conf_pulse.Tpo .deps/conf_pulse.Plo
/bin/bash ../libtool  --tag=CC   --mode=link gcc -Wall -g -I/usr/include/alsa   -D_REENTRANT  -D_GNU_SOURCE -g -O2 -module -avoid-version -export-dynamic -no-undefined -Wl,--no-undefined  -o libasound_module_conf_pulse.la -rpath /usr/lib/alsa-lib conf_pulse.lo -lasound   -lpulse  -lasound 
libtool: link: gcc -shared  -fPIC -DPIC  .libs/conf_pulse.o   -lpulse -lasound  -O2 -Wl,--no-undefined   -Wl,-soname -Wl,libasound_module_conf_pulse.so -o .libs/libasound_module_conf_pulse.so
libtool: link: ( cd ".libs" && rm -f "libasound_module_conf_pulse.la" && ln -s "../libasound_module_conf_pulse.la" "libasound_module_conf_pulse.la" )
/bin/bash ../libtool  --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..    -Wall -g -I/usr/include/alsa   -D_REENTRANT  -D_GNU_SOURCE -g -O2 -MT ctl_pulse.lo -MD -MP -MF .deps/ctl_pulse.Tpo -c -o ctl_pulse.lo ctl_pulse.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -Wall -g -I/usr/include/alsa -D_REENTRANT -D_GNU_SOURCE -g -O2 -MT ctl_pulse.lo -MD -MP -MF .deps/ctl_pulse.Tpo -c ctl_pulse.c  -fPIC -DPIC -o .libs/ctl_pulse.o
mv -f .deps/ctl_pulse.Tpo .deps/ctl_pulse.Plo
/bin/bash ../libtool  --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..    -Wall -g -I/usr/include/alsa   -D_REENTRANT  -D_GNU_SOURCE -g -O2 -MT pulse.lo -MD -MP -MF .deps/pulse.Tpo -c -o pulse.lo pulse.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -Wall -g -I/usr/include/alsa -D_REENTRANT -D_GNU_SOURCE -g -O2 -MT pulse.lo -MD -MP -MF .deps/pulse.Tpo -c pulse.c  -fPIC -DPIC -o .libs/pulse.o
pulse.c: In function 'pulse_poll_activate':
pulse.c:255:2: warning: ignoring return value of 'write', declared with attribute warn_unused_result [-Wunused-result]
  write(p->thread_fd, &x, 1);
  ^
mv -f .deps/pulse.Tpo .deps/pulse.Plo
/bin/bash ../libtool  --tag=CC   --mode=link gcc -Wall -g -I/usr/include/alsa   -D_REENTRANT  -D_GNU_SOURCE -g -O2 -module -avoid-version -export-dynamic -no-undefined -Wl,--no-undefined  -o libasound_module_ctl_pulse.la -rpath /usr/lib/alsa-lib ctl_pulse.lo pulse.lo -lasound   -lpulse  -lasound 
libtool: link: gcc -shared  -fPIC -DPIC  .libs/ctl_pulse.o .libs/pulse.o   -lpulse -lasound  -O2 -Wl,--no-undefined   -Wl,-soname -Wl,libasound_module_ctl_pulse.so -o .libs/libasound_module_ctl_pulse.so
libtool: link: ( cd ".libs" && rm -f "libasound_module_ctl_pulse.la" && ln -s "../libasound_module_ctl_pulse.la" "libasound_module_ctl_pulse.la" )
/bin/bash ../libtool  --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..    -Wall -g -I/usr/include/alsa   -D_REENTRANT  -D_GNU_SOURCE -g -O2 -MT pcm_pulse.lo -MD -MP -MF .deps/pcm_pulse.Tpo -c -o pcm_pulse.lo pcm_pulse.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -Wall -g -I/usr/include/alsa -D_REENTRANT -D_GNU_SOURCE -g -O2 -MT pcm_pulse.lo -MD -MP -MF .deps/pcm_pulse.Tpo -c pcm_pulse.c  -fPIC -DPIC -o .libs/pcm_pulse.o
mv -f .deps/pcm_pulse.Tpo .deps/pcm_pulse.Plo
/bin/bash ../libtool  --tag=CC   --mode=link gcc -Wall -g -I/usr/include/alsa   -D_REENTRANT  -D_GNU_SOURCE -g -O2 -module -avoid-version -export-dynamic -no-undefined -Wl,--no-undefined  -o libasound_module_pcm_pulse.la -rpath /usr/lib/alsa-lib pcm_pulse.lo pulse.lo -lasound   -lpulse  -lasound 
libtool: link: gcc -shared  -fPIC -DPIC  .libs/pcm_pulse.o .libs/pulse.o   -lpulse -lasound  -O2 -Wl,--no-undefined   -Wl,-soname -Wl,libasound_module_pcm_pulse.so -o .libs/libasound_module_pcm_pulse.so
libtool: link: ( cd ".libs" && rm -f "libasound_module_pcm_pulse.la" && ln -s "../libasound_module_pcm_pulse.la" "libasound_module_pcm_pulse.la" )
make[2]: Leaving directory '/home/marina711/tmp/alsa-plugins-1.0.28/pulse'
Making all in rate
make[2]: Entering directory '/home/marina711/tmp/alsa-plugins-1.0.28/rate'
/bin/bash ../libtool  --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..    -Wall -g -I/usr/include/alsa   -g -O2 -MT rate_samplerate.lo -MD -MP -MF .deps/rate_samplerate.Tpo -c -o rate_samplerate.lo rate_samplerate.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -Wall -g -I/usr/include/alsa -g -O2 -MT rate_samplerate.lo -MD -MP -MF .deps/rate_samplerate.Tpo -c rate_samplerate.c  -fPIC -DPIC -o .libs/rate_samplerate.o
mv -f .deps/rate_samplerate.Tpo .deps/rate_samplerate.Plo
/bin/bash ../libtool  --tag=CC   --mode=link gcc -Wall -g -I/usr/include/alsa   -g -O2 -module -avoid-version -export-dynamic -no-undefined -Wl,--no-undefined  -o libasound_module_rate_samplerate.la -rpath /usr/lib/alsa-lib rate_samplerate.lo -lasound  -lsamplerate  -lasound 
libtool: link: gcc -shared  -fPIC -DPIC  .libs/rate_samplerate.o   -lsamplerate -lasound  -O2 -Wl,--no-undefined   -Wl,-soname -Wl,libasound_module_rate_samplerate.so -o .libs/libasound_module_rate_samplerate.so
libtool: link: ( cd ".libs" && rm -f "libasound_module_rate_samplerate.la" && ln -s "../libasound_module_rate_samplerate.la" "libasound_module_rate_samplerate.la" )
make[2]: Leaving directory '/home/marina711/tmp/alsa-plugins-1.0.28/rate'
Making all in a52
make[2]: Entering directory '/home/marina711/tmp/alsa-plugins-1.0.28/a52'
/bin/bash ../libtool  --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..    -Wall -g -I/usr/include/alsa -DAVCODEC_HEADER="<libavcodec/avcodec.h>" -g -O2 -MT pcm_a52.lo -MD -MP -MF .deps/pcm_a52.Tpo -c -o pcm_a52.lo pcm_a52.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -Wall -g -I/usr/include/alsa "-DAVCODEC_HEADER=<libavcodec/avcodec.h>" -g -O2 -MT pcm_a52.lo -MD -MP -MF .deps/pcm_a52.Tpo -c pcm_a52.c  -fPIC -DPIC -o .libs/pcm_a52.o
pcm_a52.c: In function 'a52_free':
pcm_a52.c:510:2: warning: 'avcodec_free_frame' is deprecated (declared at /usr/include/libavcodec/avcodec.h:3220) [-Wdeprecated-declarations]
  avcodec_free_frame(&rec->frame);
  ^
pcm_a52.c: In function 'alloc_input_buffer':
pcm_a52.c:554:2: warning: 'avcodec_alloc_frame' is deprecated (declared at /usr/include/libavcodec/avcodec.h:3195) [-Wdeprecated-declarations]
  rec->frame = avcodec_alloc_frame();
  ^
mv -f .deps/pcm_a52.Tpo .deps/pcm_a52.Plo
/bin/bash ../libtool  --tag=CC   --mode=link gcc -Wall -g -I/usr/include/alsa -DAVCODEC_HEADER="<libavcodec/avcodec.h>" -g -O2 -module -avoid-version -export-dynamic -no-undefined -Wl,--no-undefined  -o libasound_module_pcm_a52.la -rpath /usr/lib/alsa-lib pcm_a52.lo -lasound  -lavcodec -lavutil  -lasound 
libtool: link: gcc -shared  -fPIC -DPIC  .libs/pcm_a52.o   -lavcodec -lavutil -lasound  -O2 -Wl,--no-undefined   -Wl,-soname -Wl,libasound_module_pcm_a52.so -o .libs/libasound_module_pcm_a52.so
libtool: link: ( cd ".libs" && rm -f "libasound_module_pcm_a52.la" && ln -s "../libasound_module_pcm_a52.la" "libasound_module_pcm_a52.la" )
make[2]: Leaving directory '/home/marina711/tmp/alsa-plugins-1.0.28/a52'
Making all in rate-lavc
make[2]: Entering directory '/home/marina711/tmp/alsa-plugins-1.0.28/rate-lavc'
/bin/bash ../libtool  --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..    -Wall -g -I/usr/include/alsa -DAVCODEC_HEADER="<libavcodec/avcodec.h>" -g -O2 -MT rate_lavcrate.lo -MD -MP -MF .deps/rate_lavcrate.Tpo -c -o rate_lavcrate.lo rate_lavcrate.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -Wall -g -I/usr/include/alsa "-DAVCODEC_HEADER=<libavcodec/avcodec.h>" -g -O2 -MT rate_lavcrate.lo -MD -MP -MF .deps/rate_lavcrate.Tpo -c rate_lavcrate.c  -fPIC -DPIC -o .libs/rate_lavcrate.o
rate_lavcrate.c: In function 'pcm_src_free':
rate_lavcrate.c:70:3: warning: implicit declaration of function 'av_resample_close' [-Wimplicit-function-declaration]
   av_resample_close(rate->context);
   ^
rate_lavcrate.c: In function 'pcm_src_init':
rate_lavcrate.c:96:3: warning: implicit declaration of function 'av_resample_init' [-Wimplicit-function-declaration]
   rate->context = av_resample_init(info->out.rate, info->in.rate,
   ^
rate_lavcrate.c:96:17: warning: assignment makes pointer from integer without a cast
   rate->context = av_resample_init(info->out.rate, info->in.rate,
                 ^
rate_lavcrate.c: In function 'pcm_src_convert_s16':
rate_lavcrate.c:186:3: warning: implicit declaration of function 'av_resample' [-Wimplicit-function-declaration]
   ret = av_resample(rate->context, rate->out[i],
   ^
rate_lavcrate.c:194:2: warning: implicit declaration of function 'av_resample_compensate' [-Wimplicit-function-declaration]
  av_resample_compensate(rate->context,
  ^
mv -f .deps/rate_lavcrate.Tpo .deps/rate_lavcrate.Plo
/bin/bash ../libtool  --tag=CC   --mode=link gcc -Wall -g -I/usr/include/alsa -DAVCODEC_HEADER="<libavcodec/avcodec.h>" -g -O2 -module -avoid-version -export-dynamic -no-undefined -Wl,--no-undefined  -o libasound_module_rate_lavcrate.la -rpath /usr/lib/alsa-lib rate_lavcrate.lo -lasound  -lavcodec -lavutil  -lasound 
libtool: link: gcc -shared  -fPIC -DPIC  .libs/rate_lavcrate.o   -lavcodec -lavutil -lasound  -O2 -Wl,--no-undefined   -Wl,-soname -Wl,libasound_module_rate_lavcrate.so -o .libs/libasound_module_rate_lavcrate.so
.libs/rate_lavcrate.o: In function `pcm_src_free':
/home/marina711/tmp/alsa-plugins-1.0.28/rate-lavc/rate_lavcrate.c:70: undefined reference to `av_resample_close'
.libs/rate_lavcrate.o: In function `pcm_src_init':
/home/marina711/tmp/alsa-plugins-1.0.28/rate-lavc/rate_lavcrate.c:96: undefined reference to `av_resample_init'
.libs/rate_lavcrate.o: In function `pcm_src_convert_s16':
/home/marina711/tmp/alsa-plugins-1.0.28/rate-lavc/rate_lavcrate.c:186: undefined reference to `av_resample'
/home/marina711/tmp/alsa-plugins-1.0.28/rate-lavc/rate_lavcrate.c:194: undefined reference to `av_resample_compensate'
/home/marina711/tmp/alsa-plugins-1.0.28/rate-lavc/rate_lavcrate.c:194: undefined reference to `av_resample_compensate'
collect2: error: ld returned 1 exit status
Makefile:412: recipe for target 'libasound_module_rate_lavcrate.la' failed
make[2]: *** [libasound_module_rate_lavcrate.la] Error 1
make[2]: Leaving directory '/home/marina711/tmp/alsa-plugins-1.0.28/rate-lavc'
Makefile:418: recipe for target 'all-recursive' failed
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory '/home/marina711/tmp/alsa-plugins-1.0.28'
Makefile:349: recipe for target 'all' failed
make: *** [all] Error 2
marina711@marina711:~/tmp/alsa-plugins-1.0.28$ 
```

I'm just an advanced user, so I'm stuck there. Can someone please help?

Best regards
Marina711

---

### Post by Yellow Pasque on 2015-08-16
Do you have libavresample-dev package installed?

---

### Post by marina071170 on 2015-08-16
Yes it's installed.
[ATTACH=CONFIG]263877[/ATTACH]

---

### Post by tgalati4 on 2015-08-16
Let's try a few things.  Install *mplayer2* then configure it to run SPDIF:

```
sudo apt-get install mplayer2
```

Add the following line to .mplayer/config:

```
cd
cd .mplayer
nano config
```

Add:

> ao=alsa:device=spdif

Control-O (enter) to save the file, Control-X to quit.

Play a music file with your digital connection hooked up (either optical TOSLink or coaxial RF--orange connector)

```
mplayer anymusicfile.mp3
```

Sorry, ignore this post, this was meant for another thread with a digital out issue.

---

### Post by mc4man on 2015-08-16
you seem to be attempting to make the "rate-lavc"plugin, (Making all in rate-lavc).  Here in 15.04 it does "rate-lavr",  (Making all in rate-lavr) & the build works.
Did your libasound2 source get the "libav10.patch' patch?
Are you using some other source than repo version for libav11 or FFmpeg headers?

(edit: the rate-lavc in _it's current state_ is not build-able, even with alsa-plugins-1.0.29 source, certainly not with 1.0.28 source

---

### Post by marina071170 on 2015-08-17
> **mc4man said:**
> you seem to be attempting to make the "rate-lavc"plugin, (Making all in rate-lavc).  Here in 15.04 it does "rate-lavr",  (Making all in rate-lavr) & the build works.
Did your libasound2 source get the "libav10.patch' patch?
I don't know. If this patch is installed through automatic update, it should be installed. But I can't check now, I'm on a business trip for the rest of the week.
> **mc4man said:**
> Are you using some other source than repo version for libav11 or FFmpeg headers?
I don't think so. Everything should be genuine ubuntu.
> **mc4man said:**
> (edit: the rate-lavc in _it's current state_ is not build-able, even with alsa-plugins-1.0.29 source, certainly not with 1.0.28 source
Is it possible to build it without? And how?

---

### Post by mc4man on 2015-08-17
> **marina071170 said:**
> I don't know. If this patch is installed through automatic update, it should be installed. But I can't check now, I'm on a business trip for the rest of the week.

The patch should have been applied if you got the source with 
```
apt-get source libasound2-plugins
```
If it wasn't then you'll need to apply manually, patch is in repo source > debian > patches

---

### Post by Yellow Pasque on 2015-08-17
> If this patch is installed through automatic update, it should be installed.
It's not a package; it's a patch. It should automatically be applied to the alsa-plugins source when you use the 'apt-get source' command.
So let's back up a bit.
```
cd ~/tmp
rm -r alsa-plugins*
apt-get source alsa-plugins
```
Please show the output of the last command.

EDIT: I'm not sure why, but I didn't see the last post where mc4man basically said the same thing. Sorry for redundancy

---

### Post by marina071170 on 2015-08-23
> **Temüjin said:**
> It's not a package; it's a patch. It should automatically be applied to the alsa-plugins source when you use the 'apt-get source' command.
So let's back up a bit.
```
cd ~/tmp
rm -r alsa-plugins*
apt-get source alsa-plugins
```
Please show the output of the last command.

EDIT: I'm not sure why, but I didn't see the last post where mc4man basically said the same thing. Sorry for redundancy
Here is the output of the last command. I'm German so most of the messages are as well:```
marina711@marina711:~/tmp$ apt-get source alsa-plugins
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
HINWEIS: »alsa-plugins«-Paketierung wird betreut im »Bzr«-Versionsverwaltungssystem auf:
http://bazaar.launchpad.net/~ubuntu-audio-dev/alsa-plugins/ubuntu
Bitte verwenden Sie:
bzr branch http://bazaar.launchpad.net/~ubuntu-audio-dev/alsa-plugins/ubuntu
um die neuesten (möglicherweise noch unveröffentlichten) Aktualisierungen
für das Paket abzurufen.
Es müssen 385 kB an Quellarchiven heruntergeladen werden.
Holen: 1 http://archive.ubuntu.com/ubuntu/ vivid/main alsa-plugins 1.0.28-1ubuntu2 (dsc) [1.780 B]
Holen: 2 http://archive.ubuntu.com/ubuntu/ vivid/main alsa-plugins 1.0.28-1ubuntu2 (tar) [366 kB]
Holen: 3 http://archive.ubuntu.com/ubuntu/ vivid/main alsa-plugins 1.0.28-1ubuntu2 (diff) [17,1 kB]
Es wurden 385 kB in 0 s geholt (747 kB/s).
gpgv: Unterschrift vom Di 25 Nov 2014 23:31:57 CET mittels DSA-Schlüssel ID 9111FB35
gpgv: Unterschrift kann nicht geprüft werden: Öffentlicher Schlüssel nicht gefunden
dpkg-source: Warnung: Fehler beim Überprüfen der Signatur von ./alsa-plugins_1.0.28-1ubuntu2.dsc
dpkg-source: Information: alsa-plugins wird nach alsa-plugins-1.0.28 extrahiert
dpkg-source: Information: alsa-plugins_1.0.28.orig.tar.bz2 wird entpackt
dpkg-source: Information: alsa-plugins_1.0.28-1ubuntu2.debian.tar.xz wird entpackt
dpkg-source: Information: arcam-av_uses_pthreads.patch wird angewandt
dpkg-source: Information: libav10.patch wird angewandt
```
But from what Ican read in the last two lines is that there are two patches being applied: *arcam-av_uses_pthreads.patch* and [I]libav10.patch

[/I]I will give it a try and see what happens now

---

### Post by marina071170 on 2015-08-23
Looks like it worked this time. No more compiling errors.

Thanks a lot!

---

