---
title: "emerald window decorator does not work"
date: 2011-03-07
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by beew on 2011-03-07
It seems that emerald is not working on the classic desktop. I tried using the command emerald --replace in ccsm > Window Decoration but nothing changes. I have not tested this on Unity, have had enough troubles enabling the cube there, I don't expect it to work in Unity at this testing phase, but the classic desktop should work.

I am using alpha 3

---

### Post by hype on 2011-03-07
It actually seems like there is no emerald compatible with 0.9.x version of compiz. :(
 I frankly regret there isnt any alternative to a window decorator editor in latest Compiz.

---

### Post by beew on 2011-03-07
Well that sucks, wonder if it is possible to downgrade Compiz if I use the classical desktop.  I really don't like the gtk black solid theme, I find it incredibly unpolished and ugly. I can even tolerate Unity but at least give us a nice window decorator. Hopefully they will work out something else in  future releases.

---

### Post by BwackNinja on 2011-03-07
Actually, there is an emerald compatible that you can build from git, but it broke within the past couple days for me. I have a simple patch to make it build again. I can post it here if you want.

---

### Post by beew on 2011-03-07
> **BwackNinja said:**
> Actually, there is an emerald compatible that you can build from git, but it broke within the past couple days for me. I have a simple patch to make it build again. I can post it here if you want.

Please do, that would be great. I am sure others would want it too. :)

---

### Post by BwackNinja on 2011-03-07
-install the dependencies for emerald (not entirely sure about all of them, but you should need at least compiz-dev and libdecoration0-dev)
-download emeraldfix.txt (attached) and install emerald from git

```
git clone git://anongit.compiz.org/fusion/decorators/emerald
cd emerald
git checkout -b compiz++ origin/compiz++
patch -p1 < ../emeraldfix.txt      #set the path properly for where you put emeraldfix.txt
./configure --prefix=/usr/local
make
sudo make install
```

---

### Post by hype on 2011-03-08
Getting an error during make:

```
Making all in src
make[2]: entrant dans le répertoire « /media/data/downloads/apps/emerald/src »
gcc -DHAVE_CONFIG_H -I. -I.. -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/libdrm -I/usr/include/libwnck-1.0 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz   -I../include -DLOCALEDIR="\"/usr/share/locale"\" -DENGINE_DIR=\"/usr/lib/emerald/engines\"    -g -O2 -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/libdrm -I/usr/include/libwnck-1.0 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz   -MT main.o -MD -MP -MF .deps/main.Tpo -c -o main.o main.c
main.c: In function ‘update_window_decoration_size’:
main.c:3044:11: warning: assignment makes pointer from integer without a cast
main.c: In function ‘update_switcher_window’:
main.c:3242:9: warning: assignment makes pointer from integer without a cast
main.c:3291:11: warning: assignment makes pointer from integer without a cast
main.c: In function ‘main’:
main.c:5620:5: error: too few arguments to function ‘decor_set_dm_check_hint’
/usr/include/compiz/decoration.h:411:1: note: declared here
make[2]: *** [main.o] Erreur 1
make[2]: quittant le répertoire « /media/data/downloads/apps/emerald/src »
make[1]: *** [all-recursive] Erreur 1
make[1]: quittant le répertoire « /media/data/downloads/apps/emerald »
make: *** [all] Erreur 2

```

---

### Post by BwackNinja on 2011-03-08
ah, sorry I forgot that you need to check out the compiz++ branch of emerald, so after you do a git clone, and cd into that directory, you need to do a 'git checkout -b compiz++ origin/compiz++'

I updated my original post.

---

### Post by hype on 2011-03-08
Thanks for answer, but i get an error message:
```
git checkout -b compiz++ origin/compiz++
error: Your local changes to the following files would be overwritten by checkout:
	src/main.c
Please, commit your changes or stash them before you can switch branches.
Aborting
```

---

### Post by BwackNinja on 2011-03-08
that's because the patch affected src/main.c, try doing a:

patch -p1 -R < ../emeraldfix.txt

to reverse the patch, and run the git checkout again, patch again, and continue from there.

---

### Post by hype on 2011-03-08
Arghh...

