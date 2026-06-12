---
title: "autogen script for wired not working..."
date: 2007-10-01
forum: Multimedia Production
---

### Post by pixeltarian on 2007-10-01
any ideas how to get a smooth output so I can "./configure" this version of wired? 
right now if I do it after autogen, it spits out: 

>  configure: error: cannot find install-sh or install.sh in config "."/config

here's the ./autogen output:
> jeffrey@jeffrey-desktop:~/Desktop/wired$ sudo ./autogen.sh
+ rm -rf config
+ rm -f aclocal.m4 configure config.log config.status
+ rm -rf autom4te.cache
+ rm -f libtool
+ rm -f ABOUT-NLS
+ rm -rf intl
+ mkdir config
+ mkdir intl
+ autopoint -f
Copying file ABOUT-NLS
Copying file config/config.rpath
Copying file intl/ChangeLog
Copying file intl/Makefile.in
Copying file intl/VERSION
Copying file intl/bindtextdom.c
Copying file intl/config.charset
Copying file intl/dcgettext.c
Copying file intl/dcigettext.c
Copying file intl/dcngettext.c
Copying file intl/dgettext.c
Copying file intl/dngettext.c
Copying file intl/eval-plural.h
Copying file intl/explodename.c
Copying file intl/finddomain.c
Copying file intl/gettext.c
Copying file intl/gettextP.h
Copying file intl/gmo.h
Copying file intl/hash-string.h
Copying file intl/intl-compat.c
Copying file intl/l10nflist.c
Copying file intl/langprefs.c
Copying file intl/libgnuintl.h.in
Copying file intl/loadinfo.h
Copying file intl/loadmsgcat.c
Copying file intl/localcharset.c
Copying file intl/localcharset.h
Copying file intl/locale.alias
Copying file intl/localealias.c
Copying file intl/localename.c
Copying file intl/log.c
Copying file intl/ngettext.c
Copying file intl/os2compat.c
Copying file intl/os2compat.h
Copying file intl/osdep.c
Copying file intl/plural-exp.c
Copying file intl/plural-exp.h
Copying file intl/plural.c
Copying file intl/plural.y
Copying file intl/printf-args.c
Copying file intl/printf-args.h
Copying file intl/printf-parse.c
Copying file intl/printf-parse.h
Copying file intl/printf.c
Copying file intl/ref-add.sin
Copying file intl/ref-del.sin
Copying file intl/relocatable.c
Copying file intl/relocatable.h
Copying file intl/textdomain.c
Copying file intl/vasnprintf.c
Copying file intl/vasnprintf.h
Copying file intl/vasnwprintf.h
Copying file intl/wprintf-parse.h
Copying file intl/xsize.h
Creating directory config/m4
Copying file config/m4/codeset.m4
Copying file config/m4/gettext.m4
Copying file config/m4/glibc2.m4
Copying file config/m4/glibc21.m4
Copying file config/m4/iconv.m4
Copying file config/m4/intdiv0.m4
Copying file config/m4/intmax.m4
Copying file config/m4/inttypes-pri.m4
Copying file config/m4/inttypes.m4
Copying file config/m4/inttypes_h.m4
Copying file config/m4/isc-posix.m4
Copying file config/m4/lcmessage.m4
Copying file config/m4/lib-ld.m4
Copying file config/m4/lib-link.m4
Copying file config/m4/lib-prefix.m4
Copying file config/m4/longdouble.m4
Copying file config/m4/longlong.m4
Copying file config/m4/nls.m4
Copying file config/m4/po.m4
Copying file config/m4/printf-posix.m4
Copying file config/m4/progtest.m4
Copying file config/m4/signed.m4
Copying file config/m4/size_max.m4
Copying file config/m4/stdint_h.m4
Copying file config/m4/uintmax_t.m4
Copying file config/m4/ulonglong.m4
Copying file config/m4/wchar_t.m4
Copying file config/m4/wint_t.m4
Copying file config/m4/xsize.m4
Copying file config/mkinstalldirs
[COLOR="Red"]+ aclocal --force -I config/m4
/usr/share/aclocal/soundtouch.m4:29: warning: underquoted definition of AM_PATH_SOUNDTOUCH
/usr/share/aclocal/soundtouch.m4:29:   run info '(automake)Extending aclocal'
/usr/share/aclocal/soundtouch.m4:29:   or see [http://sources.redhat.com/automake/automake.html#Extending-aclocal](http://sources.redhat.com/automake/automake.html#Extending-aclocal)
configure.ac:124: warning: macro `AM_OPTIONS_WXCONFIG' not found in library
configure.ac:126: warning: macro `AM_PATH_WXCONFIG' not found in library
+ libtoolize --force -c
Putting files in AC_CONFIG_AUX_DIR, `config'.
+ autoconf
configure.ac:127: error: possibly undefined macro: AM_OPTIONS_WXCONFIG
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.ac:129: error: possibly undefined macro: AM_PATH_WXCONFIG
+ set +x[/COLOR]



thanks in advance, 
-pix

---

### Post by pixeltarian on 2007-10-01
bump

---

### Post by Jonathan Huot on 2008-02-29
Hello pixeltarian,

You have to install wx-commons to finish the autogen.sh process.

If you have more issues, check the INSTALL file, it would be useful :)

Good luck !

---

### Post by pythonusr on 2008-03-20
```
Copying file config/mkinstalldirs
+ aclocal --force -I config/m4
/usr/share/aclocal/soundtouch.m4:29: warning: underquoted definition of AM_PATH_SOUNDTOUCH
/usr/share/aclocal/soundtouch.m4:29:   run info '(automake)Extending aclocal'
/usr/share/aclocal/soundtouch.m4:29:   or see http://sources.redhat.com/automake/automake.html#Extending-aclocal
+ libtoolize --force -c
./autogen.sh: 1: libtoolize: not found
+ set +x
alex@alex-laptop:~/Desktop/wired-0.6$ 
```

That's my error. What's wrong here?

---

### Post by ceelow on 2008-04-06
I've tried to run the wired make config script, it stops at this for me:

Copying file config/mkinstalldirs
+ aclocal --force -I config/m4
./autogen.sh: 1: aclocal: not found
+ set +x
cee@lin-base:~/Desktop/wired-0.6$ 

"aclocal" I would assume to be a directory, sudo doesn't help I haven't read the script yet to see if its a problem...

I'm just stuck! Does anyone have a solution?  (And can someone flag this great-looking app to included in the repos?) :D

---

### Post by plexus on 2008-07-14
I'm doing a source install of wired 0.6 on Debian Etch, I needed these packages. This *should* work on Ubuntu just as well

```

sudo apt-get install libwxgtk2.6-dev libsamplerate0-dev portaudio19-dev autotools-dev automake libtool wx-common libsoundtouch1-dev libasound2-dev
./autogen.sh
./configure && make
sudo make install

```

to actually run it I had to do:

```

export LD_LIBRARY_PATH=/usr/local/lib
wired

```

The INSTALL file has more info about why you need the LD_LIBRARY_PATH.

Have fun!

---

