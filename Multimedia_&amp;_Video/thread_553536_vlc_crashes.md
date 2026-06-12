---
title: "vlc crashes"
date: 2007-09-17
forum: Multimedia &amp; Video
---

### Post by bit188 on 2007-09-17
Hello all: I am running a 400MHz iMac G3 with 384MB of RAM, Feisty.

Every time I try to open a file with VLC, it crashes immediately. VLC played fine when I had OS X installed.

Thanks.

---

### Post by aysiu on 2007-09-18
Open up [a terminal](http://www.psychocats.net/ubuntu/terminal) and type ```
vlc
``` When it crashes, paste the output into a Google search.

---

### Post by bit188 on 2007-09-20
Nothing on Google, but here's the text it spit out:

** (.:5054): CRITICAL **: clearlooks_style_draw_focus: assertion `height >= -1' failed
[00000350] main private error: option glx-shm does not exist
Illegal instruction (core dumped)

---

### Post by aysiu on 2007-09-20
Looks like a bug that's unsolved:
[https://answers.launchpad.net/ubuntu/+source/vlc/+question/10127](https://answers.launchpad.net/ubuntu/+source/vlc/+question/10127)
[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/67605](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/67605)

Maybe use something other than Clearlooks?

---

### Post by harakiri1976 on 2007-09-21
Hi Guys!


I'm having problem with VLC too. The problem is very weird :( When I open a file, an .avi file, Xvid, whatever, it plays because I can hear the sound but there's no image!:( And the worse is that I try to move the size of the window, minimizing it and touching in some places of the screen with a Left mouse Click, I CAN SEE THE MOVIE VERY WELL!...the problem is that I can't touch it again or I can loose the image again. I don't know why it happens:( ...because XINE works very Well. :(

No image happens in all Video programs when I try to rotate the Cube with a Movie running. And that happens with all programs! The windows get black :( I am running Compiz in Feisty Fawn, Pentium 4, 3.4 GHz, 1GB of RAM and ATI Radeon with 128Mb.


Hope anybody can help :(

Thanks

---

