---
title: "wxcam not working in trusty 14.04"
date: 2014-05-22
forum: Multimedia Software
---

### Post by jflight.bump on 2014-05-22
Just upgraded to **trusty 14.04** (*64*-bit)  and **wxcam** worked well in previous version 13.05 (*64*-bit)  saucy with xubuntu.
I tried reinstalling wxcam and the error I got was **libmjpegtools 19 >= required** in short!
went to the software centre and the version installed is version libmjpegtools 2.
I removed the installed version and reinstalled them with no luck.
any idea??

---

### Post by jflight.bump on 2014-05-22
Cheese works but wxcam has better functional addons ( movement detection is most important)

---

### Post by Toz on 2014-05-22
Are you trying to install the deb file from [http://wxcam.sourceforge.net/?](http://wxcam.sourceforge.net/?) If so, the libmjpegtools-19 package is no longer in the repositories (it was deleted some Ubuntu versions ago). There doesn't appear to be pre-packaged version of wxcam for 14.04 (at least that I can find). 

However, you can compile/build the package yourself (instructions at [http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)). I was able to build the package successfully using the following process:[LIST=1]
[*]install build essential packages
```
sudo apt-get install build-essential
```
[*]install wxcam required packages
```
sudo apt-get install libwxgtk2.8-0 libwxgtk2.8-dev libxvidcore4 libxvidcore-dev libv4l-dev cimg-dev libmjpegtools-dev libasound2-dev libgtk2.0-0 libgtk2.0-dev libglade2-dev intltool
```
[*]The 64-bit fix was not needed.
[*]download the source from [http://sourceforge.net/projects/wxcam/files/wxcam/1.1/wxcam-1.1.tar.gz/download]("http://sourceforge.net/projects/wxcam/files/wxcam/1.1/wxcam-1.1.tar.gz/download")
[*]prepare, build and install the package
```
tar xzvf wxcam-1.1.tar.gz
cd wxcam-1.1
./configure
make
sudo make install
```
[*]execute it
```
wxcam
```
[*]
[/LIST]

---

### Post by jflight.bump on 2014-05-24
get  An error on the second step(install wxcam required packages) E: Unable to locate package cimg

---

### Post by Toz on 2014-05-24
> **jflight.bump said:**
> get  An error on the second step(install wxcam required packages) E: Unable to locate package cimg

Sorry, that should have been **cimg-dev**. I've corrected my post.

---

### Post by jflight.bump on 2014-05-26
when entering wxcam at the end I got this error
assertion failed!

../src/common/intl.cpp(358): assert "!(flags & 
wxLOCALE_CONV_ENCODING)" failed in Init(): 
wxLOCALE_CONV_ENCODING is no longer supported, add charset to your catalogs

ASSERT INFO:
../src/common/intl.cpp(358): assert "!(flags & wxLOCALE_CONV_ENCODING)" failed in Init(): wxLOCALE_CONV_ENCODING is no longer supported, add charset to your catalogs

BACKTRACE:
[1] wxLocale::Init(int, int)
[2] CamApp::OnInit() /home/jaco/Desktop/wxcam-1.1/src/wxcam.cpp:97
[3] wxEntry(int&, wchar_t**)
[4] main /home/jaco/Desktop/wxcam-1.1/src/wxcam.cpp:93
[5] __libc_start_main
[6] _start

---

### Post by Toz on 2014-05-26
What does the following return:
```
uname -a
```

And can you post back the output of the:
```
./configure
```
...and:
```
make
```
...commands when you run them?

---

### Post by jflight.bump on 2014-05-26
uname -a:

```
Linux witsandmarine 3.13.0-27-generic #50-Ubuntu SMP Thu May 15 18:06:16 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

./configure output:
```
jaco@witsandmarine:~$ cd /home/jaco/Desktop/wxcam-1.1
jaco@witsandmarine:~/Desktop/wxcam-1.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking wxWidgets version... 3.0.0
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
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
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking whether NLS is requested... yes
checking for intltool >= 0.35.0... 0.50.2 found
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... (cached) /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for gmsgfmt... (cached) /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for perl >= 5.8.1... 5.18.2
checking for XML::Parser... ok
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /bin/sed
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
checking for dlfcn.h... yes
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking how to run the C++ preprocessor... g++ -E
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
checking whether to build static libraries... yes
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating po/Makefile.in
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing default-1 commands
config.status: executing libtool commands
config.status: executing po/stamp-it commands
jaco@witsandmarine:~/Desktop/wxcam-1.1$ make
```

make:

```
jaco@witsandmarine:~/Desktop/wxcam-1.1$ make
make  all-recursive
make[1]: Entering directory `/home/jaco/Desktop/wxcam-1.1'
Making all in src
make[2]: Entering directory `/home/jaco/Desktop/wxcam-1.1/src'
  CXX    audio.o
  CC     avilib.o
avilib.c: In function &#8216;AVI_open_input_file&#8217;:
avilib.c:646:8: warning: variable &#8216;auds_strf_seen&#8217; set but not used [-Wunused-but-set-variable]
    int auds_strf_seen = 0;
        ^
  CXX    BaseEncoder.o
  CC     ccvt.o
ccvt.c: In function &#8216;ccvt_yuyv&#8217;:
ccvt.c:314:20: warning: variable &#8216;linewidth&#8217; set but not used [-Wunused-but-set-variable]
     int line, col, linewidth;
                    ^
  CXX    cfile.o
  CXX    configure.o
  CXX    device.o
  CXX    filters.o
  CXX    frame.o
  CXX    mddialog.o
  CXX    recording.o
  CXX    resolution.o
  CXX    revelcore.o
  CXX    setting.o
  CXX    uncompressed.o
  CXX    v4l1.o
  CXX    v4l2.o
  CXX    vidiostd.o
  CXX    wxcam.o
  CXX    xvidcodec.o
  CXX    XvidEncoder.o
  CXX    picture.o
  CXX    progressdlg.o
  CXX    motion.o
  CXXLD  wxcam
make[2]: Leaving directory `/home/jaco/Desktop/wxcam-1.1/src'
Making all in po
make[2]: Entering directory `/home/jaco/Desktop/wxcam-1.1/po'
file=`echo it | sed 's,.*/,,'`.gmo \
      && rm -f $file && /usr/bin/msgfmt -o $file it.po
file=`echo es | sed 's,.*/,,'`.gmo \
      && rm -f $file && /usr/bin/msgfmt -o $file es.po
file=`echo pt_BR | sed 's,.*/,,'`.gmo \
      && rm -f $file && /usr/bin/msgfmt -o $file pt_BR.po
file=`echo tr | sed 's,.*/,,'`.gmo \
      && rm -f $file && /usr/bin/msgfmt -o $file tr.po
file=`echo hu | sed 's,.*/,,'`.gmo \
      && rm -f $file && /usr/bin/msgfmt -o $file hu.po
file=`echo fr | sed 's,.*/,,'`.gmo \
      && rm -f $file && /usr/bin/msgfmt -o $file fr.po
make[2]: Leaving directory `/home/jaco/Desktop/wxcam-1.1/po'
make[2]: Entering directory `/home/jaco/Desktop/wxcam-1.1'
make[2]: Leaving directory `/home/jaco/Desktop/wxcam-1.1'
make[1]: Leaving directory `/home/jaco/Desktop/wxcam-1.1'
jaco@witsandmarine:~/Desktop/wxcam-1.1$
```

---

### Post by Toz on 2014-05-26
My configure and make results look the same. I've tried this process on two separate computers and I don't run into these issues. What is your locale currently set to?
```
locale
```

From the error message it looks like its related to wx locale processing ([which was changed a while back]("https://groups.google.com/forum/#!topic/wx-commits-diffs/relrPv7kK90")). You might want to create a [bug report against wxcam]("http://sourceforge.net/p/wxcam/bugs/") for this. I'm not sure how maintained this package is.

---

### Post by jflight.bump on 2014-05-27
jaco@witsandmarine:~$ locale
LANG=en_ZA.UTF-8
LANGUAGE=en_ZA:en
LC_CTYPE="en_ZA.UTF-8"
LC_NUMERIC="en_ZA.UTF-8"
LC_TIME="en_ZA.UTF-8"
LC_COLLATE="en_ZA.UTF-8"
LC_MONETARY="en_ZA.UTF-8"
LC_MESSAGES="en_ZA.UTF-8"
LC_PAPER="en_ZA.UTF-8"
LC_NAME="en_ZA.UTF-8"
LC_ADDRESS="en_ZA.UTF-8"
LC_TELEPHONE="en_ZA.UTF-8"
LC_MEASUREMENT="en_ZA.UTF-8"
LC_IDENTIFICATION="en_ZA.UTF-8"
LC_ALL=

---

### Post by Toz on 2014-05-27
Can you try running it like:
```
LANG=en_US.UTF-8 wxcam
```
...and see if it helps?

---

### Post by jflight.bump on 2014-05-27
I get the same error this is from terminal:

jaco@witsandmarine:~$ LANG=en_US.UTF-8 wxcam
../src/common/intl.cpp(358): assert "!(flags & wxLOCALE_CONV_ENCODING)" failed in Init(): wxLOCALE_CONV_ENCODING is no longer supported, add charset to your catalogs
/dev/video0: Permission denied

---

### Post by jflight.bump on 2014-05-27
Ok just did a software upgrade and I still get the error if I click ok to continue wxcam works any idea how to fix the error?
if not I will need to use it as is and hopefully find the problem at a later stage.

---

### Post by Toz on 2014-05-27
> **jflight.bump said:**
> Ok just did a software upgrade and I still get the error if I click ok to continue wxcam works any idea how to fix the error?
if not I will need to use it as is and hopefully find the problem at a later stage.

Does it display in the correct language? If so, you can probably just ignore the error - it looks like it has something to do with locales - which shouldn't affect the application. If you want, you can try filling in a bug report with the wxcam developers.

---

### Post by jflight.bump on 2014-05-28
The language is correct, but it seems that it struggles to get the program running, I need to start it 2 or 3 times before it starts, once it start it works perfectly. I will send a bug fix to them and post there reply here for others.
Thanks
TOZ

---

### Post by lorrai-m on 2014-05-31
Hi all

I'm the wxcam author. For those who are compiling wxcam from sources, I suggest to download it from cvs. The instructions are in the wxcam website.

To compile the application in release mode (this should avoid the fails of the application due to failed assrtions), change the row in the file nbproject/Makefile-impl.mk:

DEFAULTCONF=Debug
with 
DEFAULTCONF=Release


The new cvs version should resolve the issue wxLOCALE_CONV_ENCODING that throws a failed assert.

Let me know.
Thanks!

---

### Post by Toz on 2014-05-31
@lorrai-m, Welcome to Ubuntuforums. Thank you for posting the solution - always nice to have a developer drop in and clear things up.
Out of curiosity, what is causing the error message? I've compiled and run the tar package successfully a number of time?

---

### Post by usr56432 on 2015-03-13
Please update your post with instruction, it will save someone's nerves and   time. In Ubuntu 14.04.2 LTS (my case),   before any commands, enable "Community-maintained free   and open-source software (universe)". 

1. Ubuntu Software Center > Edit > Software Sources  > Ubuntu  Software > select "Community-maintained free and  open-source  software (universe)" > Close

> **Toz said:**
> Are you trying to install the deb file from [http://wxcam.sourceforge.net/?](http://wxcam.sourceforge.net/?) If so, the libmjpegtools-19 package is no longer in the repositories (it was deleted some Ubuntu versions ago). There doesn't appear to be pre-packaged version of wxcam for 14.04 (at least that I can find). 

However, you can compile/build the package yourself (instructions at [http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)). I was able to build the package successfully using the following process:
[LIST=1]
[*]install build essential packages
```
sudo apt-get install build-essential
``` 
[*]install wxcam required packages
```
sudo apt-get install libwxgtk2.8-0 libwxgtk2.8-dev libxvidcore4 libxvidcore-dev libv4l-dev cimg-dev libmjpegtools-dev libasound2-dev libgtk2.0-0 libgtk2.0-dev libglade2-dev intltool
``` 
[*]The 64-bit fix was not needed. 
[*]download the source from [http://sourceforge.net/projects/wxcam/files/wxcam/1.1/wxcam-1.1.tar.gz/download](http://sourceforge.net/projects/wxcam/files/wxcam/1.1/wxcam-1.1.tar.gz/download) 
[*]prepare, build and install the package
```
tar xzvf wxcam-1.1.tar.gz
cd wxcam-1.1
./configure
make
sudo make install
``` 
[*]execute it
```
wxcam
``` 
[/LIST]


---

### Post by my-names-not on 2015-05-05
[[COLOR=#000000]usr56432[/COLOR]]("http://ubuntuforums.org/member.php?u=1974129")[COLOR=#000000] 's solution w[/COLOR]orked great on 14.04 for me! Thanks

---

