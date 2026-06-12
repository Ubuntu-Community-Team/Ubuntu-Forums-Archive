---
title: "Help installing gmpc-tagedit-0.20.0?"
date: 2018-06-27
forum: Multimedia Software
---

### Post by bvargo on 2018-06-27
Hopefully this is the right forum... I've been trying to install this today... I had to get a few other things installed to get to where I'm at now (see below) which is no errors with ./configure

```
Log started: 2018-06-27  13:48:05Selecting previously unselected package gob2.
(Reading database ... 277614 files and directories currently installed.)
Preparing to unpack .../gob2_2.0.20-1_amd64.deb ...
Unpacking gob2 (2.0.20-1) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up gob2 (2.0.20-1) ...
Log ended: 2018-06-27  13:48:05


Log started: 2018-06-27  13:50:45
(Reading database ... 277628 files and directories currently installed.)
Removing python-configobj (5.0.6-2) ...
Removing python-pyparsing (2.0.3+dfsg1-1ubuntu0.1) ...
Log ended: 2018-06-27  13:50:46


Log started: 2018-06-27  13:56:55
Selecting previously unselected package cmake-data.
(Reading database ... 277609 files and directories currently installed.)
Preparing to unpack .../cmake-data_3.5.1-1ubuntu3_all.deb ...
Unpacking cmake-data (3.5.1-1ubuntu3) ...
Selecting previously unselected package libjsoncpp1:amd64.
Preparing to unpack .../libjsoncpp1_1.7.2-1_amd64.deb ...
Unpacking libjsoncpp1:amd64 (1.7.2-1) ...
Selecting previously unselected package cmake.
Preparing to unpack .../cmake_3.5.1-1ubuntu3_amd64.deb ...
Unpacking cmake (3.5.1-1ubuntu3) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Setting up cmake-data (3.5.1-1ubuntu3) ...
Setting up libjsoncpp1:amd64 (1.7.2-1) ...
Setting up cmake (3.5.1-1ubuntu3) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Log ended: 2018-06-27  13:57:00


Log started: 2018-06-27  14:12:24
Selecting previously unselected package libmpdclient-dev.
(Reading database ... 279666 files and directories currently installed.)
Preparing to unpack .../libmpdclient-dev_2.9-1ubuntu1_amd64.deb ...
Unpacking libmpdclient-dev (2.9-1ubuntu1) ...
Setting up libmpdclient-dev (2.9-1ubuntu1) ...
Log ended: 2018-06-27  14:12:25


Log started: 2018-06-27  14:13:47
Selecting previously unselected package libmpd1-dbg.
(Reading database ... 279708 files and directories currently installed.)
Preparing to unpack .../libmpd1-dbg_0.20.0-1.3_amd64.deb ...
Unpacking libmpd1-dbg (0.20.0-1.3) ...
Setting up libmpd1-dbg (0.20.0-1.3) ...
Log ended: 2018-06-27  14:13:48


Log started: 2018-06-27  14:18:28
Selecting previously unselected package gmpc-dbg.
(Reading database ... 279710 files and directories currently installed.)
Preparing to unpack .../gmpc-dbg_11.8.16-9_amd64.deb ...
Unpacking gmpc-dbg (11.8.16-9) ...
Selecting previously unselected package gmpc-plugins-dbg.
Preparing to unpack .../gmpc-plugins-dbg_11.8.16-2_amd64.deb ...
Unpacking gmpc-plugins-dbg (11.8.16-2) ...
Setting up gmpc-dbg (11.8.16-9) ...
Setting up gmpc-plugins-dbg (11.8.16-2) ...
Log ended: 2018-06-27  14:18:29

```

