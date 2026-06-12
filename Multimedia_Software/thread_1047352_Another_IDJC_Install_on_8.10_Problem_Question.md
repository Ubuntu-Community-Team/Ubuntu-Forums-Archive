---
title: "Another IDJC Install on 8.10 Problem Question"
date: 2009-01-22
forum: Multimedia Software
---

### Post by BennieBlount on 2009-01-22
Has ANYONE got IDJC to install on Ubuntu 8.10 with the SHOUTCAST option working? 

I have tried installing with Synaptic, The Add-Remove Programs, and apt-get. I also followed the the steps at [http://ubuntuforums.org/showpost.php?p=5200135&postcount=5](http://ubuntuforums.org/showpost.php?p=5200135&postcount=5).  

Every time the SHOUTCAST option for the server is greyed out - not available.

No theories, please - just need to know how to install from someone who has the SHOUTCAST option working.

Thanks,

Bennie

---

### Post by StephenF on 2009-01-23
You need to uninstall IDJC in synaptic *then* follow the instructions in that link you posted.

To use shoutcast the mp3 option must also be chosen.

---

### Post by depert on 2009-01-27
same here.
i have install using the source (tar.gz). When i launch idjc, shoutcast option can not be used (blank) so i cannot stream mp3 files. 

I'm using intrepid and i have install libmp3lame-dev. Is there another solution ?

FYI: When i configure (./configure CFLAGS="-O2")
checking for lame_init in -lmp3lame -lm... no
configure: WARNING: IDJC will be built without mp3 streaming support

---

### Post by depert on 2009-01-27
Solved
just update libmp3lame-dev, libmp3lame0 and lame from this url:
[http://debian-multimedia.org/pool/main/l/lame/lame.php](http://debian-multimedia.org/pool/main/l/lame/lame.php)
and compile the latest version idjc from source.

Add option --enable-lame when configure after extract tar.gz file,

./configure --enable-lame
make 
sudo make install

now, shoutcast tab active. i hope it works to you too.

---

### Post by Naiki Muliaina on 2009-01-27
Ive found IDJC to be a bit naff. Takes so much tweaking to get it going when i have a game or something else that uses me sound card. To much effort for something that should be so simple. I just use Shoutcasts main program to broadcast shoutcast now (see sig for how i do it).

---

### Post by EvilBear on 2009-04-21
Following instructions in that link till i got this...

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
make: *** No targets specified and no makefile found.  Stop.



anyone know what to do after that?

---

### Post by mackay12 on 2009-05-05
I too have the problem above, how do i make and install it?

---

### Post by Kenchappagoudra on 2009-11-24
Guys,

 I have the same problem too. I followed all the steps from provided link. When I try to configure using./configure CFLAGS="-O2"  I get a message saying;

checking for JACK... configure: error: Package requirements (jack >= 0.98.0) were not met:

No package 'jack' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables JACK_CFLAGS
and JACK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

I have tried settiing PKG_CONFIG_PATH value, but it did not work. Error repeated.

I have been trying to fix this problem for the past two days. Could anyone please help me.


Thank you

---

### Post by NeoZiggy on 2009-11-27
To solve the JACK issue install libjack-dev  ;)
```
sudo apt-get install libjack-dev
```

---

