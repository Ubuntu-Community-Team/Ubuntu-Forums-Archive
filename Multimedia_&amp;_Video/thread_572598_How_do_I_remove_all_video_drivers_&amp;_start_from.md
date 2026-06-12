---
title: "How do I remove all video drivers &amp; start from scratch?"
date: 2007-10-10
forum: Multimedia &amp; Video
---

### Post by stoomaroo on 2007-10-10
[Noob post /begin]

I am fairly new to Ubuntu and trying to get my video settings running as smoothly as possible with my ATI Radeon X800.  Out-of-the-box, everything works fine...however I have no 3D rendering despite all my efforts.  

I have been following several posts here, to try to get it all working.  I get the feeling though that I have changed soooo many settings, that I am thrashing about trying to get something to work.

So a couple of questions: 

What is the best way to remove *all* my video drivers, and start from scratch (i.e. fglrx, ATI, etc...)?  I'd love to be able to know that I have a clean system to roll back to, without all my mucked-up video driver attempts.

What is the recommended path to install 3D rendering (i.e. don't need details - just basic guidelines)?  I see a lot of people asking about specific errors, but no one discussing the "general order of things.".  i.e. Do I install proprietary drivers first? FGLRX first?  Pull out Mesa last?....etc...etc...I guess I'm looking for the basic roadmap. I am using this "HOWTO":  [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) - but wanted to know if there is anything different between the ATI drivers (from ATI's site & the fglrx provided)...

stoomaroo!
[Noob post /end]

---

### Post by stoomaroo on 2007-10-11
This post is a partial start for removals.  No word on whether I have actually changed my config back to the "vanilla" install...but it's a start:

[http://ubuntuforums.org/showthread.php?t=143283&highlight=howto+remove+video+drivers](http://ubuntuforums.org/showthread.php?t=143283&highlight=howto+remove+video+drivers)

---

### Post by stoomaroo on 2007-10-11
So far so good, I seem to have cleaned it all out, and have re-installed fglrx.

Then I installed the ATI proprietary driver (obtained from the ATI site).  I get the following results (1680x1050@60Hz):

> stoomaroo@nobody:~$ glxgears
3165 frames in 5.1 seconds = 622.764 FPS
4407 frames in 5.1 seconds = 867.154 FPS
4407 frames in 5.1 seconds = 864.878 FPS
4407 frames in 5.1 seconds = 868.771 FPS
4407 frames in 5.1 seconds = 868.690 FPS
4407 frames in 5.1 seconds = 865.172 FPS

stoomaroo@nobody:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)


...still no direct rendering though...

> stoomaroo@nobody:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No
....


So I used the following Ubuntu forum help:
[http://ubuntuforums.org/showthread.php?t=560066&highlight=HOWTO+reconfigure+xorg](http://ubuntuforums.org/showthread.php?t=560066&highlight=HOWTO+reconfigure+xorg)

and I get this:
> stoomaroo@nobody:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R300 20060815 AGP 1x x86/MMX+/3DNow!+/SSE2 TCL
OpenGL version string: 1.3 Mesa 6.5.2

stoomaroo@nobody:~$ glxgears
14153 frames in 5.0 seconds = 2819.596 FPS
18893 frames in 5.0 seconds = 3758.498 FPS
18927 frames in 5.0 seconds = 3762.302 FPS
18874 frames in 5.0 seconds = 3759.375 FPS
18787 frames in 5.0 seconds = 3755.240 FPS
18873 frames in 5.0 seconds = 3761.514 FPS
18860 frames in 5.0 seconds = 3751.792 FPS
17541 frames in 5.0 seconds = 3496.748 FPS
18820 frames in 5.0 seconds = 3750.601 FPS
18813 frames in 5.0 seconds = 3757.760 FPS

stoomaroo@nobody:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No


Better, however, when I uninstall xorg-fglrx-drivers from synaptic, my resolution shoots to 1280x1024@76Hz and....

> stoomaroo@nobody:~$ glxgears
27294 frames in 5.0 seconds = 5458.767 FPS
38788 frames in 5.0 seconds = 7757.553 FPS
38838 frames in 5.0 seconds = 7767.457 FPS
38847 frames in 5.0 seconds = 7769.253 FPS
38862 frames in 5.0 seconds = 7772.381 FPS


Holy cow!  Who knows whether this is due to the resolution change though...??? :(

After re-installing ATI drivers:

> stoomaroo@nobody:~$ glxgears
15731 frames in 5.0 seconds = 3133.018 FPS
18754 frames in 5.0 seconds = 3737.963 FPS
18761 frames in 5.0 seconds = 3734.443 FPS
18741 frames in 5.0 seconds = 3736.801 FPS
18806 frames in 5.0 seconds = 3740.078 FPS
18801 frames in 5.0 seconds = 3739.907 FPS


The resolution is back now (1680x1050@60Hz).  But I only get about half....

Then I did this:

> sudo aticonfig --initial --force   ...and I finally get:

> stoomaroo@nobody:~$ glxgears
3362 frames in 5.0 seconds = 670.730 FPS
4407 frames in 5.1 seconds = 869.563 FPS
4407 frames in 5.1 seconds = 864.654 FPS
4407 frames in 5.1 seconds = 869.596 FPS
4407 frames in 5.1 seconds = 868.656 FPS
4407 frames in 5.1 seconds = 863.987 FPS


Anyways....time for a break, and I'll try again later.

---

### Post by stoomaroo on 2007-10-12
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) 

...was a skeptic, followed it to the letter.  Now I have this:

> stoomaroo@nobody:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 XL
OpenGL version string: 2.0.6334 (8.34.8 )


> stoomaroo@nobody:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2


I'll post another thread on how to tweak it shortly.

stoomaroo

---