however, when I go to execute "make" I get the following error:
```

:~/bin/gmpc-tagedit-0.20.0$ make
make  all-recursive
make[1]: Entering directory '/home/------/bin/gmpc-tagedit-0.20.0'
Making all in src
make[2]: Entering directory '/home/------/bin/gmpc-tagedit-0.20.0/src'
make  all-am
make[3]: Entering directory '/home/------/bin/gmpc-tagedit-0.20.0/src'
/bin/bash ../libtool  --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..    -pthread -I/usr/local/include/taglib -I/usr/include/libxml2 -I/usr/include/gmpc -I/usr/include/gtk-2.0 -I/usr/lib/x86_64-linux-gnu/gtk-2.0/include -I/usr/include/gio-unix-2.0/ -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/libpng12 -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/libpng12 -I/usr/include/pango-1.0 -I/usr/include/harfbuzz -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libmpd-1.0/ -Wall -Wmissing-declarations -g -O2 -MT gmpctageditplugin_la-plugin.lo -MD -MP -MF .deps/gmpctageditplugin_la-plugin.Tpo -c -o gmpctageditplugin_la-plugin.lo `test -f 'plugin.c' || echo './'`plugin.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -pthread -I/usr/local/include/taglib -I/usr/include/libxml2 -I/usr/include/gmpc -I/usr/include/gtk-2.0 -I/usr/lib/x86_64-linux-gnu/gtk-2.0/include -I/usr/include/gio-unix-2.0/ -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/libpng12 -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/libpng12 -I/usr/include/pango-1.0 -I/usr/include/harfbuzz -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libmpd-1.0/ -Wall -Wmissing-declarations -g -O2 -MT gmpctageditplugin_la-plugin.lo -MD -MP -MF .deps/gmpctageditplugin_la-plugin.Tpo -c plugin.c  -fPIC -DPIC -o .libs/gmpctageditplugin_la-plugin.o
In file included from /usr/include/string.h:630:0,
                 from plugin.c:20:
**/usr/include/libmpd-1.0/libmpd/libmpd-internal.h:210:10: error: expected identifier or ‘(’ before ‘__extension__’**
** char *   strndup     (const char *s, size_t n);**
**          ^**
Makefile:361: recipe for target 'gmpctageditplugin_la-plugin.lo' failed
make[3]: *** [gmpctageditplugin_la-plugin.lo] Error 1
make[3]: Leaving directory '/home/------/bin/gmpc-tagedit-0.20.0/src'
Makefile:262: recipe for target 'all' failed
make[2]: *** [all] Error 2
make[2]: Leaving directory '/home/------/bin/gmpc-tagedit-0.20.0/src'
Makefile:316: recipe for target 'all-recursive' failed
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory '/home/------/bin/gmpc-tagedit-0.20.0'
Makefile:245: recipe for target 'all' failed
make: *** [all] Error 2

```

and so I'm stuck with this error and don't know where to go...if it helps, libmpd-internal.h is attached.  

I'd really appreciate it if someone would be able to point me in the right direction.

---

### Post by mc4man on 2018-06-27
Petty old stuff but,
Maybe try removing that taglib build in /usr/local & install the repo libtagc0-dev package.
Then clean your gmpc-tagedit source (make clean) and run a ./configure & make again.

---

### Post by bvargo on 2018-06-27
So the following?
```
:/usr/local/include$ sudo rm -R taglib/
:~/bin/gmpc-tagedit-0.20-0$ sudo apt install libtagc0-dev
:~/bin/gmpc-tagedit-0.20-0$ make clean
:~/bin/gmpc-tagedit-0.20-0$ ./configure
:~/bin/gmpc-tagedit-0.20-0$ make
:~/bin/gmpc-tagedit-0.20-0$ make install

```

I guess mpd is old but I haven't found anything I like using better.

---

