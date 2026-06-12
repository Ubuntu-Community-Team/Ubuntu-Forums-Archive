---
title: "rakarrack installation"
date: 2010-04-02
forum: Multimedia Software
---

### Post by ericmo on 2010-04-02
I'm trying to compile Rakarrack at my PC, following those instructions.

[http://rakarrack.sourceforge.net/dl.html](http://rakarrack.sourceforge.net/dl.html)
[http://king84.wordpress.com/2009/12/17/tutorial-installazione-rakarrack-0-4-0-su-karmic-koala/](http://king84.wordpress.com/2009/12/17/tutorial-installazione-rakarrack-0-4-0-su-karmic-koala/)

When I try to run "./configure" it says file not found.

I did run a bunch of sudo apt-get install for all of the dependencies, but didn't check if they were all there.

That's what comes out when I run ./autogen.sh
```

Generating build scripts, this might take a while.
 aclocal./autogen.sh: 36: aclocal: not found
 autoheader./autogen.sh: 37: autoheader: not found
 autoconf./autogen.sh: 38: autoconf: not found
 automake./autogen.sh: 39: automake: not found

Done generating build scripts.

```And when I run ./configure

```
bash: ./configure: File or directory not found
```What should I do?

---

### Post by ericmo on 2010-04-02
Hey, I've already found out what was wrong, I was missing the gpp package!
Also, I've downloaded the tarball package here: [http://rakarrack.sourceforge.net/dl.html](http://rakarrack.sourceforge.net/dl.html), instead of doing the cvs thing, it was much smoother. This link helped me out: [http://www.murga-linux.com/puppy/viewtopic.php?t=53128&sid=03a9b22c97da4d880b91722823946dcd](http://www.murga-linux.com/puppy/viewtopic.php?t=53128&sid=03a9b22c97da4d880b91722823946dcd)

---

### Post by transmogrifox on 2010-04-08
I'm glad you got it to work out.  The official tarballs are the easiest to compile because there are less tools required to properly build the package.  

If you want the latest and greatest, then build from the git repository.  That is where all recent development is happening (see the help page [http://rakarrack.sourceforge.net/help.html](http://rakarrack.sourceforge.net/help.html) for a description of the newest features).  This page will get you started with how to compile from git:
[http://rakarrack.sourceforge.net/dl.html](http://rakarrack.sourceforge.net/dl.html)  
And use instructions under the heading "Git".

For the benefit of other users who may read this post and want to build from git or cvs, I will attempt to explain what is likely the problem with invoking ./autogen.sh and ./configure.
 aclocal./autogen.sh: 36: aclocal: not found
 autoheader./autogen.sh: 37: autoheader: not found
 autoconf./autogen.sh: 38: autoconf: not found
 automake./autogen.sh: 39: automake: not found

This indicates you don't have the automake, autoconf tools installed. Synaptic search for automake, autoconf and autoheader.  Installing one usually selects the rest as dependencies.  This will enable the autogen script to execute correctly.

If ./autogen does not complete successfully, then ./configure will certainly fail, because autgen.sh creates the configure scripts.

./configure will tell you if you're missing other things as well.  For compiling you need things like gcc and automake just so you can run make and compile the program.

---

### Post by ericmo on 2010-04-15
I think I'm not going to mess with what is already working!
But thanks, I'll do that when updating.

---

### Post by ericmo on 2010-04-17
I've had to reinstall Ubuntu and lost my previous Rakarrack installation, so now I've installed it through Git. It is not that complicated, the problem is mostly that not all dependencies are clearly listed on readme, like Xft (libxft-dev). But it was rather smooth as I was doing it for the second time.

Thanks.

---

