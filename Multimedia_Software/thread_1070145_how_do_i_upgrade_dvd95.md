---
title: "how do i upgrade dvd95"
date: 2009-02-14
forum: Multimedia Software
---

### Post by -jay- on 2009-02-14
in ubuntu the current build is 1.3p2 but on the website it shows dvd95-1.5p0.tar.gz how do i install the newer build

---

### Post by -jay- on 2009-02-15
bump

---

### Post by mzanfardino on 2009-07-02
Once you have downloaded the file, simply untar it:
```
tar xzvf dvd95-1.5p2.tar.gz
```

This will expand the source into a directory dvd95-1.5p2/. Change to that directory:
```
cd dvd95-1.5p2/
```
Reading INSTALL reveals that the basic installation method: ./configure, make, make install should be sufficient to build and install it.

As with everything you compile from source, you might find that some libraries are missing. In my case the first pass of ./configure died stating that intltools must be installed.  A simple ```
aptitude search intltools
``` followed by ```
sudo aptitude install intltools
``` fixed this.

My next issue was with libgnomeui-2.0 and libxml-2.0. I searched apt for libgnomeui and found libgnomeui-dev, which I proceeded to install using ```
sudo aptitude install libgnomeui
```.  This proceeded to install a number of development libraries for gnome.

Again I tried ./configure and again it failed.  This time it appears that libdvdread was missing, so I searched for libdvdread in apt, noticed a libdvdread-dev and installed it with ```
sudo aptitude install libdvdread-dev
```

Back to ./configure which terminates with an error: Unable to find libdvdread >= 0.9.7. In jaunty, libdvdread-dev no longer installs 0.9.7-11ubuntu3 but instead installs 4.1.3-4ubuntu2. Searching ./configure for the libdvdread error it appears the configure is checking DVDREAD_VERSION < 907. Installing libdvdread-dev from repo installed /usr/include/dvdread/dvd_read.h which has defined DVDREAD_VERSION as 904. Not convinced that this is in fact 904, I changed this value to 907. Running ./configure again now drops out at the next error: libmpeg2 not found.

Wild guess as to what I did next: ```
aptitude search libmpeg2
``` followed by ```
sudo aptitude install libmpeg2-4-dev
```. And again, ./configure which revealed that I hadn't yet install mplayer, so again: ```
sudo aptitude install mplayer
``` 

This time ./configure completed successfully, which leaves make. Now, baring in mind I changed the version number of dvdread from 904 to 907, I'm not entirely sure that this make will complete successfully.  But I've come this far, so I ran make.  Make appeared to complete successfully, so I searched the build tree for dvd95 using ```
find . -type f -name dvd95
``` and discovered two entries, one in 
./debian/dvd95/usr/bin/dvd95 and the other in ./src/dvd95.  Checking the date/time of both files reveals that I want ./src/dvd95.  Time to run it!

```
./src/dvd95
```
Viola! dvd95 is running!  However, the language files appear to be in French, and there is still a bug whereby an iso file with an extension of .ISO (as opposed to .iso) is not found when choosing to convert an iso file (as opposed to a dvd).  However, now that I (you!) have the source, I/you can fix this minor annoyance.

In the final analysis, if you are going to build software from source, you have to be prepared to do a little leg work.  In the end, my resulting ISO could not be played back using VLC after mounting it as a directory. But I don't think it is a problem with dvd95, but more likely a problem with libdvdcss.  Guess I'll be building this from scratch next!

Good luck!

mzanfardino
--------------------------------
AMD64 Athlon X2 with 8GB ram running Ubuntu Jaunty 64

---

### Post by jwooton on 2009-08-07
Nice walkthrough.  Got me up and going.  You ever figure out how to get the language switched over from French to English?

---