```
lude -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/libdrm -I/usr/include/libwnck-1.0 -I/usr/include/startup-notification-1.0 -I/usr/include/compiz -o .libs/emerald main.o engine_loader.o -pthread -pthread  ../libengine/.libs/libemeraldengine.so -lwnck-1 /usr/lib/libgtk-x11-2.0.so /usr/lib/libgdk-x11-2.0.so /usr/lib/libatk-1.0.so /usr/lib/libgio-2.0.so /usr/lib/libpangoft2-1.0.so -lgdk_pixbuf-2.0 -lm /usr/lib/libfreetype.so -lfontconfig -ldecoration -lXrender -lX11 /usr/lib/libpangocairo-1.0.so /usr/lib/libpango-1.0.so /usr/lib/libcairo.so /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so /usr/lib/libgthread-2.0.so -lrt /usr/lib/libglib-2.0.so -pthread
/usr/bin/ld: engine_loader.o: undefined reference to symbol 'dlclose@@GLIBC_2.2.5'
/usr/bin/ld: note: 'dlclose@@GLIBC_2.2.5' is defined in DSO /lib64/libdl.so.2 so try adding it to the linker command line
/lib64/libdl.so.2: could not read symbols: Invalid operation
collect2: ld returned 1 exit status
make[2]: *** [emerald] Erreur 1
make[2]: quittant le répertoire « /media/data/downloads/apps/emerald/src »
make[1]: *** [all-recursive] Erreur 1
make[1]: quittant le répertoire « /media/data/downloads/apps/emerald »
make: *** [all] Erreur 2

```

Seems like i dont get the problem, except it may be related to the fact that i run 64bits version of natty.

---

### Post by mc4man on 2011-03-08
@ hype

