---
title: "Help with building FFMPEG on windows"
date: 2009-06-27
forum: Multimedia Software
---

### Post by Wug on 2009-06-27
I am using cygwin, a *nix emulator.
I ran configure and make, producing an executable with no problems.
However, when I try to use the executable, I get an error stating:
Unable to locate component
This application has failed to start because cygbz2-1.dll was not found. Re-installing the application may fix this problem. 
------
I found the DLL and moved it into ffmpeg's directory, but the troubling part is that I followed directions intended to make a cygwin-dependancy-free executable. (and it asked for yet another one) 
I got the ffmpeg src from SVN (version 19285)
I am using the latest version of cygwin (the unstable one)
I used the commands:

cd ~/ffmpeg
./configure --target-os=mingw32 --enable-memalign-hack --enable-static --disable-shared --extra-cflags=-mno-cygwin --extra-libs=-mno-cygwin
make

does anyone know how to get the latest ffmpeg source to compile on cygwin without lots of external dependancies?

---

### Post by Wug on 2009-06-27
hey I think I fixed it - 
I did a build first with different settings and didnt use make distclean, so some of the old settings had gotten mixed up into the new executable (which btw I think *wasnt* overwritten)
so a make distclean then ./conf... and make made a working, dependancy free windows executable.

---

