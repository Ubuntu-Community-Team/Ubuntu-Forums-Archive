---
title: "PiTiVi problem"
date: 2010-04-24
forum: Multimedia Software
---

### Post by Jbike on 2010-04-24
PiTiVi problem:

After installing Lives, PiTiVi and Cheese now fail to load with the following terminal messages respectively:

PiTiVi:

jbike@jbike-desktop:~$ pitivi
Traceback (most recent call last):
  File "/usr/bin/pitivi", line 117, in <module>
    _init_gobject_gtk_gst()
  File "/usr/bin/pitivi", line 106, in _init_gobject_gtk_gst
    import gst
  File "/usr/lib/python2.6/dist-packages/gst-0.10/gst/__init__.py", line 193, in <module>
    from _gst import *
RuntimeError: can't initialize module gst: Error re-scanning registry , child terminated by signal
jbike@jbike-desktop:~$ 

Cheese:

jbike@jbike-desktop:~$ cheese
Error re-scanning registry , child terminated by signal


I am fairly certain that the installation of "Lives" broke both of these... it is hard to say what else is effected, and I am worried that 10.04 may also be effected. Does anyone know what's up with this? 

Jbike

---

### Post by no2498 on 2010-04-24
im not positive but lives uses jack audio
pitivi and cheese do not  

hope this points you in the right way

---

### Post by Jbike on 2010-04-24
Not yet it doesn't. Brasero, Amarok, and Rhythm box are also broken now. This could be a BIG BUG for 10.04. When I start Amarok the first time I received some kind of error such as: Phonon audio playback device Nvidia bla bla sound not working... switching to pulse audio... then amarok crashes anyways. 

Jbike

---

### Post by Jbike on 2010-04-24
And... all of my video playback applications are also broken. 

Help!

Jbike

---

### Post by splicerr on 2010-04-24
Most likely it's this bug that affects you.

[https://bugs.launchpad.net/ubuntu/+source/gavl/+bug/456530](https://bugs.launchpad.net/ubuntu/+source/gavl/+bug/456530)

Seems to be fixed in Lucid.

---

### Post by Jbike on 2010-04-24
Rhythm box error was the same as Piti and cheese, Amarok's error message was more interesting... the interesting piece of amarok's error is listed below: 

[COLOR="Red"]jbike@jbike-desktop:~$ QObject: Cannot create children for a parent that is in a different thread.
(Parent is Solid::Backends::Hal::HalDevice(0xa472170), parent's thread is QThread(0x9c5e2c0), current thread is ThreadWeaver::Thread(0xa674bf0)
QObject: Cannot create children for a parent that is in a different thread.
(Parent is Solid::Backends::Hal::HalDevice(0xa89aaa0), parent's thread is QThread(0x9c5e2c0), current thread is ThreadWeaver::Thread(0xa674bf0)[/COLOR]


Ok, now I will wait for someone to give me another clue. My system is now officially borked. Any help would be appreciated!

Jbike

---

### Post by Jbike on 2010-04-24
Thanks so much for the link!  At the end of the thread, it was suggested to install the Lucid library from here: [http://packages.ubuntu.com/lucid/libgavl1](http://packages.ubuntu.com/lucid/libgavl1)   How do I do this as it is not completely clear from this page? 

Your help is appreciated. 

Jbike

---

### Post by splicerr on 2010-04-24
i386:

[http://mirrors.kernel.org/ubuntu/pool/universe/g/gavl/libgavl1_1.1.1-3_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/g/gavl/libgavl1_1.1.1-3_i386.deb)

or amd64:

[http://mirrors.kernel.org/ubuntu/pool/universe/g/gavl/libgavl1_1.1.1-3_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/universe/g/gavl/libgavl1_1.1.1-3_amd64.deb)

---

### Post by Jbike on 2010-04-24
Never mind I figured it out, and installed the new library... Everything is fixed ( I tried all of the aforementioned pkgs  - they all work now). Thanks so much. This forum continues to impress me. I fixed a major problem in just a few hours. The power of a community is mighty indeed! 

Thanks so much
Jbike

---

### Post by ubontik on 2010-05-02
I have ubuntu 10.04 LTS and    	 	 	PiTiVi v0.13.4. When I try to drag a clip from the clip library to project box     	 	 	PiTiVi crushes.

Please help
Thanks a lot

---

### Post by Jbike on 2010-10-22
Hmmm, I will check my version for you. The last time I tried dragging clips to the time line, and rendering, it all worked just fine in 10.04, 64 bit version. My beef is with the fact that transitions are not implemented yet. 

Jbike

---

### Post by Rytron on 2011-02-13
I've noticed that I can drag an MP3 file into the timeline with no problem. When I drag an FLV or JPG file in, the program crashes everytime. I ran it in the terminal and got this:
```

~$ pitivi 

progname=pitivi; RGBA=on
** Message: pygobject_register_sinkfunc is deprecated (GstObject)
The program 'pitivi' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 119 error_code 8 request_code 133 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

---

