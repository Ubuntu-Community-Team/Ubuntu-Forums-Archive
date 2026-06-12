---
title: "Good webcam app"
date: 2008-02-28
forum: Multimedia &amp; Video
---

### Post by Ephemeral on 2008-02-28
Hello, yet again ^^

I have looked all over, but still can't find a good application for my Webcam (eyetoy) I just installed. I got Cheese working, but I need more options to modifiy Luminuosity, Hue and all those settings.
XawTV just doesn't start, I click and nothing happens.
Pitivi can't be used to film anything.

I tried getting AMCAP to work under Wine, but it doesn't work, error when I start and no display.

Any other good apps ?

Thanks
~Mark

---

### Post by linuxwizard on 2008-02-28
Try Camorama, Ekiga, or look through this list you may find something > [http://www.exploits.org/v4l/](http://www.exploits.org/v4l/)

---

### Post by Ephemeral on 2008-02-28
I downloaded camorama, extracted it, and here is what happens :

```
eternal@eternal-desktop:~$ cd /home/eternal/Desktop
eternal@eternal-desktop:~/Desktop$ cd camorame-0.19
bash: cd: camorame-0.19: No such file or directory
eternal@eternal-desktop:~/Desktop$ cd camorama-0.19
eternal@eternal-desktop:~/Desktop/camorama-0.19$ sudo ./configure
[sudo] password for eternal:
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
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
checking for intltool >= 0.21... 0.35.5 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... msgfmt
checking for msgmerge... msgmerge
checking for xgettext... xgettext
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
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
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
checking for msgfmt... no
checking prefix... /usr/local
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for ANSI C header files... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking for unistd.h... (cached) yes
checking linux/videodev.h usability... yes
checking linux/videodev.h presence... yes
checking for linux/videodev.h... yes
checking png.h usability... no
checking png.h presence... no
checking for png.h... no
checking glade/glade.h usability... no
checking glade/glade.h presence... no
checking for glade/glade.h... no
checking what warning flags to pass to the C compiler... -Wall -Wmissing-prototypes
checking what language compliance flags to pass to the C compiler... 
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PACKAGE... configure: error: Package requirements (gdk-pixbuf-2.0 gdk-pixbuf-xlib-2.0 libgnomeui-2.0 gtk+-2.0 >= 2.10 gconf-2.0 libglade-2.0) were not met:

No package 'gdk-pixbuf-2.0' found
No package 'gdk-pixbuf-xlib-2.0' found
No package 'libgnomeui-2.0' found
No package 'gtk+-2.0' found
No package 'gconf-2.0' found
No package 'libglade-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

eternal@eternal-desktop:~/Desktop/camorama-0.19$ sudo make
make: *** No targets specified and no makefile found.  Stop.
eternal@eternal-desktop:~/Desktop/camorama-0.19$ sudo makeinstall
sudo: makeinstall: command not found
eternal@eternal-desktop:~/Desktop/camorama-0.19$ sudo make install
make: *** No rule to make target `install'.  Stop.
eternal@eternal-desktop:~/Desktop/camorama-0.19$ make
make: *** No targets specified and no makefile found.  Stop.
eternal@eternal-desktop:~/Desktop/camorama-0.19$ sh install-sh
install-sh: no input file specified.
eternal@eternal-desktop:~/Desktop/camorama-0
```

Any ideas?

*edit* : Need packages, I'll install them

---

### Post by linuxwizard on 2008-02-28
Camorama is in the repo. Install it with Synaptic.

---

### Post by Ephemeral on 2008-02-28
This is only for taking pictures, I want to film.
That and the image is in black & white and three images appear, squashed together.

---

### Post by Ephemeral on 2008-02-29
Bump

---

