---
title: "open office can't seem to be working with fglrx."
date: 2006-11-23
forum: Multimedia &amp; Video
---

### Post by shawn.YH.Kim on 2006-11-23
Hi, I'm happly using edgy.
Except one thing.
My laptop has ATI MOBILITY RADEON X300 graphic card on it.
When I configured my X.org with fglrx on as follows :

    ygdrasil:~$ fglrxinfo
    display: :0.0  screen: 0
    OpenGL vendor string: ATI Technologies Inc.
    OpenGL renderer string: MOBILITY RADEON X300 Generic
    OpenGL version string: 2.0.6011 (8.28.8)

the open office suite just can't seem to start spitting out messages like these :

    ygdrasil:~$ oowriter

    ** (process:5807): WARNING **: Unknown error forking main binary / abnormal early exit ...
    ygdrasil:~$ 

The strange thing is, if I unload fglrx driver, it's ok with oowriter. OOwriter goes well.

My desktop has :

ygdrasil:~$ dpkg -l |grep xorg
ii  xorg                                       7.1.1ubuntu6                   X.Org X Window System
ii  xorg-driver-fglrx                          7.1.0-8.28.8+2.6.17.6-1        Video driver for ATI graphics accelerators
ii  xorg-driver-fglrx-dev                      7.1.0-8.28.8+2.6.17.6-1        Video driver for ATI graphics accelerators (

Here is one more thing that might help figuring out the problem.
One of my colleagues tried to run it under dapper, using xorg of version 7.0 or something, he tried on fglrx and it was OK with open office. His laptop is the same model as mine.

Anybody has any idea?

(ps. i tried libGL.1.2.so that joshrobinson has kindly uploaded. unfortunately, it didn't work with my case)

---

