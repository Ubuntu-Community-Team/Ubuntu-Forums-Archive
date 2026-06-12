---
title: "Cdrdao with mp3 support"
date: 2008-07-19
forum: Multimedia Software
---

### Post by Dan83A on 2008-07-19
Hi,

It all started with trying to burn a .cue file when I saw that Brasero couldn't do anything with the .mp3 file because the cdrdao came without mp3 support.
So I started looking into it and googling it gave mostly k3b solutions which didn't seem relevant.
I decided to recompile cdrdao and downloaded the source, but running .configure showed me that the problem goes deeper to this:

[I]checking for mad_stream_init in -lmad... no
MP3 support disabled[/I]

and eventually this is what I would have gotten after compiling, which again is not what I want:

[I]------------------------------------------------------
  Building scsilib   : yes
  Building pccts     : yes
  Building cdrdao    : yes
     OGG support     : no
     MP3 support     : no
  Building toc2cue   : yes
  Building cue2toc   : yes
  Building toc2mp3   : no
  Building gcdmaster : no
------------------------------------------------------
[/I]

The system is x86_64 Ubuntu Hardy 8.04, kernel 2.6.24-19-generic.

Any help will be appreciated.

---

### Post by Dan83A on 2008-07-19
Come one guys, please, doesn't anyone have cdrdao with mp3 support?

---

### Post by andrew.46 on 2008-08-04
Hi,

 I am no longer running ubuntu so I have perhaps limited help :-). On a slackware system configure gives me:

```
------------------------------------------------------
  Building scsilib   : yes
  Building pccts     : yes
  Building cdrdao    : yes
     OGG support     : yes
     MP3 support     : yes
  Building toc2cue   : yes
  Building cue2toc   : yes
  Building toc2mp3   : yes
  Building gcdmaster : no
------------------------------------------------------

```

which I guess is closer to what you are after. Ubuntu / Debian slices the source code up a little and you are missing the so-called '-dev' or 'header' files for lame and ogg vorbis. Try a repository search with:

```

$ apt-cache search lame | grep dev
$ apt-cache search ogg  | greb dev
```

and install the suggested files or alternatively download and install the lame source code as well. Sorry I can't be more specific as my Ubuntu knowledge is fading a little :-).

  Andrew

---

### Post by Dan83A on 2008-08-11
It seems to be working after I installed those:

libvorbis-dev
libtwolame-dev
liblame-dev
gcdmaster

And purged + resinstalled cdrdao.

Thanks a lot.

---

### Post by cybrid on 2008-10-12
I know this thread may be closed, but I've run into the same problem and after installing the mentioned packages, I tried to configure cdrdao with 
```

./configure --with-mp3-support --with-ogg-support
``` and still getting 
```
------------------------------------------------------
  Building scsilib   : yes
  Building pccts     : yes
  Building cdrdao    : yes
     OGG support     : no
     MP3 support     : no
  Building toc2cue   : yes
  Building cue2toc   : yes
  Building toc2mp3   : yes
  Building gcdmaster : no
------------------------------------------------------
```
Any ideas?

This is the full configure output but I haven't been able to see anything abnormal.
```

xabi@rhuidean:~/Escritorio/cdrdao-1.2.2$ ./configure --with-mp3-support --with-ogg-support --with-lame
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking for ar... ar
checking whether make sets $(MAKE)... (cached) yes
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking getopt.h usability... yes
checking getopt.h presence... yes
checking for getopt.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking for unistd.h... (cached) yes
checking sys/mman.h usability... yes
checking sys/mman.h presence... yes
checking for sys/mman.h... yes
checking sched.h usability... yes
checking sched.h presence... yes
checking for sched.h... yes
checking whether byte ordering is bigendian... no
checking return type of signal handlers... void
checking for short... yes
checking size of short... 2
checking for int... yes
checking size of int... 4
checking for long... yes
checking size of long... 8
checking for long long... yes
checking size of long long... 8
checking for u_int8_t... yes
checking for int16_t... yes
checking for int32_t... yes
checking for u_int16_t... yes
checking for u_int32_t... yes
checking for sched_getparam... yes
checking for sched_get_priority_max... yes
checking for sched_setscheduler... yes
checking for socket in -lsocket... no
checking for connect in -lsocket... no
checking for gethostbyname in -lnsl... yes
checking for inet_addr in -lnsl... yes
checking for inet_ntoa in -lnsl... yes
checking for strerror... yes
checking for mlockall... yes
checking for munlockall... yes
checking for getpagesize... yes
checking for usleep... yes
checking for setreuid... yes
checking for setregid... yes
checking for seteuid... yes
checking for setegid... yes
checking for setuid... yes
checking for setgid... yes
checking for inet_aton... yes
checking for pthread_create... no
checking for pthread_create in -lpthread... yes
checking for pthread_sigmask in -lpthread... yes
checking for pthread_attr_setschedpolicy in -lpthread... yes
checking for pthread_attr_setschedparam in -lpthread... yes
checking for pthread_getschedparam in -lpthread... yes
checking for pthread_setschedparam in -lpthread... yes
checking for Lame library version >= 3.92... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for SIGCPP2... Building of gcdmaster disabled
checking for GTKMM2... Building of gcdmaster disabled
checking for LIBGUIMM2... Building of gcdmaster disabled
checking for VORBISFILE... yes
checking for MAD... yes
checking for AO... Building of gcdmaster disabled
configure: creating ./config.status
config.status: creating trackdb/Makefile
config.status: creating dao/Makefile
config.status: creating utils/Makefile
config.status: creating xdao/Makefile
config.status: creating xdao/stock/Makefile
config.status: creating paranoia/Makefile
config.status: creating pccts/Makefile
config.status: creating pccts/antlr/Makefile
config.status: creating pccts/dlg/Makefile
config.status: creating Makefile
config.status: creating specs/cdrdao.fedora.spec
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands

------------------------------------------------------
  Building scsilib   : yes
  Building pccts     : yes
  Building cdrdao    : yes
     OGG support     : no
     MP3 support     : no
  Building toc2cue   : yes
  Building cue2toc   : yes
  Building toc2mp3   : yes
  Building gcdmaster : no
------------------------------------------------------
```

