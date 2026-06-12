---
title: "Full-screen flash player quality"
date: 2009-02-03
forum: Multimedia Software
---

### Post by taojian on 2009-02-03
Hi there,

My problem is cruddy playback quality when using the full-screen mode of various flash-based streaming video services (ie Youtube and others). The normal size plays fine, but full screen stutters and flickers, and on some sites shows flashes of the original webpage behind the video.

I'm using Ubuntu on a Dell, with the follow versions, etc:

Mozilla/5.0 (X11; U; Linux i686; zh-CN; rv:1.9.0.5) Gecko/2008121622 Ubuntu/8.10 (intrepid) Firefox/3.0.5

Searching for flash in the package manager shows these packages installed:

adobe-flashplugin 10.0.15.3-1intrepid2
flashplugin-nonfree 10.0.15.3ubuntu1-intrepid1

I've installed ubuntu-restricted-extras.
Looking at plugins under Firefox's tool menu only shows Shockwave Flash.
Visiting about:plugins gives me this:

Shockwave Flash

    Filename&#65306; libflashplayer.so
    Shockwave Flash 10.0 r15

application/x-shockwave-flash 	Shockwave Flash 	
application/futuresplash 	FutureSplash Player


The problem could be a large screen: it's a Dell, 1440x900@60Hz. Doing a hardware test shows that Ubuntu has got the proper dimensions and whatnot, so I don't know how likely a culprit that is.

This may not sound like a major issue, but for my parents-in-law it appears to a be a dealbreaker with regards to their adoption of Ubuntu :)

Any help would be much appreciated!

Eric

---

### Post by karlmp on 2009-02-23
[http://ubuntutip.googlepages.com/](http://ubuntutip.googlepages.com/)

[http://brainstorm.ubuntu.com/idea/10787/](http://brainstorm.ubuntu.com/idea/10787/)

---

### Post by gandaran on 2009-02-23
many ubuntu users complain about adobe flash, I don't, I don't have any 3D video card (SIS M650/740) yet adobe flash works just as well normal/full window as in windows xp! it's most likely a problem with your video card drivers!
you don't need to have two flash packages (adobe-flashplugin and flashplugin-nonfree) installed, they are exactly/install the same adobe flash plugin (Shockwave Flash 10.0 r15)

---

