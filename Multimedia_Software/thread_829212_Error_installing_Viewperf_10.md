---
title: "Error installing Viewperf 10"
date: 2008-06-14
forum: Multimedia Software
---

### Post by Norwal on 2008-06-14
Could someone please help me interpret the error here.  I believe I'm missing a dependency, but can't figure out what it is.

Thanks in advance.

ron@Gazzoo:~/Bench/SPECViewperf10/viewperf/viewperf10.0/src$ ./Configure

    Which operating system are you building for?

    1. Linux32
    2. Solaris-Sparc
    3. Linux64
    4. Solaris-x86
    5. Solaris-x86_64
    6. Other (manual configuration)

    Choice:>  1

 Configuring for Linux


    Which compiler do you wish to use?

    default is: gcc 

    Choice:>              
Checking for gcc
Checking for gcc...
Building static library libz.a version 1.2.2 with gcc.
Checking for unistd.h... Yes.
Checking whether to use vs[n]printf() or s[n]printf()... using vs[n]printf()
Checking for vsnprintf() in stdio.h... Yes.
Checking for return value of vsnprintf()... Yes.
Checking for errno.h... Yes.
Checking for mmap support... Yes.
rm -f *.o *~ example minigzip \
	   libz.* foo.gz so_locations \
	   _match.s maketree contrib/infback9/*.o
/bin/rm -f *.o libpng.a pngtest pngout.png libpng-config \
	libpng12.so libpng12.so.0* pngtest-static pngtesti \
	libpng.so.3.1.2.8 \
	libpng.pc
./Configure: 336: /root/IMW/viewperf/SPECViewperf/viewperf/viewperf10.0/src: not found
rm -f viewperf Env.c objs/libvp.a
rm -f Release/Linux32/Env.o Release/Linux32/clock.o Release/Linux32/viewperf.o Release/Linux32/outputhtml.o Release/Linux32/grab.o Release/Linux32/evtF.o Release/Linux32/mshF.o
rm -f 
cd redistributable_sources/vpaux/libtk; touch options; make clean
make[1]: Entering directory `/home/ron/Bench/SPECViewperf10/viewperf/viewperf10.0/src/redistributable_sources/vpaux/libtk'
rm -f shapes.o font.o image.o event.o getset.o window.o cursor.o	 libtk.a
make[1]: Leaving directory `/home/ron/Bench/SPECViewperf10/viewperf/viewperf10.0/src/redistributable_sources/vpaux/libtk'
cd redistributable_sources/vpaux/libaux; touch options; make clean
make[1]: Entering directory `/home/ron/Bench/SPECViewperf10/viewperf/viewperf10.0/src/redistributable_sources/vpaux/libaux'
rm -f vpaux.o teapot.o vect3d.o xform.o libaux.a
make[1]: Leaving directory `/home/ron/Bench/SPECViewperf10/viewperf/viewperf10.0/src/redistributable_sources/vpaux/libaux'
cd redistributable_sources/libpng; touch options; make clean
make[1]: Entering directory `/home/ron/Bench/SPECViewperf10/viewperf/viewperf10.0/src/redistributable_sources/libpng'
/bin/rm -f *.o libpng.a pngtest pngout.png libpng-config \
	libpng12.so libpng12.so.0* pngtest-static pngtesti \
	libpng.so.3.1.2.8 \
	libpng.pc
make[1]: Leaving directory `/home/ron/Bench/SPECViewperf10/viewperf/viewperf10.0/src/redistributable_sources/libpng'
cd redistributable_sources/zlib; make clean
make[1]: Entering directory `/home/ron/Bench/SPECViewperf10/viewperf/viewperf10.0/src/redistributable_sources/zlib'
rm -f *.o *~ example minigzip \
	   libz.* foo.gz so_locations \
	   _match.s maketree contrib/infback9/*.o
make[1]: Leaving directory `/home/ron/Bench/SPECViewperf10/viewperf/viewperf10.0/src/redistributable_sources/zlib'
rm -f ../viewperf/viewperf
rm -f Env.c
ln -s EnvLINUX.c Env.c
gcc -c Env.c -o Release/Linux32/Env.o  -O3 -Iredistributable_sources/vpaux/libaux -I/usr/X11R6/include/ -I/usr/include/GL -Iredistributable_sources/libpng/include -DXWINDOWS -DSEARCHPATH -DLINUX -DPNG
gcc -c clock.c -o Release/Linux32/clock.o  -O3 -Iredistributable_sources/vpaux/libaux -I/usr/X11R6/include/ -I/usr/include/GL -Iredistributable_sources/libpng/include -DXWINDOWS -DSEARCHPATH -DLINUX -DPNG
gcc -c viewperf.c -o Release/Linux32/viewperf.o  -O3 -Iredistributable_sources/vpaux/libaux -I/usr/X11R6/include/ -I/usr/include/GL -Iredistributable_sources/libpng/include -DXWINDOWS -DSEARCHPATH -DLINUX -DPNG
gcc -c outputhtml.c -o Release/Linux32/outputhtml.o  -O3 -Iredistributable_sources/vpaux/libaux -I/usr/X11R6/include/ -I/usr/include/GL -Iredistributable_sources/libpng/include -DXWINDOWS -DSEARCHPATH -DLINUX -DPNG
gcc -c grab.c -o Release/Linux32/grab.o  -O3 -Iredistributable_sources/vpaux/libaux -I/usr/X11R6/include/ -I/usr/include/GL -Iredistributable_sources/libpng/include -DXWINDOWS -DSEARCHPATH -DLINUX -DPNG
gcc -c evtF.c -o Release/Linux32/evtF.o  -O3 -Iredistributable_sources/vpaux/libaux -I/usr/X11R6/include/ -I/usr/include/GL -Iredistributable_sources/libpng/include -DXWINDOWS -DSEARCHPATH -DLINUX -DPNG
evtF.c: In function ‘evtI’:
evtF.c:735: warning: incompatible implicit declaration of built-in function ‘exit’
evtF.c: In function ‘evtD’:
evtF.c:1368: warning: incompatible implicit declaration of built-in function ‘exit’
evtF.c: In function ‘evtIW’:
evtF.c:1934: warning: incompatible implicit declaration of built-in function ‘exit’
evtF.c: In function ‘evtDW’:
evtF.c:2500: warning: incompatible implicit declaration of built-in function ‘exit’
gcc -c mshF.c -o Release/Linux32/mshF.o  -O3 -Iredistributable_sources/vpaux/libaux -I/usr/X11R6/include/ -I/usr/include/GL -Iredistributable_sources/libpng/include -DXWINDOWS -DSEARCHPATH -DLINUX -DPNG
gcc -o viewperf Release/Linux32/Env.o Release/Linux32/clock.o Release/Linux32/viewperf.o Release/Linux32/outputhtml.o Release/Linux32/grab.o Release/Linux32/evtF.o Release/Linux32/mshF.o  -O3 -Iredistributable_sources/vpaux/libaux -I/usr/X11R6/include/ -I/usr/include/GL -Iredistributable_sources/libpng/include -DXWINDOWS -DSEARCHPATH -DLINUX -DPNG lib/Linux32/libpng.a lib/Linux32/libz.a -Llib/Linux32 -L/usr/X11R6/lib -L/usr/X11R6/lib -L/usr/X11R6/lib/lib -lm -lX11 -lXext -laux -lGL -lGLU -lpthread
/usr/bin/ld: skipping incompatible lib/Linux32/libaux.a when searching for -laux
/usr/bin/ld: cannot find -laux
collect2: ld returned 1 exit status
make: *** [viewperf] Error 1

ron@Gazzoo:~/Bench/SPECViewperf10/viewperf/viewperf10.0/src$

---

### Post by Garfeild on 2009-03-13
Hi
Did you solve this problem?

---

### Post by barbe-et-hache on 2009-04-07
Remove all the binary files and compile it again. 

# find . -name "*.o" | xargs rm
# find . -name "*.a" | xargs rm
# ./Compile

EDIT : This worked for me with Ubuntu 8.04 and a NVidia card.

---

