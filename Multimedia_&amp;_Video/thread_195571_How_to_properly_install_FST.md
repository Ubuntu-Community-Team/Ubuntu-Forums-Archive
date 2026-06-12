---
title: "How to properly install FST?"
date: 2006-06-13
forum: Multimedia &amp; Video
---

### Post by passonno on 2006-06-13
Hello,

I am having one hell of a time installing FST, in order to run vst instruments in Dapper.  Here is where it stops for me:

    LD_LIBRARY_PATH=":$LD_LIBRARY_PATH" /usr/bin/winebuild -fPIC -o libfst.spec.c --exe libfst -mgui   pthread.o interlocked.o gettid.o libwinelib.o vstwin.o fstinfofile.o fst.o   -L/usr/lib/wine -L/usr/lib/wine  -ladvapi32 -lcomdlg32 -lgdi32 -lkernel32 -lodbc32 -lole32 -loleaut32 -lshell32 -luser32 -lwinspool
winebuild: executable must be named via the -F option
make[1]: *** [libfst.spec.c] Error 1
make[1]: Leaving directory `/home/anthony/Downloads/fst-1.6/fst'
make: *** [fst] Error 2


What am I doing wrong?  Any ideas?  

Any clues as to what versions of wine and fst Ifst should be using?

---

