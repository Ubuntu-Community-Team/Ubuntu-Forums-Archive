---
title: "Why is my K3b converter still using flac 1.1.3?"
date: 2008-08-21
forum: Multimedia Software
---

### Post by logos34 on 2008-08-21
How do you update the version of FLAC encoder K3b uses?  

Mine's (K3b 1.0.4) using the previous version for some reason (that's what 'metaflac --list' and reports).  When I converted some .ape/monkey's audio files, I found I couldn't fast-forward in amarok...when I drag the progress slider bar it just snaps back like rubber band.  So I converted to .wavs, then manually compressed with flac 1.2.0, and it works (same for ogg and wav format).

---

### Post by logos34 on 2008-08-22
anyone?

funny thing--I'm getting the same problem when I use MediaCoder (wine) and flac 1.2.0.  

The only way to get fast-forward feature is to expand to .wav and then manually run flac from cli

---

### Post by cozmicharlie on 2008-08-23
This should work for you:

Uninstall your current flac

Get the build dependencies

```
#sudo apt-get build-dep flac
```

Create a ~/build directory (you don't have to do this if you don't want to - you can just download to your home folder or wherever you want just maek sure you change the commands below accordingly):

```
#mkdir ~/build
```

Change to the build directory:

```
#cd ~/build
```

Get flac's sources and change to the source directory:

```
#apt-get source flac
#cd flac-1.2.1
```

Configure, make and install:

```
#./configure
#make
#sudo make install
```

---

### Post by logos34 on 2008-08-24
This is what I get after I do sudo checkinstall (I'm using that instead of make install--usually works just fine):
> 
...

Making install in .
make[3]: Entering directory `/home/zazen/build/flac-1.2.1/src/libFLAC'
make[4]: Entering directory `/home/zazen/build/flac-1.2.1/src/libFLAC'
/bin/bash ../../mkinstalldirs /usr/local/lib
 /bin/bash ../../libtool --mode=install /usr/bin/install -c  libFLAC.la /usr/local/lib/libFLAC.la
/usr/bin/install -c .libs/libFLAC.so.8.2.0 /usr/local/lib/libFLAC.so.8.2.0
(cd /usr/local/lib && rm -f libFLAC.so.8 && ln -s libFLAC.so.8.2.0 libFLAC.so.8)
(cd /usr/local/lib && rm -f libFLAC.so && ln -s libFLAC.so.8.2.0 libFLAC.so)
/usr/bin/install -c .libs/libFLAC.lai /usr/local/lib/libFLAC.la
/usr/bin/install -c .libs/libFLAC.a /usr/local/lib/libFLAC.a
ranlib /usr/local/lib/libFLAC.a
chmod 644 /usr/local/lib/libFLAC.a
[COLOR=Red]chmod: changing permissions of `/usr/local/lib/libFLAC.a': No such file or directory
make[4]: *** [install-libLTLIBRARIES] Error 1
make[4]: Leaving directory `/home/zazen/build/flac-1.2.1/src/libFLAC'
make[3]: *** [install-am] Error 2
make[3]: Leaving directory `/home/zazen/build/flac-1.2.1/src/libFLAC'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/zazen/build/flac-1.2.1/src/libFLAC'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/zazen/build/flac-1.2.1/src'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.[/COLOR]

Cleaning up...OK

Bye.

Jeez, it's not worth it...I'll just expand the .ape to .wav first

---

### Post by mc4man on 2008-08-24
putting aside the fact flac 1.2.1 is available in the repo's, if you wanted to build it (or any source with a debian dir.) then just use 
```
doug@doug-desktop:~/flac-1.2.1$ fakeroot debian/rules binary
```

Make any configuration changes in the rules file (debian dir. in source) and or prefix them to above comm.
In some cases look for an upstream dir. and use it's rules file (copy and replace the one in debian dir. (mplayer a is good example

(Don't see anything to change here though
ex. 
> DEB_BUILD_OPTIONS="--prefix=/usr/local" fakeroot debian/rules binary


Edit: obv. you'd need fakeroot installed

Anyway this will build you nice proper .deb's (usually several

---

### Post by logos34 on 2008-08-24
> **mc4man said:**
> putting aside the fact flac 1.2.1 is available in the repo's, if you wanted to build it...

thanks...I have 1.2.1 installed, so I guess K3b can't be using 1.1.3 (I was thinking maybe it had a bundled version it used instead), and the reason for no f-forward is due to some other factor (maybe the original .ape files don't support it???)...So it looks like I have no choice but to expand to .wav then compress back down to desired format

---

