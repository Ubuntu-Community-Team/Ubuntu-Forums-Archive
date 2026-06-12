---
title: "Help Installing amarok and libgpod"
date: 2008-01-22
forum: Multimedia &amp; Video
---

### Post by evw2k on 2008-01-22
Okay, so I tried to install amarok because I heard its pretty awesome. I downloaded that tar and followed their directions until it told me to check for dependencies. According to the console I needed libgpod-dev or some crap. So I followed the links, downloaded libgpod, and followed their installation instructions. First ./configure, then make then make install. All went well until make install when I kept getting this error. Whats up? I tried libgpod 0.6 and 0.5.2.

nicholas@nicholas-desktop:~/libgpod-0.5.2$ make install
Making install in src
make[1]: Entering directory `/home/nicholas/libgpod-0.5.2/src'
make[2]: Entering directory `/home/nicholas/libgpod-0.5.2/src'
/bin/bash ../mkinstalldirs /usr/local/lib
 /bin/bash ../libtool --mode=install /usr/bin/install -c  libgpod.la /usr/local/lib/libgpod.la
/usr/bin/install -c .libs/libgpod.so.2.0.0 /usr/local/lib/libgpod.so.2.0.0
/usr/bin/install: cannot create regular file `/usr/local/lib/libgpod.so.2.0.0': Permission denied
make[2]: *** [install-libLTLIBRARIES] Error 1
make[2]: Leaving directory `/home/nicholas/libgpod-0.5.2/src'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/nicholas/libgpod-0.5.2/src'
make: *** [install-recursive] Error 1

---

### Post by ThrobbingBrain66 on 2008-01-22
There's no reason to compile amarok, it's in the repos.

It's as easy as opening a terminal and typing:
```
sudo apt-get install amarok
```

---

### Post by evw2k on 2008-01-22
wow.... i feel kinda stupid because I've been doing that with everything else. You think they'd mention that in all the readmes and website faqs. lol guess they figured I would think of that first. thanks.

---

### Post by MrClearPore on 2008-01-23
> nicholas@nicholas-desktop:~/libgpod-0.5.2$ make install
Making install in src
make[1]: Entering directory `/home/nicholas/libgpod-0.5.2/src'
make[2]: Entering directory `/home/nicholas/libgpod-0.5.2/src'
/bin/bash ../mkinstalldirs /usr/local/lib
/bin/bash ../libtool --mode=install /usr/bin/install -c libgpod.la /usr/local/lib/libgpod.la
/usr/bin/install -c .libs/libgpod.so.2.0.0 /usr/local/lib/libgpod.so.2.0.0
/usr/bin/install: cannot create regular file `/usr/local/lib/libgpod.so.2.0.0': Permission denied
make[2]: *** [install-libLTLIBRARIES] Error 1
make[2]: Leaving directory `/home/nicholas/libgpod-0.5.2/src'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/nicholas/libgpod-0.5.2/src'
make: *** [install-recursive] Error 1 

It seems that you're running the 'make install' command as a regular user and not as root.  Try 'sudo make install' instead.  The errors you're getting are permission related.
Also, if you're installing dependencies from source files (tarballs), make sure to add your /usr/local/lib path to the LD_LIBRARY_PATH variable like this:

```
export LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH 
```

By default, programs installed from source will look to /usr/lib for any needed libraries.  The above command will tell the program to look to /usr/local/lib as well, in order to find the libraries that were installed from source (in your case, libgpod, which would have installed its libraries to /usr/local/lib by default).  Of course, if you install your dependencies using Synaptic, then there's no reason to update the LD_LIBRARY_PATH variable, as the dependencies from the repos install to /usr/lib anyway.

Personally, I find installing dependency packages from source to be too much of a hassle.  I install all my programs from source and leave the dependencies to the repos whenever possible :)

Good luck.

---

