---
title: "Ubuntu Noob can't install GTKPod"
date: 2007-01-11
forum: Multimedia &amp; Video
---

### Post by rollnrock on 2007-01-11
Hi All,

I've been trying to install GTKPod with limited success. I have resolved some dependency issues like gcc not being installed etc. However, I can't seem to get past the current one. I receive the following when running ./configure:

rollie@Kubuntu1:~/gtkpod-0.99.8$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for style of include used by make... none
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... none
checking for strerror in -lcposix... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) none
checking for gcc option to accept ANSI C... none needed
checking for pkg-config... ok
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PACKAGE... no
configure: error: *** No package 'libgpod-1.0' found
See `config.log' for more details.
rollie@Kubuntu1:~/gtkpod-0.99.8$  


I've been searching the forums, and any other sources I could find for more info on how to resolve the latest issue but come up empty.

Can anyone offer some assistance?

Thanks,

rollnrock

---

### Post by meng on 2007-01-11
Why install from source code? Use the repositories to install:
[www.psychocats.net/ubuntu/installingsoftware](www.psychocats.net/ubuntu/installingsoftware)

For gtkpod, you'll need to enable universe repositories
[http://psychocats.net/ubuntu/sources](http://psychocats.net/ubuntu/sources)

then
sudo aptitude update
sudo aptitude install gtkpod

---

### Post by insanitywetrust on 2007-01-31
hi there
i read thru this posting, and have managed to get the gtkpod installed
using the psychocats pages....

however, it then says the mp3 files i tried to import are not an audio stream

is there some trick needed to convert this or something?

i read thru the help files or manual, and no help on this

---

### Post by dpmccoy on 2007-01-31
I can make this even easier for you.

Since your prompt says that you're using Kubuntu, use Automatix to install the I-Pod libraries.  Once you do that, you can use Amarok as an I-Tunes replacement.  It will sync your music to your I-Pod just as well as GTKPod, if not better.  

I used GTKPod for several months earlier last year, and I'm happier with the Amarok option.  It might work better for you as well.

Good luck!

---

