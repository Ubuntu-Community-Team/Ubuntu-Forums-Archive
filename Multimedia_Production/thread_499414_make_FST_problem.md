---
title: "make FST problem"
date: 2007-07-12
forum: Multimedia Production
---

### Post by michaelwilliamson on 2007-07-12
I'm trying to build FST to add VST to my audio system (I'm using ubuntu Studio)

I think i've satisfied all the dependencies, switced  to my  FST-1.8 directory type "make" and it doesn't work...

here is the output, I hope someone can help me resolve this:


cp -a `find . | grep 'vstsdk[^/]*\$'`/source/common ./vst
sed -i '/struct VstFileType\|struct VstFileSelect/,/};/d' vst/aeffectx.h
winegcc -c  `pkg-config --cflags gtk+-2.0` `pkg-config --cflags jack` `pkg-config --cflags jack` `pkg-config --cflags lash-1.0` -DHAVE_LASH -I.   -o audiomaster.o audiomaster.c
audiomaster.c: In function ‘jack_host_callback’:
audiomaster.c:119: warning: incompatible implicit declaration of built-in function ‘floor’
winegcc -c  `pkg-config --cflags gtk+-2.0` `pkg-config --cflags jack` `pkg-config --cflags jack` `pkg-config --cflags lash-1.0` -DHAVE_LASH -I.   -o fst.o fst.c
winegcc -c  `pkg-config --cflags gtk+-2.0` `pkg-config --cflags jack` `pkg-config --cflags jack` `pkg-config --cflags lash-1.0` -DHAVE_LASH -I.   -o fstinfofile.o fstinfofile.c
fstinfofile.c: In function ‘load_fst_info_file’:
fstinfofile.c:36: warning: incompatible implicit declaration of built-in function ‘malloc’
fstinfofile.c: In function ‘fst_info_from_plugin’:
fstinfofile.c:162: warning: incompatible implicit declaration of built-in function ‘malloc’
winegcc -c  `pkg-config --cflags gtk+-2.0` `pkg-config --cflags jack` `pkg-config --cflags jack` `pkg-config --cflags lash-1.0` -DHAVE_LASH -I.   -o gtk.o gtk.c
winegcc -c  `pkg-config --cflags gtk+-2.0` `pkg-config --cflags jack` `pkg-config --cflags jack` `pkg-config --cflags lash-1.0` -DHAVE_LASH -I.   -o jfst.o jfst.c
winegcc -c  `pkg-config --cflags gtk+-2.0` `pkg-config --cflags jack` `pkg-config --cflags jack` `pkg-config --cflags lash-1.0` -DHAVE_LASH -I.   -o vsti.o vsti.c
vsti.c: In function ‘queue_midi’:
vsti.c:79: warning: assignment from incompatible pointer type
winegcc -c  `pkg-config --cflags gtk+-2.0` `pkg-config --cflags jack` `pkg-config --cflags jack` `pkg-config --cflags lash-1.0` -DHAVE_LASH -I.   -o vstwin.o vstwin.c
vstwin.c: In function ‘fst_load’:
vstwin.c:480: warning: assignment from incompatible pointer type
winegcc -mwindows -o fst.exe audiomaster.o fst.o fstinfofile.o gtk.o jfst.o vsti.o vstwin.o     `pkg-config --libs gtk+-2.0` `pkg-config --libs jack` `pkg-config --libs alsa` `pkg-config --libs lash-1.0`  -L/usr/X11R6/lib -lX11   -luuid
jfst.o: In function `main':
jfst.c:(.text+0xa4c): undefined reference to `pthread_create'
vsti.o: In function `stop_midireceiver':
vsti.c:(.text+0x562): undefined reference to `pthread_join'
collect2: ld returned 1 exit status
winegcc: gcc failed.
make: *** [fst.exe] Error 2


I will be very grateful if someone knows the answer.

cheers

mike williamson

---

### Post by JeffV on 2007-07-15
I have exactly the same problem.  I'm also using Ubuntu Studio, only I'm trying to make FST-1.7 and not using LASH.  However, I get the exact same error messages as you.

Hasn't anyone successfully used FST in Ubuntu Studio yet?

---

### Post by mlyte4218 on 2007-07-19
Hello, Im just starting to try and get all this together myself. (I seriously miss amplitube.) I just thought I'd let you know. The site that I got the tarball from fst says this:

Ismael Valladolid Torres notes that the fst.exe.so shared object library must be in the same dir as fst. FST currently does not include a 'make install' step, so you must either run the fst binary from the fst-x.x directory or copy the binary and the fst.exe.so library to a common place in your PATH, e.g. /usr/local/bin/

Here's the site I got it from
[http://joebutton.co.uk/fst/](http://joebutton.co.uk/fst/)

hopefully that helps and then I can mooch the info back about how to get this working. 

Marc

---

### Post by 0ptix on 2007-07-31
same problem here... anyone found a fix yet?

edit: ok. i got it to compile at least. open the makefile and add "-lpthread" to the LIBRARIES variable. (i inserted it before all the pkg-config stuff.)

that did the trick.

---

### Post by ariolim on 2007-08-10
Verify that audiomaster.c  contains the include
#include <math.h>

and file fstinfofile.c contains the include
#include <stdlib.h>

If not, just add them, and retry with 'make'

Regards,
Marco Arioli

---

