---
title: "Can't get svn mplayer to see git x264 packages..."
date: 2009-10-19
forum: Multimedia Software
---

### Post by Literati on 2009-10-19
Hi all, I'm trying to compile svn mplayer to be able to use x264 encoding. 

I've uninstalled both mplayer and x264 using Synaptic. After that I ran 

git clone git://git.videolan.org/x264.git
./configure --enable-shared
make
sudo make install
ldconfig

Then I got mplayer 

svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer
./configure

And during this step I see:

Checking for x264 ... no (in libavcodec: no)

Which is really irking me! 

Any ideas on why it won't recognize it? If it makes any difference, I'm building from a ~/Other directory, in which both x264 and mplayer are found. But I would think the install process would put them where they need to be, regardless of where I built them.

---

### Post by Literati on 2009-10-19
So, I got the config to see x264 packages. But now I get this when I try to make mplayer:

matt@matt:~/Other/mplayer$ make
cc -Wundef -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -std=gnu99 -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -Ilibdvdread4 -I.  -D_REENTRANT -I/usr/include/directfb -I/usr/include/  -I/usr/include/SDL  -D_REENTRANT   -D_REENTRANT    -I/usr/include/freetype2 -I/usr/include   -I/usr/include/schroedinger-1.0 -I/usr/include/liboil-0.3     -c -o libmpcodecs/ve_x264.o libmpcodecs/ve_x264.c
libmpcodecs/ve_x264.c: In function 'config':
libmpcodecs/ve_x264.c:188: error: 'x264_param_t' has no member named 'b_bframe_pyramid'
make: *** [libmpcodecs/ve_x264.o] Error 1

---

### Post by mc4man on 2009-10-19
see if this is the mplayer -r you have ( if not get mplayer source and try again
> /Desktop/mplayer2/mplayer$  svn log --limit 10
------------------------------------------------------------------------
[COLOR="Blue"]r29787[/COLOR] | lorenm | 2009-10-19 17:23:08 -0400 (Mon, 19 Oct 2009) | 2 lines

sync to x264-r1296

---

### Post by Literati on 2009-10-19
I had r29785, r29787 seems to have fixed the problem. :) Thank you!

---

### Post by mc4man on 2009-10-19
Sometimes you got to just wait a bit for the sources to get sync'ed.

here's a few useful pages on svn and svn mplayer

[http://ubuntuforums.org/showthread.php?t=1167578](http://ubuntuforums.org/showthread.php?t=1167578)

[http://ubuntuforums.org/showthread.php?t=1154431&highlight=svn](http://ubuntuforums.org/showthread.php?t=1154431&highlight=svn)

---

### Post by liquidox on 2009-11-01
I have this exact same problem with mplayer r29805, did they break it again?

---

