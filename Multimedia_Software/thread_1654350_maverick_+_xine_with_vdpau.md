---
title: "maverick + xine with vdpau?"
date: 2010-12-28
forum: Multimedia Software
---

### Post by Catscrash on 2010-12-28
Hi,

is there any way to get an vdpau-enabled xine in maverick? With (s)mplayer vdpau works great, but xine doesn't have a vdpau option. 

The ppa's that used to work with karmic don't have packages for maverick anymore and the xine-version shipped with maverick doesn't seem to have vdpau enabled.

If there's an easy way to compile xine with vdpau, I'll take that too.

Thanks
Catscrash

---

### Post by mc4man on 2010-12-28
You would need to find or build xine-lib 1.2, then build xine-ui to support vdpau.

I tried it quite some time ago, while it worked the performance was not so great (may be hardware dependant
Because it's a work in progress best to use the latest 1.2 source, I think about 2 weeks old.

you could go here and grab a .tar.bz2 (I believe the xine-lib-1.2 and the xine-lib-1.2-vdpau are the same 
[http://hg.debian.org/hg/xine-lib/](http://hg.debian.org/hg/xine-lib/)

or in terminal

```
hg clone http://hg.debian.org/hg/xine-lib/xine-lib-1.2
```

The build-deps would be similar to the current xine-lib in maverick plus a few inc. libvdpau-dev

Best way to build not sure - you could try a ./autogen.sh, make, sudo make install (or checkinstall) to /usr/local, or adapt a debian folder/ to create individual packages.
(if using the former make sure to run this after installing
sudo ldconfig

Happen to be using natty atm and on a machine that while i could build xine-libs-1.2 w/ vdpau support the card doesn't support (7800 AGP
Did both ways, for packages grabbed the debian folder from Brandon Synders ppa, made a few changes and used that. (before building I copied the new debian folder to my build folder and compressed for future use, in screen as debian.tar.gz

+++++++++++++++++++++++++++++++++
the build-deps as shown in B.S.'s control file, should about do it.
(for natty i didn't build the xvmc plugin, was an issue there.
> Build-Depends: debhelper (>= 5.0.1), binutils (>= 2.12.90.0.9), pkg-config,
	libavcodec-dev,	libavformat-dev, libpostproc-dev,
	libvdpau-dev,
	libxcb-xv0-dev, libxcb-shm0-dev, libxcb-shape0-dev,
	libxinerama-dev, libxv-dev, libxvmc-dev, libxt-dev, 
	libasound2-dev [!kfreebsd-i386 !kfreebsd-amd64 !hurd-i386],
	libv4l-dev [!kfreebsd-i386 !kfreebsd-amd64 !hurd-i386],
	libaa1-dev, libcaca-dev, libmodplug-dev,
	libmagickwand-dev, libpng12-dev, libfreetype6-dev, 
	libogg-dev, libvorbis-dev, libtheora-dev,
	libesd0-dev, libgnomevfs2-dev,
	libvcdinfo-dev, libpulse-dev,
	liblircclient-dev, libjack-dev (<= 0.110) | libjack-dev (>= 0.116.1-3),
	libdirectfb-dev (>= 0.9.22), libgtk2.0-dev,
	libfaad-dev, libflac-dev, libsdl1.2-dev, libwavpack-dev,
	libsmbclient-dev, libspeex-dev, libmng-dev, 
	libmad0-dev, libmpcdec-dev, libcdio-dev (>= 0.76), 
	zlib1g-dev, w3m, xmlto, librsvg2-bin

---

### Post by Catscrash on 2010-12-30
okay, that way i have a xine-ui that can actually use vdpau, that's great thx. How can i get kaffeine to use that xine now and not the one from the repository-packages? 

thx!

---

### Post by mc4man on 2010-12-30
As far as kaffeine - not really a clue - never use.

I would suspect a re-build is needed against the new xine-lib (1.2), a cursory search turned up this though_ more than a bit dated_ (was in regards to kaffeine 0.8.X

> If you own a recent nvida VGA and wanna use hardware accel for h.264, get the latest nvidia beta-driver (at time of writing this the latest available one is 185.19) and xine-vdpau. Note that you need to rebuild kaffeine with the "--without-xcb" configure switch to use vdpau hardware acceleration. 


With some further searching you should find a more current 'method', whatever that may be

Edit: first place to ck. would be in current kaffeine source- ./configure --help

---

