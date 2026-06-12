---
title: "compiling gphoto2 on ubuntu 9.04 NBR"
date: 2009-08-22
forum: Multimedia Software
---

### Post by MakaniMike on 2009-08-22
hello all.

I am trying to install gphoto2 2.4.7 and libgphoto2 2.4.7 on my eeepc 701. I am unsuccessful in doing so.

I grabbed the files from here: [http://sourceforge.net/projects/gphoto/files/](http://sourceforge.net/projects/gphoto/files/)

The readme states:
> 
How do I build it?
------------------

  * If using SVN source, run "autoreconf -is".
  * configure
  * make
  * make install

Out-of-tree builds are supported. "configure --help" may help.
none of that does anything for me but give me errors.

If i run
./configure
while in the unpacked tar.gz folder of gphoto2 I get:
> 
configure: error: in '/home/makanimike/Desktop/gphoto2-2.4.7':
configure: error: C compiler cannot create executables
How do I get gphoto2 and libgphoto2-2.4.7 installed?

Thanks so much for your help. :)


oh yes. to preemptively address the inevitable question of why I do not just sudo apt-get it from a ubuntu repo:
I need the 2.4.7 version for my canon 500d camera. the repos don't have the current (week old) version. 
and yes, I can of course just plug it in and the camera will be detected.
but I want to remote control my camera in order to do time-lapse projects.

---

### Post by keithdw on 2009-10-20
I'm also having difficulty compiling gphoto2 to run on Mint (Ubuntu 9.04).

---

