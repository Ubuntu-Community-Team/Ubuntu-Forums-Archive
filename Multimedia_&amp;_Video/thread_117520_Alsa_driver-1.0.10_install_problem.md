---
title: "Alsa driver-1.0.10 install problem"
date: 2006-01-15
forum: Multimedia &amp; Video
---

### Post by garconcn on 2006-01-15
I have intel HDA sound card in my Asus w5a laptop, there is no sound after I install the Ubuntu. 

I followed the steps how to install alsa in [http://alsa.opensrc.org/Quick+Install](http://alsa.opensrc.org/Quick+Install)  , but when I run ./configure --with-sequencer=yes --with-kernel=/usr/src/linux && make, it got a problem that :
```
The file /usr/src/linux/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).

```
I don't know where is the dir. 

Thank you very much for any help.:)

---

### Post by garconcn on 2006-01-15
My soundcard work now even haven't install Utils.
-----------------------
I solved this problem by install kernel head:p 

I had finished c[COLOR="Red"]ompile & install the drivers[/COLOR] and [COLOR="Red"]ALSA libraries[/COLOR]

but when I [COLOR="Blue"]install ALSA Utils[/COLOR]:
got this:
------------------------------------
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.10/alsaconf'
Making all in po
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.10/alsaconf/po'
mv: cannot stat `t-ja.gmo': No such file or directory
make[2]: *** [ja.gmo] Error 1
----------------------------------------

```
root@ubuntu:/usr/src/alsa/alsa-utils-1.0.10# ./configure && make
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether NLS is requested... yes
checking for msgfmt... no
checking for gmsgfmt... :
checking for xgettext... no
checking for msgmerge... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking build system type... i686-pc-linux
checking host system type... i686-pc-linux
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking whether NLS is requested... yes
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for cross-compiler... gcc
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for ALSA CFLAGS...
checking for ALSA LDFLAGS...  -lasound -lm -ldl -lpthread
checking for libasound headers version >= 1.0.9... found.
checking for snd_ctl_open in -lasound... yes
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for initscr in -lncurses... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for _LARGE_FILES value needed for large files... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating alsactl/Makefile
config.status: creating alsamixer/Makefile
config.status: creating amidi/Makefile
config.status: creating amixer/Makefile
config.status: creating m4/Makefile
config.status: creating po/Makefile.in
config.status: creating alsaconf/alsaconf
config.status: creating alsaconf/Makefile
config.status: creating alsaconf/po/Makefile
config.status: creating aplay/Makefile
config.status: creating include/Makefile
config.status: creating iecset/Makefile
config.status: creating utils/Makefile
config.status: creating utils/alsa-utils.spec
config.status: creating seq/Makefile
config.status: creating seq/aconnect/Makefile
config.status: creating seq/aplaymidi/Makefile
config.status: creating seq/aseqdump/Makefile
config.status: creating seq/aseqnet/Makefile
config.status: creating speaker-test/Makefile
config.status: creating speaker-test/samples/Makefile
config.status: creating include/aconfig.h
config.status: include/aconfig.h is unchanged
config.status: executing default-1 commands
config.status: creating po/POTFILES
config.status: creating po/Makefile
config.status: executing depfiles commands
Making all in include
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.10/include'
make  all-am
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.10/include'
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.10/include'
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.10/include'
Making all in alsactl
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.10/alsactl'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.10/alsactl'
Making all in alsaconf
[COLOR="Red"]make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.10/alsaconf'
Making all in po
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.10/alsaconf/po'
mv: cannot stat `t-ja.gmo': No such file or directory
make[2]: *** [ja.gmo] Error 1[/COLOR]
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.10/alsaconf/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.10/alsaconf'
make: *** [all-recursive] Error 1
root@ubuntu:/usr/src/alsa/alsa-utils-1.0.10#


```

---

