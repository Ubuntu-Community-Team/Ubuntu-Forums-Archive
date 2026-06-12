---
title: "xbmc, where did it install to, how do i open the program?"
date: 2009-06-13
forum: Multimedia Software
---

### Post by xfearxnxloathing on 2009-06-13
just did fresh install and reboot, dont see it listed in any drop down menu from the start bar.  anyone tell me where an icon or how to start the program please!?!

---

### Post by kruykaze on 2009-06-13
all you have to do is run xbmc in terminal and see what it says.
I have mine under sound and video.I installed from the repos.

---

### Post by xfearxnxloathing on 2009-06-18
apparently its not installed..  yet is why, i get this error when i do ```
./configure
```

```
~/XBMC$ ./configure
configure: Ensuring config.guess and config.sub exist and is executable
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for ccache... none
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for gawk... no
checking for mawk... mawk
checking whether ln -s works... yes
checking whether make sets $(MAKE)... yes
checking how to run the C++ preprocessor... g++ -E
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
checking boost/shared_ptr.hpp usability... no
checking boost/shared_ptr.hpp presence... no
checking for boost/shared_ptr.hpp... no
configure: error: Could not find a required library. Please see the README for your platform.
```

anyone have any idea?

---

### Post by gontofe on 2009-06-21
Yes, you need to check the README file for linux, then make sure all your dependencies are satisfied.

You can try running sudo apt-get build-dep xbmc too :)

---

