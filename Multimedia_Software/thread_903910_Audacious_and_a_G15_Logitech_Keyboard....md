---
title: "Audacious and a G15 Logitech Keyboard..."
date: 2008-08-28
forum: Multimedia Software
---

### Post by TheKeyMaker on 2008-08-28
My question is really one of two. The first one is probably the easiest. 

1) I have a Logitech G15 keyboard, as the title implies, and would like to use the multi media keys (play/pause, stop, etc...) to control Audacious. For Rhythmbox is work right away. Is there any good plug-in or webpages that you would recommend works well. 

2) Also along with all of this I am trying to get the LCD to display the music info. I found this site [http://gentoo-wiki.com/HARDWARE_Logitech_G15]("http://gentoo-wiki.com/HARDWARE_Logitech_G15") that talks about it, but through the install I get this error:

```

thekeymaker@B:~$ svn co https://g15daemon.svn.sourceforge.net/svnroot/g15daemon/trunk/g15daemon-audio-plugins/g15daemon_audacious
A    g15daemon_audacious/g15daemon_audacious_spectrum.c
A    g15daemon_audacious/debian
A    g15daemon_audacious/debian/control
A    g15daemon_audacious/debian/dirs
A    g15daemon_audacious/debian/files
A    g15daemon_audacious/debian/compat
A    g15daemon_audacious/debian/changelog
A    g15daemon_audacious/debian/copyright
A    g15daemon_audacious/debian/docs
A    g15daemon_audacious/debian/rules
A    g15daemon_audacious/debian/README.Debian
A    g15daemon_audacious/AUTHORS
A    g15daemon_audacious/TODO
A    g15daemon_audacious/config
A    g15daemon_audacious/INSTALL
A    g15daemon_audacious/configure.in
A    g15daemon_audacious/ChangeLog
A    g15daemon_audacious/COPYING
A    g15daemon_audacious/Makefile.am
A    g15daemon_audacious/autogen.sh
A    g15daemon_audacious/NEWS
A    g15daemon_audacious/README
Checked out revision 463.
thekeymaker@B:~$ cd g15daemon_audacious
thekeymaker@B:~/g15daemon_audacious$ ./autogen.sh && ./configure && make
+ aclocal -I config
+ libtoolize --force --copy
./autogen.sh: 1: libtoolize: not found
+ autoheader
+ automake --add-missing --copy
configure.in: installing `config/install-sh'
configure.in: installing `config/missing'
Makefile.am:1: Libtool library used but `LIBTOOL' is undefined
Makefile.am:1: 
Makefile.am:1: The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
Makefile.am:1: to `configure.in' and run `aclocal' and `autoconf' again.
Makefile.am: installing `config/depcomp'
+ autoconf
**configure.in:17: error: possibly undefined macro: AC_PROG_LIBTOOL**
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.


``` 

If anyone knows how to do this or know a better way please help.

If it helps I'm running Ubuntu 8.04, Audacious 1.5.0, and I do have my LCD display working with G15Tools [http://www.g15tools.com/Welcome.html]("http://www.g15tools.com/Welcome.html")

Any help is appreciated!!!

Thank You!

---

