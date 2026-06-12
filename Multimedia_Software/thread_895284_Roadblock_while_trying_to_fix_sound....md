---
title: "Roadblock while trying to fix sound..."
date: 2008-08-20
forum: Multimedia Software
---

### Post by youknowwhat4q on 2008-08-20
So I've been having what seems to be a pretty common issue where there is no sound to speak of, but I think that this:

[I]# webbca01 figured out how to get AC'97 work with the help of the second last post here and this post. Basically, if you have an intel8x0 module, you can get AC'97 working by
Code:

sudo nano /etc/modprobe.d/alsa-base

and adding this as the last line:
Code:

"options snd-intel8x0 ac97_quirk=3"
[/I]
may work.  Only problem, it that once I input [sudo nano /etc/modprobe.d/alsa-base] it prompts me for a password, but will not allow me to input any text.

Suggestions?

---

### Post by eggdeng on 2008-08-20
> will not allow me to input any text
When you input a password in the terminal, there is no response other than the blinking cursor until you hit intro.

---

### Post by youknowwhat4q on 2008-08-21
Haha, wow do I feel like a fool.

Thanks.

---

### Post by youknowwhat4q on 2008-08-26
I thought I posted again, but I guess it didn't go through.

The sound is still malfunctioning, and recently decided that it can't find the sound card.  Now I'm completely lost.

I'm on the third step of the [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449").  Having trouble trying to figure out what what to do from here.  The Alsa site just sent me to [this page.]("http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0")  Which might as well be written in Chinese.

---

### Post by eggdeng on 2008-08-27
Basically, both pages are telling you the same thing.
Download the latest version of alsa (1.0.17) from 
[http://www.alsa-project.org/main/index.php/Main_Page]("http://www.alsa-project.org/main/index.php/Main_Page")

Download and install the linux-headers file
```
sudo apt-get install build-essential linux-headers-$(uname -r)
```
Create a folder for the installation
```
sudo mkdir /usr/src/alsa
```
Assuming the file has downloaded to your desktop, move it to your /usr/src/alsa folder
```
sudo mv ~/Desktop/alsa-driver-1.0.17.tar.bz2 /usr/src/alsa
```
Move to /usr/src/alsa
```
cd /usr/src/alsa
```
Now, extract the file
```
tar xvjf /alsa-driver-1.0.17.tar.bz2
```
Change to the extracted file folder
```
cd alsa-driver-1.0.17
```
Configure and install
```
sudo ./configure --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=Intel8x0 --with-sequencer=yes --with-oss=yes
``` 
```
sudo make 
```
```
sudo make install
```

Edit: Follow additional steps inserted 2 posts down.

Load the modules
```
modprobe snd-intel8x0 ; modprobe snd-pcm-oss ; modprobe snd-mixer-oss ; modprobe snd-seq-oss
```
The driver is now installed and loaded. You can now type
```
alsamixer
``` and play around with the settings. & you can try to play some sounds.

---

### Post by youknowwhat4q on 2008-08-27
```
amanda@amanda-laptop:/usr/src/alsa/alsa-driver-1.0.17$ sudo ./configure --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=Intel8x0 --with-sequencer=yes --with-oss=yes
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

```

I'm lost once again.  Thank you so much for the step by step, I really appreciate it.

---

### Post by eggdeng on 2008-08-28
Run
```
sudo apt-get install libc6-dev g++ gcc
```
Make sure you are in the alsa-driver-1.0.17 directory and run the configure command again.

Before you go on to the step 'Load the modules', download the following additional packages from
[http://www.alsa-project.org/main/index.php/Main_Page]("http://www.alsa-project.org/main/index.php/Main_Page")
```
alsa-lib-1.0.17a
alsa-utils-1.0.17
```

As before, move them to your installation folder
```
sudo mv ~/Desktop/alsa-lib-1.0.17a.tar.bz2 /usr/src/alsa
sudo mv ~/Desktop/alsa-utils-1.0.17.tar.bz2 /usr/src/alsa
```

Again, as before, unzip and install the alsa-lib package

```
cd /usr/src/alsa
bunzip2 alsa-lib-1.0.17a
tar -xf alsa-lib-1.0.17a
cd alsa-lib-alsa-lib-1.0.17a
sudo ./configure ; make ; make install
```

Unzip and install the alsa-utils package

```
cd /usr/src/alsa
bunzip2 alsa-utils-1.0.17
tar -xf alsa-utils-1.0.17
cd alsa-utils-1.0.17
sudo ./configure ; make ; make install
```

Go on to the step 'Load the Modules'.

---

### Post by youknowwhat4q on 2008-08-28
```
root@amanda-laptop:/usr/src/alsa/alsa-utils-1.0.17# sudo ./configure ; make ; make install
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
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for cross-compiler... gcc
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for ALSA CFLAGS... 
checking for ALSA LDFLAGS...  -lasound -lm -ldl -lpthread
checking for libasound headers version >= 1.0.16... found.
checking for snd_ctl_open in -lasound... yes
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for ncurses5-config... yes
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
config.status: WARNING:  alsaconf/po/Makefile.in seems to ignore the --datarootdir setting
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
config.status: executing po-directories commands
config.status: creating po/POTFILES
config.status: creating po/Makefile
config.status: executing depfiles commands
Making all in include
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.17/include'
make  all-am
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.17/include'
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.17/include'
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.17/include'
Making all in alsactl
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.17/alsactl'
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT alsactl.o -MD -MP -MF ".deps/alsactl.Tpo" -c -o alsactl.o alsactl.c; \
	then mv -f ".deps/alsactl.Tpo" ".deps/alsactl.Po"; else rm -f ".deps/alsactl.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT state.o -MD -MP -MF ".deps/state.Tpo" -c -o state.o state.c; \
	then mv -f ".deps/state.Tpo" ".deps/state.Po"; else rm -f ".deps/state.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT names.o -MD -MP -MF ".deps/names.Tpo" -c -o names.o names.c; \
	then mv -f ".deps/names.Tpo" ".deps/names.Po"; else rm -f ".deps/names.Tpo"; exit 1; fi
gcc  -g -O2   -o alsactl  alsactl.o state.o names.o  -lasound -lm -ldl -lpthread
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.17/alsactl'
Making all in alsaconf
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.17/alsaconf'
Making all in po
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.17/alsaconf/po'
mv: cannot stat `t-ja.gmo': No such file or directory
make[2]: *** [ja.gmo] Error 1
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.17/alsaconf/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.17/alsaconf'
make: *** [all-recursive] Error 1
Making install in include
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.17/include'
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.17/include'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.17/include'
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.17/include'
Making install in alsactl
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.17/alsactl'
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.17/alsactl'
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
  /usr/bin/install -c 'alsactl' '/usr/sbin/alsactl'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsactl.1' '/usr/share/man/man1/alsactl.1'
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.17/alsactl'
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.17/alsactl'
Making install in alsaconf
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.17/alsaconf'
Making install in po
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.17/alsaconf/po'
mv: cannot stat `t-ja.gmo': No such file or directory
make[2]: *** [ja.gmo] Error 1
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.17/alsaconf/po'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.17/alsaconf'
make: *** [install-recursive] Error 1

```

I got this error while installing alsa-lib as well, but it worked fine once I switched to root it was fine.

---

### Post by youknowwhat4q on 2008-08-30
I figured it out, I'll put up how I did it later, not time now.

---