Happens occasionally in natty with gcc-4.5 (DSO linking problems
either use gcc-4.4 or try 
```
./configure --prefix=/usr/local LIBS=-ldl
```

(plus as to orig. instructions - probably an ./autogen.sh to create a configure

---

### Post by hype on 2011-03-09
Yep, it worked :) 
Thanks for the tip; doesn't seem to be really 100% stable, but it's good to have emerald back :p

---

### Post by beew on 2011-03-09
Sorry for leaving the thread hanging. I am going to move my Natty install to a bigger harddrive ( ~3.5G now and fast running out of space after a few updates) There is no point doing anything until I get the hard drive in the next couple of days. It is awesome that it works!

---

### Post by gris-pato on 2011-03-17
Hey all, first time user.
I am trying to compile emerald, but can not get to the patch (emeraldfix.txt), could you put it somewhere we can access it.
thanks for the trouble.

---

### Post by hype on 2011-03-17
Here is the content of the file (copy/past this in a file called "emeraldfix.txt"; dont forget to put it in the "emerald" folder mentionned above)
```

diff -ru emerald/src/main.c emerald-fixed/src/main.c
--- emerald/src/main.c	2011-03-07 22:38:32.865582662 -0500
+++ emerald-fixed/src/main.c	2011-03-07 22:41:16.000000000 -0500
@@ -505,7 +505,7 @@
 	maxextents = extents;
 
     decor_quads_to_property(data, GDK_PIXMAP_XID(d->pixmap),
-			    &extents, &maxextents, 0, 0, quads, nQuad);
+			    &extents, &extents, &maxextents, &maxextents, 0, 0, quads, nQuad);
 
     gdk_error_trap_push();
     XChangeProperty(xdisplay, d->prop_xid,
@@ -1937,7 +1937,7 @@
     nQuad = set_switcher_quads(quads, d->width, d->height, ws);
 
     decor_quads_to_property(data, GDK_PIXMAP_XID(d->pixmap),
-			    &extents, &extents, 0, 0, quads, nQuad);
+			    &extents, &extents, &extents, &extents, 0, 0, quads, nQuad);
 
     style = gtk_widget_get_style (style_window);
 
@@ -2364,7 +2364,7 @@
 	nQuad = set_shadow_quads(quads, width, height, ws);
 
 	decor_quads_to_property(data, GDK_PIXMAP_XID(ws->shadow_pixmap),
-				&ws->shadow_extents, &ws->shadow_extents, 0, 0,
+				&ws->shadow_extents, &ws->shadow_extents, &ws->shadow_extents, &ws->shadow_extents, 0, 0,
 				quads, nQuad);
 
 	XChangeProperty(xdisplay, xroot,
@@ -2424,7 +2424,7 @@
 	(*d.draw) (&d);
 
 	decor_quads_to_property(data, GDK_PIXMAP_XID(d.p_inactive),
-				&extents, &extents, 0, 0, quads, nQuad);
+				&extents, &extents, &extents, &extents, 0, 0, quads, nQuad);
 
 	XChangeProperty(xdisplay, xroot,
 			normalAtom,
@@ -2433,7 +2433,7 @@
 			BASE_PROP_SIZE + QUAD_PROP_SIZE * nQuad);
 
 	decor_quads_to_property(data, GDK_PIXMAP_XID(d.p_active),
-				&extents, &extents, 0, 0, quads, nQuad);
+				&extents, &extents, &extents, &extents, 0, 0, quads, nQuad);
 
 	XChangeProperty(xdisplay, xroot,
 			activeAtom,

```

---

### Post by beew on 2011-04-11
Finally got a chance to do this but went into error
> mb@test:~$ git clone git://anongit.compiz.org/fusion/decorators/emerald
Cloning into emerald...
remote: Counting objects: 2251, done.
remote: Compressing objects: 100% (2204/2204), done.
remote: Total 2251 (delta 1613), reused 0 (delta 0)
Receiving objects: 100% (2251/2251), 823.98 KiB | 356 KiB/s, done.
Resolving deltas: 100% (1613/1613), done.
mb@test:~$ cd emerald
mb@test:~/emerald$ git checkout -b compiz++ origin/compiz++
Branch compiz++ set up to track remote branch compiz++ from origin.
Switched to a new branch 'compiz++'
mb@test:~/emerald$ patch -p1 < ../emeraldfix.txt
patching file src/main.c
mb@test:~/emerald$ ./configure --prefix=/usr/local
bash: ./configure: No such file or directory



Got stuck because of the last line.

---

### Post by mc4man on 2011-04-11
I mentioned this previously - 
you'll need to run this before a configure

```
./autogen.sh
```
There has been some changes to natty's gcc so you'll probably not need to link dl

---

### Post by beew on 2011-04-12
> **mc4man said:**
> I mentioned this previously - 
you'll need to run this before a configure

```
./autogen.sh
```There has been some changes to natty's gcc so you'll probably not need to link dl


Hi, still didn't work.

> mb@test:~/emerald$ ./autogen.sh
./autogen.sh: 9: autoreconf: not found


I ran this after > patch -p1 < ../emeraldfix.txt


---

### Post by mc4man on 2011-04-12
> **beew said:**
> Hi, still didn't work.
I ran this after

well install autoconf
(you may be missing others but the ./configure should show (when you have one to run

---

### Post by beew on 2011-04-13
Hi, Mc4man,

Still doesn't work!

Thanks for the patience.

```
~$ git clone git://anongit.compiz.org/fusion/decorators/emerald
Cloning into emerald...
remote: Counting objects: 2251, done.
remote: Compressing objects: 100% (2204/2204), done.
remote: Total 2251 (delta 1613), reused 0 (delta 0)
Receiving objects: 100% (2251/2251), 823.98 KiB | 396 KiB/s, done.
Resolving deltas: 100% (1613/1613), done.
mb@test:~$ cd emerald
mb@test:~/emerald$ git checkout -b compiz++ origin/compiz++
Branch compiz++ set up to track remote branch compiz++ from origin.
Switched to a new branch 'compiz++'
mb@test:~/emerald$ patch -p1 < ../emeraldfix.txt
patching file src/main.c
mb@test:~/emerald$ ./autogen.sh
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal 
autoreconf: configure.ac: tracing
autoreconf: running: libtoolize --install --copy
libtoolize: putting auxiliary files in `.'.
libtoolize: copying file `./config.guess'
libtoolize: copying file `./config.sub'
libtoolize: copying file `./install-sh'
libtoolize: copying file `./ltmain.sh'
libtoolize: Consider adding `AC_CONFIG_MACRO_DIR([m4])' to configure.ac and
libtoolize: rerunning libtoolize, to keep the correct libtool macros in-tree.
libtoolize: Consider adding `-I m4' to ACLOCAL_AMFLAGS in Makefile.am.
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy --no-force
configure.ac:6: installing `./missing'
engines/Makefile.am: installing `./depcomp'
autoreconf: Leaving directory `.'
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
[ftp://ftp.gnu.org/pub/gnu/config/](ftp://ftp.gnu.org/pub/gnu/config/).

./autogen.sh: 11: intltoolize: not found
mb@test:~/emerald$ ./configure --prefix=/usr/local LIBS=-ldl
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
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
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
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
checking for ANSI C header files... (cached) yes
./configure: line 11296: syntax error near unexpected token `0.35.0'
./configure: line 11296: `IT_PROG_INTLTOOL(0.35.0)'
mb@test:~/emerald$ make
make: *** No targets specified and no makefile found.  Stop.



```

---

### Post by beew on 2011-04-14
bump!

---

### Post by mc4man on 2011-04-14
```
sudo apt-get install intltool
```
may not be all that's missing - after above install run ./autogen.sh again,  which will also then automatically run a configure - take a look at the output and see 

(you also may no longer need the LIBS=-ldl anymore, and did you install compiz-dev  libdecoration0-dev as mentioned early

---

### Post by beew on 2011-04-14
> **mc4man said:**
> ```
sudo apt-get install intltool
```may not be all that's missing - after above install run ./autogen.sh again,  which will also then automatically run a configure - take a look at the output and see 

(you also may no longer need the LIBS=-ldl anymore, and did you install compiz-dev  libdecoration0-dev as mentioned early

Hi, thanks for the hint. I installed intltool and   ran configure again and I got 

> configure: error: Package requirements ( xrender >= 0.8.4              gtk+-2.0 >= 2.8.0             libwnck-1.0                      libdecoration         pangocairo) were not met:

No package 'gtk+-2.0' found
No package 'libwnck-1.0' found
I checked Synaptic but could not find any package called gtk+-2.0

There is libwnck-3.0 but no lbwnck-1.0

What should I do now? Thanks.

---

### Post by mc4man on 2011-04-14
Well I have to say I've no interest in emerald so if you do happen to get it built and installed can't say if it will work

You need to (in most but not all cases),  take what's not found so literally, nor search exactly. It's usually looking for the -dev libraries and in many cases stick a lib in front when searching

So  - 
libgtk2.0-dev
libwnck-dev
libxrender-dev 
libpango1.0-dev 
libcairo2-dev

---

### Post by beew on 2011-04-15
> **mc4man said:**
> Well I have to say I've no interest in emerald so if you do happen to get it built and installed can't say if it will work

You need to (in most but not all cases),  take what's not found so literally, nor search exactly. It's usually looking for the -dev libraries and in many cases stick a lib in front when searching

So  - 
libgtk2.0-dev
libwnck-dev
libxrender-dev 
libpango1.0-dev 
libcairo2-dev

Thanks, I installed a bunch of -dev files and libraries as you said and it seem to have worked. After make install there are a bunch of emerald stuffs in /usr/local/share but I am not sure how to use them. Normally one would do something like emerald --replace but I think this is a local install if it is installed at all (emerald is not installed in Synaptic)
I am not sure this is right..

Again thanks for the help and patience.

---

### Post by BwackNinja on 2011-04-15
> **beew said:**
> Thanks, I installed a bunch of -dev files and libraries as you said and it seem to have worked. After make install there are a bunch of emerald stuffs in /usr/local/share but I am not sure how to use them. Normally one would do something like emerald --replace but I think this is a local install if it is installed at all (emerald is not installed in Synaptic)
I am not sure this is right..

Again thanks for the help and patience.

You can just do an emerald --replace.

/usr/local/bin is in your $PATH.

---

### Post by beew on 2011-04-15
> **BwackNinja said:**
> You can just do an emerald --replace.

/usr/local/bin is in your $PATH.

Hi, just did that and nothing happened. Is there a way to check whether emerald is actually installed?

Also, there is a desktop file for emerald-theme-manager in /usr/local/share/applications but it has no icon and doesn't seem to anything (I have already changed it to executable using chmod + x)  

Thanks.

---

### Post by beew on 2011-04-15
Oh, it works. If I do "emerald --replace" in the terminal it works, but it doesn't do anything if i type it into the command box opened by alt+F2 (so it may be a bug for alt+f2)

I opened ccsm and changed the command in Window Decoration to /usr/local/bin/emerald and now it starts up automatically. The only thing is that it doesn't work on maximized windows,--because of requirements for the global menu I am sure,-- but I can live with it.

I hope eventually there will be a real window decorator for Unity which would allow emerald like theming options. gtk-window-decorator doesn't decorate, it is just a black bar.

Thanks to everyone who has helped, especially mc4man who has been very patient and helpful even though he doesn't use emerald himself.

---

### Post by wizard10000 on 2011-04-25
If anybody's interested, KDE users can use smaragd to run emerald themes under kwin.  Works pretty well - and there's a ppa available.

[http://kde-look.org/content/show.php/Smaragd+%28Emerald+for+KDE%29?content=125162](http://kde-look.org/content/show.php/Smaragd+%28Emerald+for+KDE%29?content=125162)

Not hard to set up at all.

---

