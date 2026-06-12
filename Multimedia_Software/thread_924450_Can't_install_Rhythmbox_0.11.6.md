---
title: "Can't install Rhythmbox 0.11.6"
date: 2008-09-19
forum: Multimedia Software
---

### Post by thehkv on 2008-09-19
Hi everyone.

I seem to be having trouble installing latest Rhythmbox 0.11.6 from source code posted [here]("http://ftp.gnome.org/pub/GNOME/sources/rhythmbox/0.11/rhythmbox-0.11.6.tar.gz"). ([Other versions]("http://ftp.gnome.org/pub/GNOME/sources/rhythmbox/0.11/?C=M;O=D"))

1. I downloaded rhythmbox-0.11.6.tar.gz
2. extracted it in rhythmbox
3. cd into it
4. ./configure > output.txt
contents of output.txt :
[HTML]checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking for intltool >= 0.35.0... 0.37.1 found
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
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
checking the maximum length of command line arguments... 98304
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
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
checking how to run the C++ preprocessor... g++ -E
checking whether byte ordering is bigendian... no
checking for long... yes
checking size of long... 4
checking for GNU extension fwrite_unlocked... yes
checking for mkdtemp... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GLIB_TESTS... [/HTML]

Output on the terminal :
[HTML]
configure: error: Package requirements (glib-2.0) were not met:

No package 'glib-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GLIB_TESTS_CFLAGS
and GLIB_TESTS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.[/HTML]

5. I guess since there were errors, make did not work and gave this error : 
[HTML]make: *** No targets specified and no makefile found.  Stop.[/HTML]

6. And make install this : 
[HTML]make: *** No rule to make target `install'.  Stop.[/HTML]

I cant find any 'glib-2.0' in synaptic.

Can anyone please tell me what am I doing wrong ?
Can't I get a deb from somewhere instead ?

I needed the newer version because 0.11.5 quits the application on crossing it (X button); in .6, they've fixed it (goes to tray instead of exiting).
I switched to amarok but my multimedia keys won't work with it and I like rhythmbox instead.

---

### Post by xc3RnbFO8P on 2008-09-19
Do have **libglib2.0-0** installed in Synaptic?

---

### Post by thehkv on 2008-09-19
I searched, and it was installed. But I marked it for re-installation, and two others too - **libglib2.0-0-dbg** and **libglib2.0-dev**.
Then I did **./configure** again, now it shows a different error : 

No package 'gnome-vfs-2.0' found

So I looked it up in synaptic, it showed **libgnome2-vfs-perl** which was already installed. I re-installed but same error.
What else package could I be missing ? 
Thanks for replying.

Edit : **libglib2.0-dev** was needed I guess.

---

### Post by xc3RnbFO8P on 2008-09-19
Search for **vfs**,

---

### Post by thehkv on 2008-09-19
It returned 93 packages, 17 are installed, none by the name vfs alone.
Can you give me exact package name ? Or should I install all 93 of them ?

---

### Post by xc3RnbFO8P on 2008-09-19
> Or should I install all 93 of them ?
No, I would try packages with ubuntu sign, one at the time.

---

### Post by thehkv on 2008-09-19
I installed **libgnomevfs2-dev** (and dependencies). (By a guess based on [this page]("http://ubuntuforums.org/showthread.php?t=385981&page=24"))

Compiled, and I got this error : 

[COLOR="Red"]No package 'gtk+-2.0' found
No package 'libgnomeui-2.0' found
No package 'libglade-2.0' found[/COLOR]

I searched again, and found that ...

[gtk+-2.0	= **libgtk2.0-dev**]("http://ubuntuforums.org/showthread.php?p=46719")
[libgnomeui-2.0	= **libgnomeui-dev**]("http://ubuntuforums.org/showthread.php?t=645838")
[libglade-2.0	= **libglade2-dev**]("http://ubuntuforums.org/showthread.php?t=692523")

So I installed them (and dependencies).
Then I got this error

[COLOR="Red"]configure: error: totem playlist parsing library not found or too old[/COLOR]

I searched and found [here]("http://www.pcworld.com/article/127601-2/free_agent_how_to_compile_free_software_apps.html") that I needed **libtotem-plparser-dev**.

Further errors : 
[COLOR="Red"]
No package 'gstreamer-0.10' found
No package 'gstreamer-base-0.10' found
No package 'gstreamer-plugins-base-0.10' found[/COLOR]

By now, I feel like I have a little experience, so in synaptic I'm guessing
gstreamer-0.10 = **libgstreamer0.10-dev**
gstreamer-base-0.10 = **??**
gstreamer-plugins-base-0.10 = **libgstreamer-plugins-base0.10-dev**

[COLOR="Red"]No package 'dbus-glib-1' found[/COLOR] [IMG]http://l.yimg.com/us.yimg.com/i/mesg/emoticons7/102.gif[/IMG]

dbus-glib-1 = **libdbus-glib-1-dev**

[COLOR="Red"]No package 'pygtk-2.0' found[/COLOR]
= **python-gtk2-dev**

No errors this time. [IMG]http://l.yimg.com/us.yimg.com/i/mesg/emoticons7/13.gif[/IMG]
I did **make**. It started building.
Errors : [IMG]http://l.yimg.com/us.yimg.com/i/mesg/emoticons7/29.gif[/IMG][COLOR="red"]
.
.
.
In file included from rb-audioscrobbler-entry.c:41:
../../lib/rb-soup-compat.h:31:26: error: libsoup/soup.h: No such file or directory
rb-audioscrobbler-entry.c: In function &#8216;rb_audioscrobbler_entry_encode&#8217;:
rb-audioscrobbler-entry.c:117: warning: assignment makes pointer from integer without a cast
rb-audioscrobbler-entry.c:119: warning: assignment makes pointer from integer without a cast
rb-audioscrobbler-entry.c:121: warning: assignment makes pointer from integer without a cast
rb-audioscrobbler-entry.c:123: warning: assignment makes pointer from integer without a cast
make[4]: *** [rb-audioscrobbler-entry.lo] Error 1
make[4]: Leaving directory `/home/hkv/Desktop/rhythmbox/rhythmbox/plugins/audioscrobbler'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/hkv/Desktop/rhythmbox/rhythmbox/plugins/audioscrobbler'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/hkv/Desktop/rhythmbox/rhythmbox/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/hkv/Desktop/rhythmbox/rhythmbox'
make: *** [all] Error 2
[/COLOR]

