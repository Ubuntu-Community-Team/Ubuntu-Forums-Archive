---
title: "[SOLVED] FourCC problem turned into install nightmare..."
date: 2008-01-30
forum: Multimedia &amp; Video
---

### Post by twooften on 2008-01-30
I am a new user to ubuntu, other than trying out the live CD.
One of the task that I would preform on my old XP install is changing the FourCC code on avi files.
I have found two programs that claim to be able to do the change, AviUtils KDE and some AviC Linux equivalent (check here to see [http://blog.mypapit.net/2005/06/fourcc-changer-divx-avi-under-linux.html](http://blog.mypapit.net/2005/06/fourcc-changer-divx-avi-under-linux.html) )
The AviUtils I figured out is a program done in kommander, so I install kommander, I only see a way to run the program, at which point it does not appear to be working properly cause I cant open any files with it.
As for the AviC thing, I downloaded their source files and followed instructions to the best of my knowledge.
I extracted the "gfourcc" archive and used a terminal to "./configure" (instructions that came with it) and got "checking for C compiler default output file name... configure: error: C compiler cannot create executables"
So my question(s) is, am I going about the proper route, or am I headed off into nowhere land...?
If I am going the right direction, what am I missing?
If I should be looking into something else....what?

Thanks for any insight!

---

### Post by twooften on 2008-01-31
There has to be someone who knows the ./configure thing, or kommander....?

---

### Post by archivator on 2008-01-31
Before compiling anything from scratch, you need to install the build-essential package.
```
sudo apt-get install build-essential
```
After that, the configure script will tell you of any missing dependencies you might need to install.

---

### Post by eye208 on 2008-01-31
> **twooften said:**
> If I should be looking into something else....what?
Just install [cfourcc](http://packages.ubuntu.com/gutsy/graphics/cfourcc) from the repository. No need to compile anything.

---

### Post by twooften on 2008-01-31
Thanks a lot guys!

Two things there that really helped, the repository and installing build essentials.

Although I have read about it several times, I didn't know what the repository was.

Cheers!

---

