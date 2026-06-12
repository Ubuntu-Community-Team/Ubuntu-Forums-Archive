---
title: "xmms-wavpack for 64 bit.....   got the 32-bit and would like...."
date: 2011-04-11
forum: Multimedia Software
---

### Post by shantiq on 2011-04-11
...to turn it so that it can be used on 64-bit setup with natty


any workaround/ways of modifying the package?


attached


thanx for all clever suggestions

---

### Post by Yellow Pasque on 2011-04-11
The file you attached is unbuilt source, so what happens when you try and build it? (i.e. post build log).

---

### Post by shantiq on 2011-04-11
hi Temujin    


i have a copy of   libwavpack.so

in   /home/shantiq/.xmms/Plugins


and in ```
/usr/lib
```   ```
/usr/lib32
```  also

```
/usr/lib/xmms/Input
``` which is the one where it should be normally



==================================================================


build log goes like this    i remember i had the same problem with 32-bit but could be fixed

./configure goes perfect


then on ```
make
``` you get this

```
shantiq@shantiq:~$ cd Downloads
shantiq@shantiq:~/Downloads$ cd xmms-wavpack-1.0.2
shantiq@shantiq:~/Downloads/xmms-wavpack-1.0.2$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for gcc... gcc
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
checking for a BSD-compatible install... /usr/bin/install -c
checking for ANSI C header files... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking wchar.h usability... yes
checking wchar.h presence... yes
checking for wchar.h... yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for an ANSI C-conforming const... yes
checking for off_t... yes
checking for size_t... yes
checking for xmms-config... /usr/bin/xmms-config
checking for gawk... (cached) gawk
checking for XMMS - version >= 1.2.10... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GTK... yes
checking for GLIB... yes
checking wavpack/wavpack.h usability... yes
checking wavpack/wavpack.h presence... yes
checking for wavpack/wavpack.h... yes
checking for WavpackGetVersion in -lwavpack... yes
checking iconv.h usability... yes
checking iconv.h presence... yes
checking for iconv.h... yes
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking for old style FreeBSD -pthread flag... no
checking for pthread_attr_init in -lpthread... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/config.h
config.status: src/config.h is unchanged
config.status: executing depfiles commands
 xmms-wavpack 1.0.2 configured successfully.
shantiq@shantiq:~/Downloads/xmms-wavpack-1.0.2$ make
Making all in src
make[1]: Entering directory `/home/shantiq/Downloads/xmms-wavpack-1.0.2/src'
make  all-am
make[2]: Entering directory `/home/shantiq/Downloads/xmms-wavpack-1.0.2/src'
/bin/bash ../libtool --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I/usr/include/glib-1.2 -I/usr/lib/glib/include   -I/usr/include/xmms -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include   -DVERSION=\"1.0.2\"   -fPIC -DTAGS -g -O2 -O3 -fomit-frame-pointer -MT libwavpack_la-equalizer.lo -MD -MP -MF .deps/libwavpack_la-equalizer.Tpo -c -o libwavpack_la-equalizer.lo `test -f 'equalizer.cpp' || echo './'`equalizer.cpp
 g++ -DHAVE_CONFIG_H -I. -I/usr/include/glib-1.2 -I/usr/lib/glib/include -I/usr/include/xmms -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -DVERSION=\"1.0.2\" -fPIC -DTAGS -g -O2 -O3 -fomit-frame-pointer -MT libwavpack_la-equalizer.lo -MD -MP -MF .deps/libwavpack_la-equalizer.Tpo -c equalizer.cpp  -fPIC -DPIC -o .libs/libwavpack_la-equalizer.o
mv -f .deps/libwavpack_la-equalizer.Tpo .deps/libwavpack_la-equalizer.Plo
/bin/bash ../libtool --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I/usr/include/glib-1.2 -I/usr/lib/glib/include   -I/usr/include/xmms -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include   -DVERSION=\"1.0.2\"   -fPIC -DTAGS -g -O2 -O3 -fomit-frame-pointer -MT libwavpack_la-libwavpack.lo -MD -MP -MF .deps/libwavpack_la-libwavpack.Tpo -c -o libwavpack_la-libwavpack.lo `test -f 'libwavpack.cpp' || echo './'`libwavpack.cpp
 g++ -DHAVE_CONFIG_H -I. -I/usr/include/glib-1.2 -I/usr/lib/glib/include -I/usr/include/xmms -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -DVERSION=\"1.0.2\" -fPIC -DTAGS -g -O2 -O3 -fomit-frame-pointer -MT libwavpack_la-libwavpack.lo -MD -MP -MF .deps/libwavpack_la-libwavpack.Tpo -c libwavpack.cpp  -fPIC -DPIC -o .libs/libwavpack_la-libwavpack.o
libwavpack.cpp: In function 'void update_tag(ape_tag*, char*)':
libwavpack.cpp:248:31: warning: deprecated conversion from string constant to 'gchar*'
libwavpack.cpp:248:31: warning: deprecated conversion from string constant to 'gchar*'
libwavpack.cpp:293:31: warning: deprecated conversion from string constant to 'gchar*'
libwavpack.cpp:293:31: warning: deprecated conversion from string constant to 'gchar*'
libwavpack.cpp: In function 'void delete_tag(char*)':
libwavpack.cpp:312:31: warning: deprecated conversion from string constant to 'gchar*'
libwavpack.cpp:312:31: warning: deprecated conversion from string constant to 'gchar*'
libwavpack.cpp:325:31: warning: deprecated conversion from string constant to 'gchar*'
libwavpack.cpp:325:31: warning: deprecated conversion from string constant to 'gchar*'
libwavpack.cpp: In function 'char* generate_title(const char*, WavpackContext*)':
libwavpack.cpp:455:20: warning: deprecated conversion from string constant to 'gchar*'
libwavpack.cpp: In function 'void wv_load_config()':
libwavpack.cpp:558:49: warning: deprecated conversion from string constant to 'gchar*'
libwavpack.cpp:558:49: warning: deprecated conversion from string constant to 'gchar*'
libwavpack.cpp:560:50: warning: deprecated conversion from string constant to 'gchar*'
libwavpack.cpp:560:50: warning: deprecated conversion from string constant to 'gchar*'
libwavpack.cpp:561:76: warning: deprecated conversion from string constant to 'gchar*'
libwavpack.cpp:561:76: warning: deprecated conversion from string constant to 'gchar*'
libwavpack.cpp:562:75: warning: deprecated conversion from string constant to 'gchar*'
libwavpack.cpp:562:75: warning: deprecated conversion from string constant to 'gchar*'
mv -f .deps/libwavpack_la-libwavpack.Tpo .deps/libwavpack_la-libwavpack.Plo
/bin/bash ../libtool --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I/usr/include/glib-1.2 -I/usr/lib/glib/include   -I/usr/include/xmms -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include   -DVERSION=\"1.0.2\"   -fPIC -DTAGS -g -O2 -O3 -fomit-frame-pointer -MT libwavpack_la-ui.lo -MD -MP -MF .deps/libwavpack_la-ui.Tpo -c -o libwavpack_la-ui.lo `test -f 'ui.cpp' || echo './'`ui.cpp
 g++ -DHAVE_CONFIG_H -I. -I/usr/include/glib-1.2 -I/usr/lib/glib/include -I/usr/include/xmms -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -DVERSION=\"1.0.2\" -fPIC -DTAGS -g -O2 -O3 -fomit-frame-pointer -MT libwavpack_la-ui.lo -MD -MP -MF .deps/libwavpack_la-ui.Tpo -c ui.cpp  -fPIC -DPIC -o .libs/libwavpack_la-ui.o
ui.cpp: In function 'void wv_about_box()':
ui.cpp:58:52: warning: deprecated conversion from string constant to 'gchar*'
ui.cpp:58:52: warning: deprecated conversion from string constant to 'gchar*'
ui.cpp: In function 'void wv_file_info_box(char*)':
ui.cpp:389:72: warning: deprecated conversion from string constant to 'char*'
ui.cpp:390:105: warning: deprecated conversion from string constant to 'char*'
ui.cpp:391:78: warning: deprecated conversion from string constant to 'char*'
ui.cpp:392:94: warning: deprecated conversion from string constant to 'char*'
ui.cpp:393:77: warning: deprecated conversion from string constant to 'char*'
ui.cpp:394:69: warning: deprecated conversion from string constant to 'char*'
ui.cpp:395:82: warning: deprecated conversion from string constant to 'char*'
ui.cpp:397:65: warning: deprecated conversion from string constant to 'char*'
ui.cpp:398:65: warning: deprecated conversion from string constant to 'char*'
ui.cpp:399:65: warning: deprecated conversion from string constant to 'char*'
ui.cpp:400:65: warning: deprecated conversion from string constant to 'char*'
ui.cpp: In function 'void wv_configurewin_ok(GtkWidget*, void*)':
ui.cpp:440:49: warning: deprecated conversion from string constant to 'gchar*'
ui.cpp:440:49: warning: deprecated conversion from string constant to 'gchar*'
ui.cpp:442:50: warning: deprecated conversion from string constant to 'gchar*'
ui.cpp:442:50: warning: deprecated conversion from string constant to 'gchar*'
ui.cpp:443:76: warning: deprecated conversion from string constant to 'gchar*'
ui.cpp:443:76: warning: deprecated conversion from string constant to 'gchar*'
ui.cpp:444:75: warning: deprecated conversion from string constant to 'gchar*'
ui.cpp:444:75: warning: deprecated conversion from string constant to 'gchar*'
mv -f .deps/libwavpack_la-ui.Tpo .deps/libwavpack_la-ui.Plo
/bin/bash ../libtool --tag=CXX   --mode=link g++ -fPIC -DTAGS -g -O2 -O3 -fomit-frame-pointer -avoid-version  -o libwavpack.la -rpath /usr/lib/xmms/Input libwavpack_la-equalizer.lo libwavpack_la-libwavpack.lo libwavpack_la-ui.lo -lpthread -lglib   -L/usr/lib -lgtk -lgdk -rdynamic -lgmodule -lglib -ldl -lXi -lXext -lX11 -lm -lxmms -lgtk -lgdk -lXi -lXext -lX11 -lm -lglib   -lwavpack 
rm -fr  .libs/libwavpack.la .libs/libwavpack.lai .libs/libwavpack.so .libs/libwavpack.soT
g++ -shared -nostdlib /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/../../../crti.o /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/crtbeginS.o  .libs/libwavpack_la-equalizer.o .libs/libwavpack_la-libwavpack.o .libs/libwavpack_la-ui.o  -Wl,--rpath -Wl,/home/shantiq/Downloads/xmms-wavpack-1.0.2/src/.libs -Wl,--rpath -Wl,/usr/lib/xmms/Input -lpthread -L/usr/lib /usr/lib/libgmodule.so -ldl /usr/lib/libxmms.so /usr/lib/libgtk.so /usr/lib/libgdk.so -lXi -lXext -lX11 /usr/lib/libglib.so /home/shantiq/Downloads/xmms-wavpack-1.0.2/src/.libs/libwavpack.so -L/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2 -L/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/../../.. -L/usr/lib/x86_64-linux-gnu -lstdc++ -lm -lc -lgcc_s /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/crtendS.o /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/../../../crtn.o  -Wl,-soname -Wl,libwavpack.so -o .libs/libwavpack.so
g++: /home/shantiq/Downloads/xmms-wavpack-1.0.2/src/.libs/libwavpack.so: No such file or directory
make[2]: *** [libwavpack.la] Error 1
make[2]: Leaving directory `/home/shantiq/Downloads/xmms-wavpack-1.0.2/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/shantiq/Downloads/xmms-wavpack-1.0.2/src'
make: *** [all-recursive] Error 1
shantiq@shantiq:~/Downloads/xmms-wavpack-1.0.2$ make
Making all in src
make[1]: Entering directory `/home/shantiq/Downloads/xmms-wavpack-1.0.2/src'
make  all-am
make[2]: Entering directory `/home/shantiq/Downloads/xmms-wavpack-1.0.2/src'
/bin/bash ../libtool --tag=CXX   --mode=link g++ -fPIC -DTAGS -g -O2 -O3 -fomit-frame-pointer -avoid-version  -o libwavpack.la -rpath /usr/lib/xmms/Input libwavpack_la-equalizer.lo libwavpack_la-libwavpack.lo libwavpack_la-ui.lo -lpthread -lglib   -L/usr/lib -lgtk -lgdk -rdynamic -lgmodule -lglib -ldl -lXi -lXext -lX11 -lm -lxmms -lgtk -lgdk -lXi -lXext -lX11 -lm -lglib   -lwavpack 
rm -fr  .libs/libwavpack.so
g++ -shared -nostdlib /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/../../../crti.o /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/crtbeginS.o  .libs/libwavpack_la-equalizer.o .libs/libwavpack_la-libwavpack.o .libs/libwavpack_la-ui.o  -Wl,--rpath -Wl,/home/shantiq/Downloads/xmms-wavpack-1.0.2/src/.libs -Wl,--rpath -Wl,/usr/lib/xmms/Input -lpthread -L/usr/lib /usr/lib/libgmodule.so -ldl /usr/lib/libxmms.so /usr/lib/libgtk.so /usr/lib/libgdk.so -lXi -lXext -lX11 /usr/lib/libglib.so /home/shantiq/Downloads/xmms-wavpack-1.0.2/src/.libs/libwavpack.so -L/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2 -L/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/../../.. -L/usr/lib/x86_64-linux-gnu -lstdc++ -lm -lc -lgcc_s /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/crtendS.o /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/../../../crtn.o  -Wl,-soname -Wl,libwavpack.so -o .libs/libwavpack.so
g++: /home/shantiq/Downloads/xmms-wavpack-1.0.2/src/.libs/libwavpack.so: No such file or directory
make[2]: *** [libwavpack.la] Error 1
make[2]: Leaving directory `/home/shantiq/Downloads/xmms-wavpack-1.0.2/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/shantiq/Downloads/xmms-wavpack-1.0.2/src'
make: *** [all-recursive] Error 1
shantiq@shantiq:~/Downloads/xmms-wavpack-1.0.2$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... ^Z
[1]+  Stopped                 ./configure
shantiq@shantiq:~/Downloads/xmms-wavpack-1.0.2$ make
Making all in src
make[1]: Entering directory `/home/shantiq/Downloads/xmms-wavpack-1.0.2/src'
make  all-am
make[2]: Entering directory `/home/shantiq/Downloads/xmms-wavpack-1.0.2/src'
/bin/bash ../libtool --tag=CXX   --mode=link g++ -fPIC -DTAGS -g -O2 -O3 -fomit-frame-pointer -avoid-version  -o libwavpack.la -rpath /usr/lib/xmms/Input libwavpack_la-equalizer.lo libwavpack_la-libwavpack.lo libwavpack_la-ui.lo -lpthread -lglib   -L/usr/lib -lgtk -lgdk -rdynamic -lgmodule -lglib -ldl -lXi -lXext -lX11 -lm -lxmms -lgtk -lgdk -lXi -lXext -lX11 -lm -lglib   -lwavpack 
rm -fr  .libs/libwavpack.so
g++ -shared -nostdlib /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/../../../crti.o /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/crtbeginS.o  .libs/libwavpack_la-equalizer.o .libs/libwavpack_la-libwavpack.o .libs/libwavpack_la-ui.o  -Wl,--rpath -Wl,/home/shantiq/Downloads/xmms-wavpack-1.0.2/src/.libs -Wl,--rpath -Wl,/usr/lib/xmms/Input -lpthread -L/usr/lib /usr/lib/libgmodule.so -ldl /usr/lib/libxmms.so /usr/lib/libgtk.so /usr/lib/libgdk.so -lXi -lXext -lX11 /usr/lib/libglib.so /home/shantiq/Downloads/xmms-wavpack-1.0.2/src/.libs/libwavpack.so -L/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2 -L/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/../../.. -L/usr/lib/x86_64-linux-gnu -lstdc++ -lm -lc -lgcc_s /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/crtendS.o /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/../../../crtn.o  -Wl,-soname -Wl,libwavpack.so -o .libs/libwavpack.so
g++: /home/shantiq/Downloads/xmms-wavpack-1.0.2/src/.libs/libwavpack.so: No such file or directory
make[2]: *** [libwavpack.la] Error 1
make[2]: Leaving directory `/home/shantiq/Downloads/xmms-wavpack-1.0.2/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/shantiq/Downloads/xmms-wavpack-1.0.2/src'
make: *** [all-recursive] Error 1
shantiq@shantiq:~/Downloads/xmms-wavpack-1.0.2$ cd
shantiq@shantiq:~$ clear