Any Ideas ? Now I'm down to just building it. The *whole* output of **make** attached as text.

---

### Post by Yellow Pasque on 2008-09-19
```
sudo apt-get install libsoup2.4-dev
```

Also, the next time you build something from source that has an equivalent package in Synaptic, you can save yourself a lot of grief by grabbing the necessary libs with:
```
sudo apt-get build-dep <packagename>
```

---

### Post by thehkv on 2008-09-19
> **Temüjin said:**
> Also, the next time you build something from source that has an equivalent package in Synaptic, you can save yourself a lot of grief by grabbing the necessary libs with:```
sudo apt-get build-dep <packagename>
``` If only I had known that before. [IMG]http://l.yimg.com/us.yimg.com/i/mesg/emoticons7/40.gif[/IMG]

ha ha !! I did it ! after 6 hrs of googling - I finally did it !! woo hoo [IMG]http://l.yimg.com/us.yimg.com/i/mesg/emoticons7/111.gif[/IMG] !! compiled from scratch !! yeah baby !!
er-ahem .. excuse me <comes back to senses>

thanks a ton guys.
umm one last thing, how can I make a DEB package out of it ?

---

### Post by Yellow Pasque on 2008-09-19
Making .deb's is a bit complicated when you first start to do it (which is expected because it's an elegant system that makes things easy for the end-user).

I like this quick'n'dirty guide: [http://www.linuxdevices.com/articles/AT8047723203.html](http://www.linuxdevices.com/articles/AT8047723203.html)

---

### Post by NeoZiggy on 2009-02-25
WHEW! Thanks for help with this to all the past people who helped with this topic. However after trying to run Rhythmbox it would not launch. Running it in terminal showed this error: "rhythmbox: symbol lookup error: rhythmbox: undefined symbol: rb_marshal_BOOLEAN__STRING_BOOLEAN".

The answer to that problem I found in this thread: [http://ubuntuforums.org/showthread.php?t=822662]("http://ubuntuforums.org/showthread.php?t=822662")
Just in case some one else has the same problem.

Rock on! :guitar:

---

