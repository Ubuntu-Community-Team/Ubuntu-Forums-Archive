---
title: "I can't get ANY mp3 players to work"
date: 2007-04-23
forum: Multimedia &amp; Video
---

### Post by Pilot-Doofy on 2007-04-23
I've tried a multitude of open source MP3 players, but none of them work. They all work very similarly in the installation and require the same commands, and they never work. Here is  a copy of what was in Terminal when I tried to install the MP3 player found at this location:
[http://www.mpg123.de/](http://www.mpg123.de/)

In addition, the one at this location gave me a VERY similar, if not exact error:
[http://www.xmms.org/](http://www.xmms.org/)

Terminal:
dan@dan-desktop:~$ cd /home/dan/mpg123-0.65
dan@dan-desktop:~/mpg123-0.65$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
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
checking dependency style of gcc... none
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) none
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking for an ANSI C-conforming const... yes
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking whether byte ordering is bigendian... no
checking for inline... inline
checking POSIX termios... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking for sched_setscheduler... yes
checking for setpriority... yes
checking for sqrt in -lm... yes
checking for powf in -lmx... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for JACK... no
checking for ESOUND... no
checking for SDL... no
checking for AuOpenServer in -laudio... no
checking for Pa_Initialize in -lportaudio... no
checking for snd_pcm_open in -lasound... no
checking for ANSI C header files... (cached) yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking sched.h usability... yes
checking sched.h presence... yes
checking for sched.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking for stdint.h... (cached) yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking sys/soundcard.h usability... yes
checking sys/soundcard.h presence... yes
checking for sys/soundcard.h... yes
checking linux/soundcard.h usability... yes
checking linux/soundcard.h presence... yes
checking for linux/soundcard.h... yes
checking machine/soundcard.h usability... no
checking machine/soundcard.h presence... no
checking for machine/soundcard.h... no
checking sun/audioio.h usability... no
checking sun/audioio.h presence... no
checking for sun/audioio.h... no
checking sys/audioio.h usability... no
checking sys/audioio.h presence... no
checking for sys/audioio.h... no
checking asm/audioio.h usability... no
checking asm/audioio.h presence... no
checking for asm/audioio.h... no
checking sys/audio.h usability... no
checking sys/audio.h presence... no
checking for sys/audio.h... no
checking AudioUnit/AudioUnit.h usability... no
checking AudioUnit/AudioUnit.h presence... no
checking for AudioUnit/AudioUnit.h... no
checking CoreServices/CoreServices.h usability... no
checking CoreServices/CoreServices.h presence... no
checking for CoreServices/CoreServices.h... no
checking AudioToolbox/AudioToolbox.h usability... no
checking AudioToolbox/AudioToolbox.h presence... no
checking for AudioToolbox/AudioToolbox.h... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/config.h
config.status: executing depfiles commands

  mpg123 0.65

  Install path ............ /usr/local
  CPU Optimisation......... mmx
  Compiler Optimization ... 2
  Audio output ............ oss
  Gapless Support ......... enabled
  Debugging ............... disabled
  Seek table size ......... 1000

Next type 'make' and then 'make install'.
dan@dan-desktop:~/mpg123-0.65$ make
bash: make: command not found

Any idea?

---

### Post by jfinkels on 2007-04-23
First, you should install applications using Synaptic or aptitude so you don't have to compile them!

Second, if you really want to compile them, you need the "make" program. To install this and other utilities necessary for compiling many applications, type the following in the terminal:
```

sudo aptitude install build-essential

```

---

### Post by Pilot-Doofy on 2007-04-23
Thanks, I got the commands to work finally! Now, I ran the commands and an error occurred near the bottom. I looked through the Terminal and I found this:

Making install in src
make[1]: Entering directory `/home/dan/mpg123-0.65/src'
make[2]: Entering directory `/home/dan/mpg123-0.65/src'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /usr/bin/install -c 'mpg123' '/usr/local/bin/mpg123'
/usr/bin/install: cannot create regular file `/usr/local/bin/mpg123': Permission denied
make[2]: *** [install-binPROGRAMS] Error 1
make[2]: Leaving directory `/home/dan/mpg123-0.65/src'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/dan/mpg123-0.65/src'
make: *** [install-recursive] Error 1

Then I ran sudo make install and I got this:

dan@dan-desktop:~/mpg123-0.65$ sudo make install
Making install in src
make[1]: Entering directory `/home/dan/mpg123-0.65/src'
make[2]: Entering directory `/home/dan/mpg123-0.65/src'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /usr/bin/install -c 'mpg123' '/usr/local/bin/mpg123'
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/dan/mpg123-0.65/src'
make[1]: Leaving directory `/home/dan/mpg123-0.65/src'
make[1]: Entering directory `/home/dan/mpg123-0.65'
make[2]: Entering directory `/home/dan/mpg123-0.65'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/man/man1" || /bin/mkdir -p "/usr/local/share/man/man1" /usr/bin/install -c -m 644 './mpg123.1' '/usr/local/share/man/man1/mpg123.1'
make[2]: Leaving directory `/home/dan/mpg123-0.65'
make[1]: Leaving directory `/home/dan/mpg123-0.65'
dan@dan-desktop:~/mpg123-0.65$

---

### Post by jfinkels on 2007-04-23
Again, you shouldn't really be compiling programs...but your program is now installed. Now you can run it (probably just type the name of the program in the terminal "mpg123")

---

### Post by Pilot-Doofy on 2007-04-24
I can open files with the command "mpg123" but I guess I just assumed it would have a visualizer. I have another question. I've looked around and it looks like there's never one way to uninstall something.

Is there a pretty solid way of uninstalling a program every time with the same code or similar code? Plus, I had to compile myself because I didn't have any of the programs you talked about.

---

### Post by Pilot-Doofy on 2007-04-24
this forum gets kinda slow..

---

### Post by Swab on 2007-04-24
System > Administration > Synaptic Package Manager

You can install and uninstall programs to your hearts content.  No need to compile.

---

### Post by Pilot-Doofy on 2007-04-24
Thanks Swab! Again guys, I'm sorry. I'm a complete noob at Windows. I just know I'm getting fed up with Microsoft's BS!

---

