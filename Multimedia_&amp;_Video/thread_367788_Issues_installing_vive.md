---
title: "Issues installing vive"
date: 2007-02-22
forum: Multimedia &amp; Video
---

### Post by fearevilleet on 2007-02-22
Hello,

I am trying to install vive but am unable to do so. 

When I do ./configure I get 

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for ffmpeg... yes
checking for vobcopy... no
checking for mplayer... yes
checking for prefix by checking for ffmpeg... /usr/bin/ffmpeg
checking whether DVD is enabled... yes
configure: error: You have enabled DVD usage but do not have vobcopy installed. If you would not like to e
nable DVD usage or would not like install vobcopy use the --disable-dvd option.

```

When I do ./INSTALL I get

```
evilleet@box:~/vive-2.0.0-beta1$ ./INSTALL
./INSTALL: line 1: syntax error near unexpected token `C'
./INSTALL: line 1: `Copyright (C) 1994, 1995, 1996, 1999, 2000, 2001, 2002 Free Software'
evilleet@box:~/vive-2.0.0-beta1$

```

I was unable to figure out how to fix this by searching the fourms, could someone please point me in the right direction.

---

### Post by Old Pink on 2007-02-22
2.0.0 is a BETA release, try the latest stable release?

---

### Post by Old Pink on 2007-02-22
To confirm, 2.0.0 is the first release in C. 

Vive 1.0.2 will work on your system, and is actually very similar to 2.0.0, you're not missing out on anything.

Vive 1.0.2:
[http://downloads.sourceforge.net/vive/vive-1.0.2.tar.gz?modtime=1159810081&big_mirror=0](http://downloads.sourceforge.net/vive/vive-1.0.2.tar.gz?modtime=1159810081&big_mirror=0)

---

### Post by fearevilleet on 2007-02-22
Thanks, I was able to install a stable version. Now when I go to load vive I get

```
evilleet@box:~/vive-1.0.2$ ./vive
Failed to open file '/usr/share/pixmaps/vive.xpm': No such file or directory at ./vive line 1844.
evilleet@box:~/vive-1.0.2$ 

```

Any ideas?

---

### Post by xfile087 on 2007-02-24
> **fearevilleet said:**
> Thanks, I was able to install a stable version. Now when I go to load vive I get

```
evilleet@box:~/vive-1.0.2$ ./vive
Failed to open file '/usr/share/pixmaps/vive.xpm': No such file or directory at ./vive line 1844.
evilleet@box:~/vive-1.0.2$ 

```

Any ideas?

I'm not an expert and I don't have the same problem but perhaps if you tried copying vive.xmp to /usr/share/pixmaps it may work?

All I did was the following and it worked flawlessly.

> ./configure
make
checkinstall


---

### Post by lisa on 2007-02-28
> **fearevilleet said:**
> Hello,

I am trying to install vive but am unable to do so. 

When I do ./configure I get 

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for ffmpeg... yes
checking for vobcopy... no
checking for mplayer... yes
checking for prefix by checking for ffmpeg... /usr/bin/ffmpeg
checking whether DVD is enabled... yes
configure: error: You have enabled DVD usage but do not have vobcopy installed. If you would not like to e
nable DVD usage or would not like install vobcopy use the --disable-dvd option.

```

When I do ./INSTALL I get

```
evilleet@box:~/vive-2.0.0-beta1$ ./INSTALL
./INSTALL: line 1: syntax error near unexpected token `C'
./INSTALL: line 1: `Copyright (C) 1994, 1995, 1996, 1999, 2000, 2001, 2002 Free Software'
evilleet@box:~/vive-2.0.0-beta1$

```

I was unable to figure out how to fix this by searching the fourms, could someone please point me in the right direction.

You need to install vobcopy first, before you run the install-Script!!!!!

---