### Post by mc4man on 2018-06-28
By old meant the tagedit plugin, doesn't seem to have had any activity for many years. I think you should be able to compile it as above, whether it actually works , no idea.
(- you'd need to install as root (sudo)

---

### Post by bvargo on 2018-06-28
Hmm... yeah, I looked and it said on Wikipedia that mpd was last updated in the last month or so.  I guess tagedit is not maintained anymore though.  Anyway, just for completeness, I tried the above steps and:

```

**:/usr/local/include$ ls**
taglib

**:/usr/local/include$ ****sudo**** rm -R ****taglib**
[B]
:/usr/local/include$ ll[/B]
total 8
drwxr-xr-x  2 root root 4096 Jun 28 10:16 ./
drwxr-xr-x 11 root root 4096 May 12 18:01 ../

**:/usr/local/include$ cd ~/bin/gmpc-****tagedit****-0.20.0/**
[B]
:~/bin/[/B]**gmpc****-****tagedit****-0.20.0$ ****sudo**** apt install libtagc0-****debv**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libtagc0-debv

**:~/bin/****gmpc****-****tagedit****-0.20.0$ ****sudo**** apt install libtagc0-dev**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  libtag1-dev
The following NEW packages will be installed:
  libtag1-dev libtagc0-dev
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 90.1 kB of archives.
After this operation, 755 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 libtag1-dev amd64 1.9.1-2.4ubuntu1 [76.8 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 libtagc0-dev amd64 1.9.1-2.4ubuntu1 [13.3 kB]
Fetched 90.1 kB in 0s (693 kB/s)        
Selecting previously unselected package libtag1-dev.
(Reading database ... 279741 files and directories currently installed.)
Preparing to unpack .../libtag1-dev_1.9.1-2.4ubuntu1_amd64.deb ...
Unpacking libtag1-dev (1.9.1-2.4ubuntu1) ...
Selecting previously unselected package libtagc0-dev.
Preparing to unpack .../libtagc0-dev_1.9.1-2.4ubuntu1_amd64.deb ...
Unpacking libtagc0-dev (1.9.1-2.4ubuntu1) ...
Setting up libtag1-dev (1.9.1-2.4ubuntu1) ...
Setting up libtagc0-dev (1.9.1-2.4ubuntu1) ...

**:~/bin/gmpc-tagedit-0.20.0$ make clean**
Making clean in po
make[1]: Entering directory '/home/------/bin/gmpc-tagedit-0.20.0/po'
rm -f *.pox gmpc-tagedit.pot *.old.po cat-id-tbl.tmp
rm -f .intltool-merge-cache
make[1]: Leaving directory '/home/------/bin/gmpc-tagedit-0.20.0/po'
Making clean in src
make[1]: Entering directory '/home/------/bin/gmpc-tagedit-0.20.0/src'
rm -rf .libs _libs
test -z "gmpctageditplugin.la" || rm -f gmpctageditplugin.la
rm -f "./so_locations"
rm -f *.o
rm -f *.lo
make[1]: Leaving directory '/home/------/bin/gmpc-tagedit-0.20.0/src'
Making clean in .
make[1]: Entering directory '/home/------/bin/gmpc-tagedit-0.20.0'
rm -rf .libs _libs
rm -f *.lo
make[1]: Leaving directory '/home/------/bin/gmpc-tagedit-0.20.0'
bvargo@gigabyte:~/bin/gmpc-tagedit-0.20.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
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
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
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
checking whether NLS is requested... yes
checking for intltool >= 0.21... 0.51.0 found
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for perl >= 5.8.1... 5.22.1
checking for XML::Parser... ok
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... (cached) /usr/bin/msgfmt
checking for xgettext... (cached) /usr/bin/xgettext
checking for catalogs to be installed...  bg bs de es fr it ja nb nl pl ro ru sv zh_CN
/usr/local
checking for gob2... /usr/bin/gob2
checking for gob-2 >= 2.0.10... ok
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for gmpctagedit... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating po/Makefile.in
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands

**:~/bin/gmpc-tagedit-0.20.0$ make**
make  all-recursive
make[1]: Entering directory '/home/------/bin/gmpc-tagedit-0.20.0'
Making all in src
make[2]: Entering directory '/home/------/bin/gmpc-tagedit-0.20.0/src'
make  all-am
make[3]: Entering directory '/home/------/bin/gmpc-tagedit-0.20.0/src'
/bin/bash ../libtool  --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..    -pthread -I/usr/local/include/taglib -I/usr/include/libxml2 -I/usr/include/gmpc -I/usr/include/gtk-2.0 -I/usr/lib/x86_64-linux-gnu/gtk-2.0/include -I/usr/include/gio-unix-2.0/ -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/libpng12 -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/libpng12 -I/usr/include/pango-1.0 -I/usr/include/harfbuzz -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libmpd-1.0/ -Wall -Wmissing-declarations -g -O2 -MT gmpctageditplugin_la-plugin.lo -MD -MP -MF .deps/gmpctageditplugin_la-plugin.Tpo -c -o gmpctageditplugin_la-plugin.lo `test -f 'plugin.c' || echo './'`plugin.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -pthread -I/usr/local/include/taglib -I/usr/include/libxml2 -I/usr/include/gmpc -I/usr/include/gtk-2.0 -I/usr/lib/x86_64-linux-gnu/gtk-2.0/include -I/usr/include/gio-unix-2.0/ -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/libpng12 -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/libpng12 -I/usr/include/pango-1.0 -I/usr/include/harfbuzz -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libmpd-1.0/ -Wall -Wmissing-declarations -g -O2 -MT gmpctageditplugin_la-plugin.lo -MD -MP -MF .deps/gmpctageditplugin_la-plugin.Tpo -c plugin.c  -fPIC -DPIC -o .libs/gmpctageditplugin_la-plugin.o
**plugin.c:30:19: fatal error: tag_c.h: No such file or directory**
**compilation terminated.**
Makefile:361: recipe for target 'gmpctageditplugin_la-plugin.lo' failed
make[3]: *** [gmpctageditplugin_la-plugin.lo] Error 1
make[3]: Leaving directory '/home/------/bin/gmpc-tagedit-0.20.0/src'
Makefile:262: recipe for target 'all' failed
make[2]: *** [all] Error 2
make[2]: Leaving directory '/home/------/bin/gmpc-tagedit-0.20.0/src'
Makefile:316: recipe for target 'all-recursive' failed
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory '/home/------/bin/gmpc-tagedit-0.20.0'
Makefile:245: recipe for target 'all' failed
make: *** [all] Error 2

```

---

### Post by mc4man on 2018-06-28
For whatever reason it's still linking to taglib in /usr/local (now fails on not finding it.
(- maybe the make clean is not totallly effective??

I'd suggest deleting current gmpc-tagedit-0.20.0 folder & extract new from gmpc-tagedit-0.20.0.tar.gz

Testing here works fine to build - (scroll right for blue highlights..
```
~/Downloads/gmpc-tagedit-0.20.0$ make
make  all-recursive
make[1]: Entering directory '/home/doug/Downloads/gmpc-tagedit-0.20.0'
Making all in src
make[2]: Entering directory '/home/doug/Downloads/gmpc-tagedit-0.20.0/src'
make  all-am
make[3]: Entering directory '/home/doug/Downloads/gmpc-tagedit-0.20.0/src'
/bin/bash ../libtool  --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..    -pthread -I/usr/include/libxml2 -I/usr/include/gmpc -I/usr/include/libmpd-1.0/ -I/usr/include/gtk-2.0 -I/usr/lib/x86_64-linux-gnu/gtk-2.0/include -I/usr/include/gio-unix-2.0/ -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/libpng16 -I/usr/include/pango-1.0 -I/usr/include/harfbuzz -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng16 -I/usr/include/freetype2 -I/usr/include/libpng16 [COLOR="#0000CD"]-I/usr/include/taglib [/COLOR]-Wall -Wmissing-declarations -g -O2 -MT gmpctageditplugin_la-plugin.lo -MD -MP -MF .deps/gmpctageditplugin_la-plugin.Tpo -c -o gmpctageditplugin_la-plugin.lo `test -f 'plugin.c' || echo './'`plugin.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -pthread -I/usr/include/libxml2 -I/usr/include/gmpc -I/usr/include/libmpd-1.0/ -I/usr/include/gtk-2.0 -I/usr/lib/x86_64-linux-gnu/gtk-2.0/include -I/usr/include/gio-unix-2.0/ -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/libpng16 -I/usr/include/pango-1.0 -I/usr/include/harfbuzz -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng16 -I/usr/include/freetype2 -I/usr/include/libpng16 [COLOR="#0000CD"]-I/usr/include/taglib[/COLOR] -Wall -Wmissing-declarations -g -O2 -MT gmpctageditplugin_la-plugin.lo -MD -MP -MF .deps/gmpctageditplugin_la-plugin.Tpo -c plugin.c  -fPIC -DPIC -o .libs/gmpctageditplugin_la-plugin.o
mv -f .deps/gmpctageditplugin_la-plugin.Tpo .deps/gmpctageditplugin_la-plugin.Plo
/bin/bash ../libtool  --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..    -pthread -I/usr/include/libxml2 -I/usr/include/gmpc -I/usr/include/libmpd-1.0/ -I/usr/include/gtk-2.0 -I/usr/lib/x86_64-linux-gnu/gtk-2.0/include -I/usr/include/gio-unix-2.0/ -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/libpng16 -I/usr/include/pango-1.0 -I/usr/include/harfbuzz -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng16 -I/usr/include/freetype2 -I/usr/include/libpng16[COLOR="#0000CD"] -I/usr/include/taglib [/COLOR]-Wall -Wmissing-declarations -g -O2 -MT gmpctageditplugin_la-gmpc-mpddata-model-tagedit.lo -MD -MP -MF .deps/gmpctageditplugin_la-gmpc-mpddata-model-tagedit.Tpo -c -o gmpctageditplugin_la-gmpc-mpddata-model-tagedit.lo `test -f 'gmpc-mpddata-model-tagedit.c' || echo './'`gmpc-mpddata-model-tagedit.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -pthread -I/usr/include/libxml2 -I/usr/include/gmpc -I/usr/include/libmpd-1.0/ -I/usr/include/gtk-2.0 -I/usr/lib/x86_64-linux-gnu/gtk-2.0/include -I/usr/include/gio-unix-2.0/ -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/libpng16 -I/usr/include/pango-1.0 -I/usr/include/harfbuzz -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng16 -I/usr/include/freetype2 -I/usr/include/libpng16 [COLOR="#0000CD"]-I/usr/include/taglib[/COLOR] -Wall -Wmissing-declarations -g -O2 -MT gmpctageditplugin_la-gmpc-mpddata-model-tagedit.lo -MD -MP -MF .deps/gmpctageditplugin_la-gmpc-mpddata-model-tagedit.Tpo -c gmpc-mpddata-model-tagedit.c  -fPIC -DPIC -o .libs/gmpctageditplugin_la-gmpc-mpddata-model-tagedit.o
gmpc-mpddata-model-tagedit.gob: In function &#8216;gmpc_mpddata_model_tagedit_new&#8217;:
gmpc-mpddata-model-tagedit.gob:45:16: warning: return from incompatible pointer type [-Wincompatible-pointer-types]
         return self;
                ^~~~
mv -f .deps/gmpctageditplugin_la-gmpc-mpddata-model-tagedit.Tpo .deps/gmpctageditplugin_la-gmpc-mpddata-model-tagedit.Plo
/bin/bash ../libtool --tag=CC   --mode=link gcc -pthread -I/usr/include/libxml2 -I/usr/include/gmpc -I/usr/include/libmpd-1.0/ -I/usr/include/gtk-2.0 -I/usr/lib/x86_64-linux-gnu/gtk-2.0/include -I/usr/include/gio-unix-2.0/ -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/libpng16 -I/usr/include/pango-1.0 -I/usr/include/harfbuzz -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng16 -I/usr/include/freetype2 -I/usr/include/libpng16 -I/usr/include/taglib -Wall -Wmissing-declarations -g -O2 -module -avoid-version   -o gmpctageditplugin.la -rpath /usr/local/lib/gmpc/plugins/ gmpctageditplugin_la-plugin.lo gmpctageditplugin_la-gmpc-mpddata-model-tagedit.lo -Wl,--export-dynamic -lgmodule-2.0 -pthread -lxml2 -lgthread-2.0 -pthread -lmpd -lgtk-x11-2.0 -lgdk-x11-2.0 -lpangocairo-1.0 -latk-1.0 -lcairo -lgdk_pixbuf-2.0 -lgio-2.0 -lpangoft2-1.0 -lpango-1.0 -lgobject-2.0 -lglib-2.0 -lfontconfig -lfreetype -ltag_c -ltag  
libtool: link: gcc -shared  .libs/gmpctageditplugin_la-plugin.o .libs/gmpctageditplugin_la-gmpc-mpddata-model-tagedit.o   -lgmodule-2.0 -lxml2 -lgthread-2.0 -lmpd -lgtk-x11-2.0 -lgdk-x11-2.0 -lpangocairo-1.0 -latk-1.0 -lcairo -lgdk_pixbuf-2.0 -lgio-2.0 -lpangoft2-1.0 -lpango-1.0 -lgobject-2.0 -lglib-2.0 -lfontconfig /usr/lib/x86_64-linux-gnu/libfreetype.so -ltag_c -ltag  -pthread -Wl,--export-dynamic -pthread -pthread   -pthread -Wl,-soname -Wl,gmpctageditplugin.so -o .libs/gmpctageditplugin.so
libtool: link: ( cd ".libs" && rm -f "gmpctageditplugin.la" && ln -s "../gmpctageditplugin.la" "gmpctageditplugin.la" )
make[3]: Leaving directory '/home/doug/Downloads/gmpc-tagedit-0.20.0/src'
make[2]: Leaving directory '/home/doug/Downloads/gmpc-tagedit-0.20.0/src'
Making all in po
make[2]: Entering directory '/home/doug/Downloads/gmpc-tagedit-0.20.0/po'
make[2]: Nothing to be done for 'all'.
make[2]: Leaving directory '/home/doug/Downloads/gmpc-tagedit-0.20.0/po'
make[2]: Entering directory '/home/doug/Downloads/gmpc-tagedit-0.20.0'
make[2]: Leaving directory '/home/doug/Downloads/gmpc-tagedit-0.20.0'
make[1]: Leaving directory '/home/doug/Downloads/gmpc-tagedit-0.20.0'
```

---

### Post by bvargo on 2018-06-29
Well...I tried a few different things...and now I'm rewarded with the same error I started with!
I removed the gmpc-tagedit-0.20.0 folder and re-extracted it.
I copied /usr/include/taglib to /usr/local/include/taglib.
make clean
./configure
make

```
:~/bin/gmpc-tagedit-0.20.0$ make
make  all-recursive
make[1]: Entering directory '/home/-----/bin/gmpc-tagedit-0.20.0'
Making all in src
make[2]: Entering directory '/home/-----/bin/gmpc-tagedit-0.20.0/src'
make  all-am
make[3]: Entering directory '/home/-----/bin/gmpc-tagedit-0.20.0/src'
/bin/bash ../libtool  --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..    -pthread -I/usr/local/include/taglib -I/usr/include/libxml2 -I/usr/include/gmpc -I/usr/include/gtk-2.0 -I/usr/lib/x86_64-linux-gnu/gtk-2.0/include -I/usr/include/gio-unix-2.0/ -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/libpng12 -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/libpng12 -I/usr/include/pango-1.0 -I/usr/include/harfbuzz -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libmpd-1.0/ -Wall -Wmissing-declarations -g -O2 -MT gmpctageditplugin_la-plugin.lo -MD -MP -MF .deps/gmpctageditplugin_la-plugin.Tpo -c -o gmpctageditplugin_la-plugin.lo `test -f 'plugin.c' || echo './'`plugin.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -pthread -I/usr/local/include/taglib -I/usr/include/libxml2 -I/usr/include/gmpc -I/usr/include/gtk-2.0 -I/usr/lib/x86_64-linux-gnu/gtk-2.0/include -I/usr/include/gio-unix-2.0/ -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/libpng12 -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/libpng12 -I/usr/include/pango-1.0 -I/usr/include/harfbuzz -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libmpd-1.0/ -Wall -Wmissing-declarations -g -O2 -MT gmpctageditplugin_la-plugin.lo -MD -MP -MF .deps/gmpctageditplugin_la-plugin.Tpo -c plugin.c  -fPIC -DPIC -o .libs/gmpctageditplugin_la-plugin.o
In file included from /usr/include/string.h:630:0,
                 from plugin.c:20:
**/usr/include/libmpd-1.0/libmpd/libmpd-internal.h:210:10: error: expected identifier or ‘(’ before ‘__extension__’**
** char *   strndup     (const char *s, size_t n);**
          ^
Makefile:361: recipe for target 'gmpctageditplugin_la-plugin.lo' failed
make[3]: *** [gmpctageditplugin_la-plugin.lo] Error 1
make[3]: Leaving directory '/home/-----/bin/gmpc-tagedit-0.20.0/src'
Makefile:262: recipe for target 'all' failed
make[2]: *** [all] Error 2
make[2]: Leaving directory '/home/-----/bin/gmpc-tagedit-0.20.0/src'
Makefile:316: recipe for target 'all-recursive' failed
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory '/home/-----/bin/gmpc-tagedit-0.20.0'
Makefile:245: recipe for target 'all' failed
make: *** [all] Error 2
```

Since I have no idea what I'm doing, copying /usr/include/taglib to /usr/local/include/taglib seems to have gotten around the missing file issue (i.e. I get the tag_c.h missing error if it isn't in /usr/local/include/taglib) but that's about it...I obviously lack the skill to hash out what the expected identifier error is and I assume I shouldn't be editing the source code of libmpd-internal.h.

Thanks again for the help.

---

### Post by bvargo on 2018-06-29
also... I just found this:
```
:/usr/local/bin$ lltotal 92
drwxr-xr-x  2 root root  4096 Jun 27 14:06 ./
drwxr-xr-x 11 root root  4096 May 12 18:01 ../
lrwxrwxrwx  1 root root    18 May 31 19:56 rambox -> /opt/Rambox/rambox*
-rwxr-xr-x  1 root root 19248 May 12 18:01 rrip_cli*
-rwxr-xr-x  1 root root 61180 May 12 18:01 rrip_gui*
-rwxr-xr-x  1 root root   614 Jun 27 13:57 taglib-config*


```

but moving taglib-config to taglib-config~ and starting with make clean; ./configure; make didn't change the error.


```
:/usr/local/bin$ cat taglib-config #!/bin/sh


usage()
{
    echo "usage: $0 [OPTIONS]"
cat << EOH


options:
    [--libs]
    [--cflags]
    [--version]
    [--prefix]
EOH
    exit 1;
}


prefix=/usr/local
exec_prefix=/usr/local
libdir=/usr/local/lib
includedir=/usr/local/include


flags=""


if test $# -eq 0 ; then
  usage
fi


while test $# -gt 0
do
  case $1 in
    --libs)
      flags="$flags -L$libdir -ltag"
      ;;
    --cflags)
      flags="$flags -I$includedir/taglib"
      ;;
    --version)
      echo 1.11.1
      ;;
    --prefix)
      echo $prefix
      ;;
    *)
      echo "$0: unknown option $1"
      echo
      usage
      ;;
  esac
  shift
done


if test -n "$flags"
then
  echo $flags
fi



```

---

### Post by mc4man on 2018-06-30
If you want this to work remove anything & everything concerning taglib from /usr/local/
If you've modified any other taglib files in /usr then undo.
Till then you're just going around in circles..

---