shantiq@shantiq:~$ cd xmms-wavpack-1.0.2
shantiq@shantiq:~/xmms-wavpack-1.0.2$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for gcc... gcc
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
checking for a BSD-compatible install... /usr/bin/install -c
checking for ANSI C header files... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking wchar.h usability... yes
checking wchar.h presence... yes
checking for wchar.h... yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for an ANSI C-conforming const... yes
checking for off_t... yes
checking for size_t... yes
checking for xmms-config... /usr/bin/xmms-config
checking for gawk... (cached) gawk
checking for XMMS - version >= 1.2.10... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GTK... yes
checking for GLIB... yes
checking wavpack/wavpack.h usability... yes
checking wavpack/wavpack.h presence... yes
checking for wavpack/wavpack.h... yes
checking for WavpackGetVersion in -lwavpack... yes
checking iconv.h usability... yes
checking iconv.h presence... yes
checking for iconv.h... yes
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking for old style FreeBSD -pthread flag... no
checking for pthread_attr_init in -lpthread... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/config.h
config.status: src/config.h is unchanged
config.status: executing depfiles commands
 xmms-wavpack 1.0.2 configured successfully.
shantiq@shantiq:~/xmms-wavpack-1.0.2$ make
Making all in src
make[1]: Entering directory `/home/shantiq/xmms-wavpack-1.0.2/src'
make  all-am
make[2]: Entering directory `/home/shantiq/xmms-wavpack-1.0.2/src'
/bin/bash ../libtool --tag=CXX   --mode=link g++ -fPIC -DTAGS -g -O2 -O3 -fomit-frame-pointer -avoid-version  -o libwavpack.la -rpath /usr/lib/xmms/Input libwavpack_la-equalizer.lo libwavpack_la-libwavpack.lo libwavpack_la-ui.lo -lpthread -lglib   -L/usr/lib -lgtk -lgdk -rdynamic -lgmodule -lglib -ldl -lXi -lXext -lX11 -lm -lxmms -lgtk -lgdk -lXi -lXext -lX11 -lm -lglib   -lwavpack 
rm -fr  .libs/libwavpack.so
g++ -shared -nostdlib /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/../../../crti.o /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/crtbeginS.o  .libs/libwavpack_la-equalizer.o .libs/libwavpack_la-libwavpack.o .libs/libwavpack_la-ui.o  -Wl,--rpath -Wl,/home/shantiq/xmms-wavpack-1.0.2/src/.libs -Wl,--rpath -Wl,/usr/lib/xmms/Input -lpthread -L/usr/lib /usr/lib/libgmodule.so -ldl /usr/lib/libxmms.so /usr/lib/libgtk.so /usr/lib/libgdk.so -lXi -lXext -lX11 /usr/lib/libglib.so /home/shantiq/xmms-wavpack-1.0.2/src/.libs/libwavpack.so -L/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2 -L/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/../../.. -L/usr/lib/x86_64-linux-gnu -lstdc++ -lm -lc -lgcc_s /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/crtendS.o /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/../../../crtn.o  -Wl,-soname -Wl,libwavpack.so -o .libs/libwavpack.so
g++: [COLOR="Red"]/home/shantiq/xmms-wavpack-1.0.2/src/.libs/libwavpack.so: No such file or directory
make[2]: *** [libwavpack.la] Error 1
make[2]: Leaving directory `/home/shantiq/xmms-wavpack-1.0.2/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/shantiq/xmms-wavpack-1.0.2/src'
make: *** [all-recursive] Error 1[/COLOR]
shantiq@shantiq:~/xmms-wavpack-1.0.2$ 

 
```


