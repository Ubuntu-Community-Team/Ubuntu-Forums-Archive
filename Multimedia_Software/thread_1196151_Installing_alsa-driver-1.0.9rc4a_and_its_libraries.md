---
title: "Installing alsa-driver-1.0.9rc4a and its libraries and utilities"
date: 2009-06-24
forum: Multimedia Software
---

### Post by aaronsnell89 on 2009-06-24
I am trying to install these but when I try to ./configure ; make ; make install get these errors:
The alsa-driver-1.0.9rc4a has around 50 errors some of them are:

error: expected declaration specifiers or ‘...’ before ‘loff_t’

make[1]: *** [hpetimer.o] Error 1
make[1]: Leaving directory `/home/trey/Desktop/alsa-driver-1.0.9rc4a/acore'
make: *** [compile] Error 1

cp: cannot stat `snd-hpet.o': No such file or directory
cp: cannot stat `snd-hwdep.o': No such file or directory
cp: cannot stat `snd-page-alloc.o': No such file or directory
cp: cannot stat `snd-pcm.o': No such file or directory
cp: cannot stat `snd-rawmidi.o': No such file or directory
cp: cannot stat `snd-timer.o': No such file or directory
cp: cannot stat `snd.o': No such file or directory
make[1]: *** [_modinst__] Error 1

and

make[1]: Leaving directory `/home/trey/Desktop/alsa-driver-1.0.9rc4a/acore'
make: *** [install-modules] Error 1

alsa-lib-1.0.9rc4 it says

checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.

and alsa-utils-1.0.9rc4a says

checking for libasound headers version >= 1.0.9... not present.
configure: error: Sufficiently new version of libasound not found.
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.


could anyone help me?

---

### Post by Yellow Pasque on 2009-06-24
Why are you trying to install such an old version of ALSA? Here is a script that builds the latest version: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

---

