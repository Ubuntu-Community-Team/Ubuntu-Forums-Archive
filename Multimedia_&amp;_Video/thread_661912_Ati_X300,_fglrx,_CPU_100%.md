---
title: "Ati X300, fglrx, CPU 100%"
date: 2008-01-08
forum: Multimedia &amp; Video
---

### Post by didanoff on 2008-01-08
Hello community :)
I use 7.10 on notebook win ATI Mobility X300.
I install the latest fglrx driver from ati.com
using: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

user@Argo:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X300
OpenGL version string: 2.1.7170 Release

root@Argo:/var/log#glxinfo | grep direct
direct rendering: Yes

user@Argo:~$ glxgears
8420 frames in 5.0 seconds = 1687.183 FPS
8265 frames in 5.0 seconds = 1653.941 FPS

I think its normal results?
But when I run glxgears or other 3G game, CPU is 100%
And games are very slowly :( 

Many thanks for any question :)

---