---

### Post by Dan83A on 2008-10-12
I'm guessing that you did whatever Andrew suggested and what I did, right?

It's been a while since then but I know that after all that, I installed nero for linux and everything worked fine (while before that, nero failed as well).

---

### Post by cybrid on 2008-10-12
Yes, I installed 

libvorbis-dev
libtwolame-dev
liblame-dev
gcdmaster

by means of aptitude and tried to "./configure" it. In fact I'd like to make a package of it, if it's possible, although I have yet to learn how to build packages :)

---

### Post by andrew.46 on 2008-10-17
Hi,

Well I have an Intrepid Ibex install now and I cannot get these 2 options to work either. A bit of a mystery.

  Andrew

---

### Post by andrew.46 on 2008-11-29
Hi,

Woooo hoooooo!!! Managed the following on Intrepid Ibex:
```

------------------------------------------------------
  Building scsilib   : yes
  Building pccts     : yes
  Building cdrdao    : yes
     OGG support     : yes
     MP3 support     : yes
  Building toc2cue   : yes
  Building cue2toc   : yes
  Building toc2mp3   : yes
  Building gcdmaster : no
------------------------------------------------------
```

There was of course a missing dependency: 

```
libao-dev - Cross Platform Audio Output Library Development
```

so hopefully a simply:

```
sudo apt-get install libao-dev
```

should get you out of trouble :-). Mind you an even easier method is to try:

```
sudo apt-get build-dep cdrdao
```

and I note this also allows the building o the gcdmaster option.

  All the best,

    Andrew

---

### Post by cybrid on 2008-11-30
Wow, thanks a lot andrew ;) I'll be sure to try it when I come back home on Tuesday.

---

### Post by andrew.46 on 2008-12-03
Hi,

Well the plot has thickened somewhat I am afraid :-). I had a few troubles compiling cdrdao and was a little worried that I had given you bum advice! However all is solved now and if you are happy with a little work the program can be compiled with all options under Intrepid.

There is a known problem with compiling the release version of cdrdao under gcc 4.3.x and this has been addressed under the cvs cdrdao. However a patch is required for this to work with the release version under gcc 4.3.x. I have used the patch available here:

[http://bugs.gentoo.org/show_bug.cgi?id=213191](http://bugs.gentoo.org/show_bug.cgi?id=213191)

or more specifically this one:

[http://bugs.gentoo.org/attachment.cgi?id=151679](http://bugs.gentoo.org/attachment.cgi?id=151679)

So the procedure that worked for me:

```
$ sudo apt-get build-dep cdrdao
$ sudo apt-get build-essential checkinstall
$ wget http://downloads.sourceforge.net/cdrdao/cdrdao-1.2.2.tar.bz2
$ tar xjvf cdrdao-1.2.2.tar.bz2
$ wget http://bugs.gentoo.org/attachment.cgi?id=151679 -O cdrdao-1.2.2-gcc43.patch 
$ cd cdrdao-1.2.2
$ patch -p1 < ../cdrdao-1.2.2-gcc43.patch 
$ ./configure
$ make
$ sudo checkinstall --fstrans=no
```

Let me know if this works out, certainly worked on my system. 

  Andrew

**Edit:** Wooo hooo! Even the gcdmaster worked with this compile which never seemed to work with the reposiory version.

---

### Post by rustyco on 2009-06-07
Hey, thanks for this tip. I did

sudo apt-get install libao-dev
and was able to configure --with-mp3-support.

---

### Post by andrew.46 on 2009-06-07
Hi rustyco,

> **rustyco said:**
> Hey, thanks for this tip. I did

sudo apt-get install libao-dev
and was able to configure --with-mp3-support.

My pleasure :-). I will admit that I had forgotten this older post of mine and I marvel a little at how much research I put into it at the time!

All the best,

Andrew

---

