---
title: "(#) DirectFBError [QDirectFBPixmapData::fromDataBufferDescription()]: File not found!"
date: 2012-01-28
forum: Multimedia Software
---

### Post by pravinkumar.chavan on 2012-01-28
Hi All,

I have FAT-32 partition on my embedded device. I change  that to EXT2. Ui of my device giving following problem on clicking on  touch screen buttons.
Same thing work perfectly on FAT but giving problem when FS is change to EXT2.
I checked the images name and path on my ui they are perfect but still I am getting the error.
Can some one help me...


   ~~~~~~~~~~~~~~~~~~~~~~~~~~| DirectFB 1.4.3 |~~~~~~~~~~~~~~~~~~~~~~~~~~
        (c) 2001-2009  The world wide DirectFB Open Source Community
        (c) 2000-2004  Convergence (integrated media) GmbH
      ----------------------------------------------------------------

(*) DirectFB/Core: Single Application Core. (2010-04-27 18:24)
(*) Direct/Thread: Started 'VT Switcher' (143) [CRITICAL OTHER/OTHER 0/0] <2093056>...
(*) Direct/Thread: Started 'VT Flusher' (144) [DEFAULT OTHER/OTHER 0/0] <2093056>...
(*) DirectFB/FBDev: Found 'AU1200' (ID 0) with frame buffer at 0x08000000, 1500k (MMIO 0x00000000, 0k)
(*) Direct/Thread: Started 'tslib Input' (145) [INPUT OTHER/OTHER 0/0] <2093056>...
(*) DirectFB/Input: tslib touchscreen 0 0.1 (tslib)
(*) Direct/Thread: Started 'Keyboard Input' (146) [INPUT OTHER/OTHER 0/0] <2093056>...
(*) DirectFB/Input: Keyboard 0.9 ([directfb.org]("http://directfb.org/"))
(*) DirectFB/Graphics: Generic Software Rasterizer 0.6 ([directfb.org]("http://directfb.org/"))
(*) DirectFB/Core/WM: Default 0.3 ([directfb.org]("http://directfb.org/"))
 (!!!)  *** ONCE [no mode found for 800x480] *** [fbdev.c:1288 in dfb_fbdev_find_mode()]
 (!!!)  *** WARNING [letting unprivileged IDirectFBDisplayLayer::GetSurface() call pass until cooperative level handling is finished] *** [idirectfbdisplaylayer.c:174 in IDirectFBDisplayLayer_GetSurface()]
(*) Direct/Thread: Started 'EventBufferFeed' (147) [MESSAGING OTHER/OTHER 0/0] <2093056>...

[COLOR=#3333FF](#) DirectFBError [QDirectFBPixmapData::fromDataBufferDescription()]: File not found![/COLOR]
[COLOR=#3333FF](#) DirectFBError [QDirectFBPixmapData::fromDataBufferDescription()]: File not found![/COLOR]
 [COLOR=#3333FF](*) Direct/Interface: Loaded 'PNG' implementation of 'IDirectFBImageProvider'.[/COLOR]
[COLOR=#3333FF](#) DirectFBError [QDirectFBPixmapData::fromDataBufferDescription()]: File not found![/COLOR]
 [COLOR=#3333FF](#) DirectFBError [QDirectFBPixmapData::fromDataBufferDescription()]: File not found![/COLOR]
[COLOR=#3333FF](#) DirectFBError [QDirectFBPixmapData::fromDataBufferDescription()]: File not found![/COLOR]
 [COLOR=#3333FF](#) DirectFBError [QDirectFBPixmapData::fromDataBufferDescription()]: File not found![/COLOR]

**Could not parse application stylesheet**
 
[COLOR=#3333FF](#) DirectFBError [QDirectFBPixmapData::[/COLOR][COLOR=#3333FF]fromDataBufferDescription()]: File not found!
(#) DirectFBError [QDirectFBPixmapData::fromDataBufferDescription()]: File not found![/COLOR]

---