now on 32-bit you could find libwavpack.so in src which you can too here and copy it to .lib   and i think i  remember it worked fine     here when i run make again it disappears from the .lib folder i have just added it to and returns the same error



when i load from command line i get this

```
shantiq@shantiq:~/xmms-wavpack-1.0.2$ xmms

Gtk-WARNING **: Failed to load module "libcanberra-gtk-module.so": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory
/home/shantiq/.xmms/Plugins/libaac.so: wrong ELF class: ELFCLASS32
**[COLOR="DarkRed"]/home/shantiq/.xmms/Plugins/libwavpack.so: wrong ELF class: ELFCLASS32[/COLOR]**
/home/shantiq/.xmms/Plugins/libxmms-tta.so: wrong ELF class: ELFCLASS32
libfaad.so.0: cannot open shared object file: No such file or directory
/home/shantiq/.xmms/Plugins/libwma.so: wrong ELF class: ELFCLASS32
/home/shantiq/.xmms/Plugins/libffmpeg.so: wrong ELF class: ELFCLASS32
/home/shantiq/.xmms/Plugins/libmpc.so: wrong ELF class: ELFCLASS32
/home/shantiq/.xmms/Plugins/libmacinput.so: wrong ELF class: ELFCLASS32
/usr/lib/xmms/Input/libaac.so: wrong ELF class: ELFCLASS32
/usr/lib/xmms/Input/libwavpack.so: wrong ELF class: ELFCLASS32
/usr/lib/xmms/Input/libxmms-tta.so: wrong ELF class: ELFCLASS32
libfaad.so.0: cannot open shared object file: No such file or directory
/usr/lib/xmms/Input/libwma.so: wrong ELF class: ELFCLASS32
/usr/lib/xmms/Input/libffmpeg.so: wrong ELF class: ELFCLASS32
/usr/lib/xmms/Input/libmpc.so: wrong ELF class: ELFCLASS32
/usr/lib/xmms/Input/libmacinput.so: wrong ELF class: ELFCLASS32
Message: device: default

```

