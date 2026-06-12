---
title: "How to compile mp4creator?"
date: 2016-12-15
forum: Multimedia Software
---

### Post by ron998 on 2016-12-15
Hi
I need to use mp4creator to mux aac files for my low-spec player.
At present I'm using mp4creator.exe with wine.
It's attached below.
It works OK but I'd like to compile a linux version.

```
$ wine ./mp4creator -version
Z:\home\user\mp4creator.exe - mpeg4ip version 1.6.1d
```

Use it like this...
```
$ wine ./mp4creator -create=foo.aac foo.m4a
```

The source code is available from sourceforge...
```
$ wget sourceforge.net/projects/mp4creator/files/mp4creator/version%201.6.1d/mp4creator-src-1.6.1d.tar.gz
$ tar -xf mp4creator-src-1.6.1d.tar.gz
$ cd v1.6.1d
$ chmod a+x bootstrap
$ ./bootstrap
```

But when I run ./bootstrap there is an error...

```
$ ./bootstrap
dir: .
Please run cvs_bootstrap instead.
Please note that you will need autoconf, automake and libtool
of the correct version as specified in the README
```

I have autoconf, automake and libtool installed but I don't understand about "**cvs_bootstrap**".

Any ideas what to do next?:confused:

(My distro is 64-bit Linux Mint 18 Sarah, similar to Xubuntu-16.04)

---

### Post by Keith_Helms on 2016-12-15
I looked at the sourceforge page for mp4creator and found no mention that it will run on anything other than Windows.

---

### Post by ron998 on 2016-12-15
> **Keith_Helms said:**
> ... no mention that it will run on anything other than Windows.Hmmm
I think that mp4creator is part of mpeg4ip which used to be available for Ubuntu back in the day.
Packages such as  [FONT=courier new]mpeg4ip-utils[/FONT] and [FONT=courier new]mpeg4ip-server[/FONT].

