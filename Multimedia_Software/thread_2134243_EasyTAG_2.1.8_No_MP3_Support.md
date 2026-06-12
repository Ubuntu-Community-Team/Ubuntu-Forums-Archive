---
title: "EasyTAG 2.1.8 No MP3 Support"
date: 2013-04-10
forum: Multimedia Software
---

### Post by Thadago on 2013-04-10
Hello All,

I have spent the better part of the day attempting to get EasyTAG 2.1.8 to compile and work.  Long story short I have all of the dependencies met (to the best of my knowledge).  It will not find MP3s and it refuses to compile with not only MP3 support, but with ANY file support:

Configuration for EasyTAG 2.1.8 :
--------------------------------


Source code location ....: .
Host System Type ........: x86_64-unknown-linux-gnu
Preprocessor ............: gcc
Deprecation defines .....: -DG_DISABLE_SINGLE_INCLUDES -DGTK_DISABLE_SINGLE_INCLUDES -DG_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED -DGSEAL_ENABLE
Compiler ................: gcc -g -O2
Compiler warnings .......: -Wall -Wstrict-prototypes -Wnested-externs -Werror=missing-prototypes -Werror=implicit-function-declaration -Werror=pointer-arith -Werror=init-self -Werror=format-security -Werror=format=2 -Werror=missing-include-dirs -Werror=declaration-after-statement
Linker ..................: gcc
GTK version .............: 3.4.2
MP3 file support ........: no
ID3v2.3 tags support ....: no
Ogg Vorbis file support .: no
Ogg Speex file support ..: no
FLAC file support .......: no
MP4 file support ........: no
WavPack support .........: no
NLS/gettext .............: yes
Install prefix ..........: /usr/local


Now type make to build EasyTAG 2.1.8,
and then make install for installation.


I have libid3 installed:

chris@UbuntuBox:/usr/lib$ ls -l *id3*
lrwxrwxrwx 1 root root     19 Oct 18  2011 libid3-3.8.so.3 -> libid3-3.8.so.3.0.0
-rw-r--r-- 1 root root 233000 Oct 18  2011 libid3-3.8.so.3.0.0
-rw-r--r-- 1 root root 621524 Oct 18  2011 libid3.a
-rw-r--r-- 1 root root    939 Oct 18  2011 libid3.la
lrwxrwxrwx 1 root root     19 Oct 18  2011 libid3.so -> libid3-3.8.so.3.0.0
lrwxrwxrwx 1 root root     18 Mar  6  2010 libid3tag.so.0 -> libid3tag.so.0.3.0
-rw-r--r-- 1 root root  88336 Mar  6  2010 libid3tag.so.0.3.0

---

### Post by tgalati4 on 2013-04-10
What is in 2.1.8 that you need?  2.1.7-2 is in 12.10.

tgalati4@Mint14-Extensa ~ $ apt-cache policy easytag
easytag:
  Installed: 2.1.7-2
  Candidate: 2.1.7-2
  Version table:
 *** 2.1.7-2 0
    

Do you have all of the dependencies?

tgalati4@Mint14-Extensa ~ $ apt-cache depends easytag
easytag
  Depends: libc6
  Depends: libflac8
  Depends: libgdk-pixbuf2.0-0
  Depends: libglib2.0-0
  Depends: libgtk2.0-0
  Depends: libid3-3.8.3c2a
  Depends: libid3tag0
  Depends: libogg0
  Depends: libpango1.0-0
  Depends: libspeex1
  Depends: libstdc++6
  Depends: libtagc0
  Depends: libvorbis0a
  Depends: libvorbisfile3
  Depends: libwavpack1
  Conflicts: easytag:i386

---

### Post by andrew.46 on 2013-04-11
Perhaps use a somewhat shotgun approach to gathering the dependencies:

```

sudo apt-get build-dep easytag

```

---