---

### Post by Ibidem on 2011-05-05
UPDATE: Newer version available!
Another way of getting it to build:
libtoolize
aclocal
automake
autoconf
./configure
make

(Thanks to the FSF for a build system that will error out if you do any of the 6 steps out of order, or have the "wrong" version.
I'll stick with make for anything I do.)

And... it builds.  (at least on i386)
You DO need libwavpack-dev, it seems

UPDATE:
[http://www.wavpack.com/downloads.html](http://www.wavpack.com/downloads.html) has 1.0.3, which has these advantages:
1.  tar.bz2 file
2.  has the copyright notices--GPL2, distributable
3.  actually builds cleanly

---

### Post by Ibidem on 2011-05-05
OK--
```
Accepted:
 OK: xmms-wavpack_1.0.3.orig.tar.gz
 OK: xmms-wavpack_1.0.3-1.diff.gz
 OK: xmms-wavpack_1.0.3-1.dsc
     -> Component: main Section: sound  

Format: 1.8
Date: Wed, 04 May 2011 22:03:50 -0700
Source: xmms-wavpack
Binary: xmms-wavpack
Architecture: source
Version: 1.0.3-1
Distribution: lucid
Urgency: low
Maintainer: Isaac <ibid_ag@lavabit.com>
Changed-By: Ibidem <ibid_ag@lavabit.com>
Description: 
xmms-wavpack - <insert up to 60 chars description>
Changes: 
xmms-wavpack (1.0.3-1) lucid; urgency=low

  * Initial release
Checksums-Sha1: 
90b2ab80ac9cc20ec2d37535fa9d65f7a19140d8 1400 xmms-wavpack_1.0.3-1.dsc
500a52efff149f3c3a780e0487a5c431dc0ecd45 338836 xmms-wavpack_1.0.3.orig.tar.gz
14ee0969d4f87999e4d46fbc59a63b827f5aa087 1917 xmms-wavpack_1.0.3-1.diff.gz
Checksums-Sha256: 
9e306b0efba1a10fc59e6bd5c82e4c6e198488f7999f4bc27495200668a0d0b1 1400 xmms-wavpack_1.0.3-1.dsc
5db149499f3c53ea8af7ed93ff5478e2ca975fcf0bd2f805a03a9efb42ebc040 338836 xmms-wavpack_1.0.3.orig.tar.gz
14f318121e35f2dfbce3c5b5a02e00bbcd483eb3d4e4e9abc7386fc08af49819 1917 xmms-wavpack_1.0.3-1.diff.gz
Files: 
4ba55b1505f00db3dbab6635f551714f 1400 sound extra xmms-wavpack_1.0.3-1.dsc
a4e2dd96655a7b8f52783dccef78f503 338836 sound extra xmms-wavpack_1.0.3.orig.tar.gz
526e5819f55b7d8763db223106b44934 1917 sound extra xmms-wavpack_1.0.3-1.diff.gz
```
i386 builds in 5 hours, amd64 builds in 8.

---

### Post by shantiq on 2011-05-05
hi there ibidem if you have built the 64-bit version any chance you could attach it here?   thanx   shan

---

