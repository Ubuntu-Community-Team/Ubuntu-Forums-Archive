---
title: "Need help with IDJC, Choppy and can't install correctly"
date: 2009-04-21
forum: Multimedia Software
---

### Post by EvilBear on 2009-04-21
Followed instructions in the IDJC's install guide till i got this...

evilbear@evilbear-laptop:~/idjc-0.7.14$ ./configure CFLAGS="-02"
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for a Python interpreter with version >= 2.4... python
checking for python... /usr/bin/python
checking for python version... 2.5
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.5/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.5/site-packages
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
checking whether gcc and cc understand -c and -o together... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for JACK... configure: error: Package requirements (jack >= 0.98.0) were not met:

No package 'jack' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables JACK_CFLAGS
and JACK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

evilbear@evilbear-laptop:~/idjc-0.7.14$ make
make: *** No targets specified and no makefile found. Stop.



anyone know what to do to fix that? I really have just been following instructions. The programs audio is all choppy.

---

### Post by johnh10000 on 2009-07-18
No package 'jack' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.



anyone know what to do to fix that? I really have just been following instructions. The programs audio is all choppy.[/QUOTE]

I compiled the latest one this morn.  I had similar issues:

how Idid it.  Put jack-dev for example bang it into synaptic and get that one.
don't shut synaptic, I think there 2 or 3 more.

It want the deveopment libraies.

oh I think it's .17 is out now

hope that helps

---