There is a git mirror here ---> [https://github.com/stsquad/mpeg4ip](https://github.com/stsquad/mpeg4ip)
It has a **cvs_bootstrap** file.
But when I run it there are errors.

```
$ git clone https://github.com/stsquad/mpeg4ip
$ cd mpeg4ip
```

```
$ ./cvs_bootstrap
Found SDL
+ mkdir -p ./config
+ which aclocal
+ test -d /usr/local/share/aclocal -a /usr/bin/aclocal != /usr/local/bin/aclocal
+ ACLOCAL_FLAGS=-I /usr/local/share/aclocal 
+ which aclocal
+ test -d /usr/contrib/share/aclocal -a /usr/bin/aclocal != /usr/contrib/bin/aclocal
+ which aclocal
+ test -d /opt/gnome/share/aclocal -a /usr/bin/aclocal != /opt/gnome/bin/aclocal
+ which aclocal
+ test -d /usr/share/aclocal -a /usr/bin/aclocal != /usr/bin/aclocal
+ which aclocal
+ test -d /opt/local/share/aclocal -a /usr/bin/aclocal != /opt/local/bin/aclocal
+ test Linux != CYGWIN_NT-5.1
+ ERRCMD=--enable-warns-as-err
+ pwd
+ pwd=/home/user/mpeg4ip
+ test Linux != Darwin
+ test Linux != CYGWIN_NT-5.1
+ cd /home/ron/mpeg4ip/lib/SDLAudio
+ aclocal -I /usr/local/share/aclocal
aclocal: warning: autoconf input should be named 'configure.ac', not 'configure.in'
+ libtoolize --force
libtoolize: putting auxiliary files in '.'.
libtoolize: linking file './ltmain.sh'
libtoolize: Consider adding 'AC_CONFIG_MACRO_DIRS([m4])' to configure.in,
libtoolize: and rerunning libtoolize and aclocal.
libtoolize: Consider adding '-I m4' to ACLOCAL_AMFLAGS in Makefile.am.
+ automake --add-missing --foreign
automake: warning: autoconf input should be named 'configure.ac', not 'configure.in'
configure.in:44: warning: AM_INIT_AUTOMAKE: two- and three-arguments forms are deprecated.  For more info, see:
configure.in:44: http://www.gnu.org/software/automake/manual/automake.html#Modernize-AM_005fINIT_005fAUTOMAKE-invocation
configure.in:49: installing './compile'
configure.in:41: installing './config.guess'
configure.in:41: installing './config.sub'
configure.in:44: installing './install-sh'
configure.in:44: installing './missing'
automake: warning: autoconf input should be named 'configure.ac', not 'configure.in'
src/audio/Makefile.am: installing './depcomp'
/usr/share/automake-1.15/am/depend2.am: error: am__fastdepCCAS does not appear in AM_CONDITIONAL
/usr/share/automake-1.15/am/depend2.am:   The usual way to define 'am__fastdepCCAS' is to add 'AM_PROG_AS'
/usr/share/automake-1.15/am/depend2.am:   to 'configure.in' and run 'aclocal' and 'autoconf' again
+ exit 5
```

---

### Post by SeijiSensei on 2016-12-15
I use ffmpeg for most tasks like this.  Just today I created a couple of .mp4 files using a video encoded with Apple prores and an audio file in Ogg.  The output file used H.264 and AAC.  I followed this guide and used the two-pass method: [https://trac.ffmpeg.org/wiki/Encode/H.264](https://trac.ffmpeg.org/wiki/Encode/H.264)

---

### Post by mc4man on 2016-12-15
With a  bit of work you *may* be able to build in 12.04, after that no way.. You should be able to dupe whatever you need in ffmpeg or just keep using wine.

---

### Post by ron998 on 2016-12-16
> **mc4man said:**
> ... you *may* be able to build in 12.04...

Hi
Do you think that I could *build* a static version of mp4creator in 12.04 (using a live CD/USB) then *use* it in 16.04?

---

### Post by Keith_Helms on 2016-12-16
I tried to nurse a favorite program along after it was dropped from the repositories - the grip CD ripper - and found that dependencies on old versions of libraries just made it too much work.  I switched to a supported program and it actually turned out to be better.

---

### Post by mc4man on 2016-12-16
> **ron998 said:**
> Hi
Do you think that I could *build* a static version of mp4creator in 12.04 (using a live CD/USB) then *use* it in 16.04?
Don't think so & to boot don't see anything in the old utils package similar to 'mp4create', screen shows the binaries it provided.

Does your player not use m4a > aac done thru ffmpeg?

---

### Post by ron998 on 2016-12-16
> **mc4man said:**
> ... don't see anything in the old utils package similar to 'mp4creator'
Maybe it's in the [FONT=courier new]mpeg4ip-server[/FONT] package.

---

### Post by ron998 on 2016-12-17
> **mc4man said:**
> ...a  bit of work...
Hi
Found a source for a _standalone_ mp4creator.
[https://sourceforge.net/p/mp4creator/code/HEAD/tree/](https://sourceforge.net/p/mp4creator/code/HEAD/tree/)
This might be less hassle than the mpeg4ip package, if we can figure it out how to build it.:p

```
$ svn checkout svn://svn.code.sf.net/p/mp4creator/code/trunk mp4creator-code
$ cd mp4creator-code
$ ./cvs_bootstrap
```

When I run the **./cvs_bootstrap** it gives an error...
"util/testnasm.sh: line 8: test: =: unary operator expected"

It's supposed to check the version of nasm... 
"# This shell looks for version, then sees if we're 0.98.19 or greater"

I have nasm installed, but that routine util/testnasm.sh won't accept it.
```
~ $ nasm -v
NASM version 2.11.08
```

So I've hacked my util/testnasm.sh script.
Now it says...
```
#
# shell to verify nasm version
# nasm -r has format "NASM version <foo> <extra stuff>"
#
# This shell looks for version, then sees if we're 0.98.19 or greater
#
#
# SKIP THE TEST because I know that NASM version 2.11.08 is installed.
echo "yes"
exit 0
#
#
```

The **./cvs_bootstrap** script now returns...
```
MP4Live is not installed (requires V4L2 - check log)
ready to make
```

But make gives an error.
```
Makefile:396: recipe for target 'all' failed
make: *** [all] Error 2
```
I've attached the config log and make error below.
Any ideas?
:-?

PS
Do you think it's failing because I'm using 16.04? :mad:

---

### Post by mc4man on 2016-12-17
Well I got it quite a ways by fixing a few errors but then a boatload of undefined ref's, looks quite tedious to resolve.
Maybe you should try a much older gcc, here I tried gcc-4.7 which is the oldest directly available in 16.04.
Attached make log so you can see the final bunch..

Two earlier errors are resolved as such - 
In /include/mpeg4ip.h remove line 128 so looks like - 
```
#ifdef __cplusplus
extern "C" {
#endif

#ifdef __cplusplus
}
#endif
```

In /lib/mp4v2/Makefile.am add atom_chp1.cpp \  so looks like - 
 	atom_amr.cpp \
 	atom_avc1.cpp \
 	atom_avcC.cpp \
	atom_chp1.cpp \
 	atom_d263.cpp \
 	atom_damr.cpp \
 	atom_dref.cpp \

---

### Post by #&amp;thj^% on 2016-12-17
Would gpac work? [https://gpac.wp.mines-telecom.fr/mp4box/mp4box-documentation/](https://gpac.wp.mines-telecom.fr/mp4box/mp4box-documentation/)

It has MP4box: [https://gpac.wp.mines-telecom.fr/mp4box/](https://gpac.wp.mines-telecom.fr/mp4box/)
Just a Thought.

---

### Post by mc4man on 2016-12-17
Try this if on _64 bit_ install - 
extract attached folder
place the 4 .so's in /usr/local/lib 
Run -
```
sudo ldconfig 
```
Place the mp4create binary in a bin folder in $PATH (~/bin or /usr/local/bin

Give it a try for what you want to do, ex. here - 
```
doug@doug-Lenovo-IdeaPad-Y510P:~$ mp4creator -create=5.aac foo.m4a
Warning: dropped 255 input bytes at offset 0
Warning: dropped 255 input bytes at offset 0
doug@doug-Lenovo-IdeaPad-Y510P:~$ 
```

(- still think ffmpeg could do this...

---

### Post by ron998 on 2016-12-17
> **mc4man said:**
> ...Give it a try...
That's great.
Thanks. ;)
I will use your files instead of trying to build it for myself.

:guitar:

```
~ $ ldd /usr/local/bin/mp4creator
    linux-vdso.so.1 =>  (0x00007ffd085c4000)
    libmp4v2.so.0 => /usr/local/lib/libmp4v2.so.0 (0x00007ff68e497000)
    libmp4av.so.0 => /usr/local/lib/libmp4av.so.0 (0x00007ff68e280000)
    libmpeg4ip_gnu.so.0 => /usr/local/lib/libmpeg4ip_gnu.so.0 (0x00007ff68e07d000)
    libismacryp.so.0 => /usr/local/lib/libismacryp.so.0 (0x00007ff68de79000)
    libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007ff68dc75000)
    libstdc++.so.6 => /usr/lib/x86_64-linux-gnu/libstdc++.so.6 (0x00007ff68d8f2000)
    libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007ff68d5e9000)
    libgcc_s.so.1 => /lib/x86_64-linux-gnu/libgcc_s.so.1 (0x00007ff68d3d3000)
    libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007ff68d009000)
    /lib64/ld-linux-x86-64.so.2 (0x00005649a6905000)
```

```
~ $ mp4creator -version
mp4creator - mpeg4ip version 1.6
```

```
~ $ mp4creator -create=foo.aac foo.m4a
~ $ mediainfo foo.m4a
General
Complete name                            : foo.m4a
Format                                   : MPEG-4
Format profile                           : Base Media / Version 2
Codec ID                                 : mp42 (mp42/isom)
File size                                : 27.8 MiB
Duration                                 : 30 min 0 s
Overall bit rate mode                    : Variable
Overall bit rate                         : 130 kb/s
Encoded date                             : UTC 2016-12-17 23:05:46
Tagged date                              : UTC 2016-12-17 23:05:46
Writing application                      : mp4creator 1.6

Audio
ID                                       : 1
Format                                   : AAC
Format/Info                              : Advanced Audio Codec
Format profile                           : LC
Codec ID                                 : 40
Duration                                 : 30 min 0 s
Bit rate mode                            : Variable
Bit rate                                 : 128 kb/s
Maximum bit rate                         : 132 kb/s
Channel(s)                               : 2 channels
Channel positions                        : Front: L R
Sampling rate                            : 48.0 kHz
Frame rate                               : 46.875 FPS (1024 spf)
Compression mode                         : Lossy
Stream size                              : 27.5 MiB (99%)
Language                                 : English
Encoded date                             : UTC 2016-12-17 23:05:46
Tagged date                              : UTC 2016-12-17 23:05:46


```

---

### Post by mc4man on 2016-12-17
Great, rare case where the old binary & libs could be re-used.
For info, source & procedure

Last ubuntu builds - 
[https://launchpad.net/ubuntu/+source/mpeg4ip/1:1.6dfsg-0.2ubuntu9](https://launchpad.net/ubuntu/+source/mpeg4ip/1:1.6dfsg-0.2ubuntu9)

Extracted the binary from mpeg4ip-server package, ran an ldd on it, 3 missing .so's
Found missing .so's in libmpv4v2-0 & libmpeg4ip-0 packages, ran ldd's on them, 1 missing
Found that missing in one of the above, an ldd on it came up clean so the ldd circle was closed.

No real guarantee the binary would work properly or fully, only that it would run. Apparently it can do what you need it for..

---

### Post by ymliang on 2017-01-02
HI mc4man, I download the attached folder: mp4ip.tar.gz which you supported, but I found that the files in folder are in this format: *.so.0.0.0, but mp4creator need files in this format: *.so.0, so mistakes appear... Could you help how to get the files in format: *.so.0? Thanks very much
[IMG]file:///C:/Users/liangyameng/Desktop/1.jpg[/IMG]

---

### Post by ymliang on 2017-01-03
Now the problem is solved! I copy the *.so.0.0.0 files to path: /lib64/ , then I can use mp4creator. Thankyou all the way~

---

