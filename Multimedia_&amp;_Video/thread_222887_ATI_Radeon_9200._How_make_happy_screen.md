---
title: "ATI Radeon 9200. How make happy screen?"
date: 2006-07-25
forum: Multimedia &amp; Video
---

### Post by mjpatey on 2006-07-25
I have an ATI Radeon 9200 graphics card.  I've seen post after post offering suggestions on how to use it to its full capacity, but they're all slightly different.

Does anyone know THE definitive link that contains the best information on how to install the right driver for the 9200 in Dapper?

My issues with the performance of the generic ATI driver are general slowness in both 2-D and 3-D graphics.  When dragging a window over another window, for example, I get a long trail behind the window I'm dragging.  And in the 3-D realm, Google Earth using OpenGL is not a pretty sight!  Not to mention the embarrassment of slow screensavers... :-)

I realize these things seem trivial, buy they make the system feel slow, even though it's a 3.2GHz processor with 1.5GB of fast RAM.

Any help would be greatly appreciated!

-Mark

---

### Post by Seamus on 2006-07-25
Mjpatey,

I'm more interested in getting it using teh drivers in the first place! 

Any tips on how you got it using it? what is your output equivalent to this:

> $ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)


I can't get it recognising the ATI drivers at all - I hve a 9250 card, so very similar :(

---

### Post by mjpatey on 2006-07-25
Hmm... this is what I get:

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

I did try several times to install fglrx (or whatever), and honestly don't remember where I left off in the process.  I almost feel as if I'd be better off reinstalling Ubuntu and attacking the problem anew at that point.

Any suggestions?

-Mark

---

### Post by Seamus on 2006-07-25
Mark,

I don't think you are actualling using the correct ATI drivers then... I have seen other outputs from that that actually list the ATI drivers etc as the vendor and renderer....

---

### Post by BigJerm on 2006-07-26
I am also sick of having low FPS screensavers. I have Direct Rendering enabled, and I get about 900FPS in glxgears. Can't understand, why the screensavers performance is so bad. I am currently using a Radeon 9200SE.

fglrxinfo
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9200SE DDR Generic
OpenGL version string: 1.3.1060 (X4.3.0-8.24.8)
```

---

