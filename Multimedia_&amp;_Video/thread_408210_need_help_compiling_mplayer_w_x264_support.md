---
title: "need help compiling mplayer w/ x264 support"
date: 2007-04-13
forum: Multimedia &amp; Video
---

### Post by czynski on 2007-04-13
I have been trying to get better playback on a .mkv video and thought compiling
 
mplayer from source would help but is says no support for x264. i have every single

 codec i could possibly think of.

---

### Post by stefangr1 on 2007-04-13
You should install x264 seperately. You could do that by following the steps below:

svn co svn://svn.videolan.org/x264/trunk x264
cd x264
./configure
make
sudo make install
cd ..

You might need to install svn first (with sudo apt-get install svn).

After this, you can compile and install mplayer again, and you will have x264 enabled.

---

### Post by czynski on 2007-04-13
well that makes sense. only prob though is that when i try to compile x264 it says no 

assembler. please install yasm. i have yasm installed through the repos and it still won't 

work.

---

### Post by PurpleSkunk on 2007-04-16
+1, same error here when compiling x264.

"No assembler. Please install yasm."

This is very annoying since I am actually trying to cross-compile JVLC Java Bindings, and this is part of the process.

Any help would be greatly appreciated.

Thanks a lot in advance.



EDIT : Nevermind, **installing nasm solved my issue**. Sorry for that ! :-\"

---

### Post by stefangr1 on 2007-04-20
I think the performance gain of compiling mplayer yourself will be almost undetectable. I have compiled it myself previously (I had -vo out error problem with the prebuilt version), but never succeeded to get good mp3 support, and in some h264 files the sound stayed out of synd whatever I tried. 

I yesterday installed Ubuntu 7.04, installed all proprietary and most used codecs with Automatix, and installed mplayer with apt-get install. It's probably a suboptimal solution, but at least everything is installed very fast and you can play any file (actually even more than with vlc, to my experience).

---

### Post by penvzila on 2007-05-12
The repository version of MPlayer contains x264 that wasn't compiled with multithreading support.  So the performance gain from compiliing it yourself should be huge on a dual core machine.

---

### Post by penvzila on 2007-05-14
> **czynski said:**
> well that makes sense. only prob though is that when i try to compile x264 it says no 

assembler. please install yasm. i have yasm installed through the repos and it still won't 

work.


You need yasm .6.0, which you can build.  Just google yasm.

---

### Post by hypocratus on 2008-01-13
I'm using dapper and I just installed nasm which seemed to work fine for compiling x264. At least it didn't complain about no assembler anymore.

---

