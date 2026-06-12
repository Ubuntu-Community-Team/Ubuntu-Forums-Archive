---
title: "opengl support"
date: 2007-05-26
forum: Multimedia Production
---

### Post by FunkyMunky on 2007-05-26
hello. i'm trying to install cinelerra and everything seems to go smoothly.
although i know that opengl hardware accelation is only optional, i want to have it, but it seems to be missing. after i have done "./configure --with-buildinfo=svn/recompilesee" i get a bunch of text but i think this is the thing i need to see (note that i'm fairly new to linux):

>  Summary of mandatory components:
  libogg                  found
  libvorbis               found
  libvorbisenc            found
  libvorbisfile           found
  libtheora               found
  OpenEXR                 found
  libdv                   found
  libpng                  found
  libjpeg libraries       found  libjpeg headers         found
  libtiff libraries       found
  libtiff headers         found
  FreeType 2              found
  libx264 libraries       found
  libx264 headers         found
  libuuid libraries       found
  libuuid headers         found
  mjpegtools              found
  libfftw3 libraries      found
  libfftw3 headers        found
  liba52 libraries        found
  liba52 headers          found
  libmp3lame libraries    found
  libmp3lame headers      found
  libsndfile libraries    found
  libsndfile headers      found
  libfaac libraries       found
  libfaac headers         found
  libfaad libraries       found
  libfaad headers         found

Summary of optional components:
  ESD subsystem           missing
ESD (Enlightenment Sound Daemon) is disabled
  ALSA subsystem          found
ALSA is enabled
  libraw1394              found
  libiec61883             found
  libavc1394 libraries    found
  libavc1394 headers      found
  librom1394 libraries    found
  librom1394 headers      found
Firewire is enabled
  OpenGL 2.0 libraries    missing
Hardware acceleration using OpenGL 2.0 is disabled

Now type
          make

to start compilation.
root@xubuntu:/opt/hvirtual# 
  


any idea how to enable opengl support?
also, what is ESD subsystem which also seems to be disabled (or not installed)?

if anyone needs to know, my system is:

athlon x2 4000+
2x1gb ddr2 takems
radeon x1350xt (although i'm not sure...)
xubuntu 7.04 x32
fglrx driver
everything up to date.

help appreciated :)

---

### Post by nedecor on 2007-05-26
ESD really isn't necessary, so I would just leave it out.

Cinelerra is looking for OpenGL 2.0, which as far as I know, is implemented by libmesa. I'm not sure of the exact package name, I'm at work so I don't have my Linux Box in front of me, but whenever I'm looking for a package I use:

sudo apt-cache search libmesa

Hope that helps.

Jake

---

