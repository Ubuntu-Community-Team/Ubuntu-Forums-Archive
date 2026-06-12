---
title: "Realtek HD Audio Codec"
date: 2008-01-19
forum: Multimedia &amp; Video
---

### Post by Faust942 on 2008-01-19
I'm trying to install my Realtek HD Audio Driver. I downloaded the package from the site, extracted it. Tried in terminal as root, still got this:

root@Faust:/home/joel/Desktop/realtek-linux-audiopack-4.07b# ./install
.....Decompress Driver source v1.0.15-4.07b
.....Decompress ALSA Library source v1.0.14
.....Decompress ALSA Utility v1.0.14
Remove old sound driver
Compile Driver........
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
make all-deps
make[1]: Entering directory `/home/joel/Desktop/realtek-linux-audiopack-4.07b/alsa-driver-hg20080110'
make[1]: Nothing to be done for `all-deps'.
make[1]: Leaving directory `/home/joel/Desktop/realtek-linux-audiopack-4.07b/alsa-driver-hg20080110'

Please, run the configure script as first...

if [ -L /include/sound ]; then \
                rm -f /include/sound; \
                ln -sf /home/joel/Desktop/realtek-linux-audiopack-4.07b/alsa-driver-hg20080110/include/sound /include/sound; \
        else \
                rm -rf /include/sound; \
                install -d -m 755 -g root -o root /include/sound; \
                for f in include/sound/*.h; do \
                        install -m 644 -g root -o root $f /include/sound; \
                done \
        fi
install: cannot stat `include/sound/*.h': No such file or directory
make: *** [install-headers] Error 1
./install: 40: ./snddevices: not found
Remove old alsa library
Compile ALSA Library.....
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
Compile ALSA Utility......
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
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
Remove Folder.....
./install: 101: alsaconf: not found


So what am I getting wrong and what do I need to install? I'm using Ubuntu 7.04 (because I didn't like 7.10)

---

### Post by Candlemass on 2008-05-03
I have the exact same problem with Realtek HD Audio codec on an Acer Aspire 7720G laptop with Kubuntu 8.04 (and 7.10 previously)....

Can't get the drivers to install and I have no sound whatsoever. Kubuntu detects the Realtek chipset as an Intel one... 

Is there a workaround?? thanx in advance!

---

### Post by Allex1 on 2008-05-08
This also happens to me in Ubuntu 8.04... :( waiting for feedback..

---

### Post by jlownie on 2008-05-12
I fixed the problem by installing these packages then doing an automatic install:

build-essential libncurses-dev gettext linux-headers-`uname -r`

More info on this page:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Also this thread might help:

[http://ubuntuforums.org/showthread.php?t=658902](http://ubuntuforums.org/showthread.php?t=658902)

---

