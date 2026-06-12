---
title: "CPU overload (100%) when running sdl applications"
date: 2007-05-23
forum: Multimedia &amp; Video
---

### Post by agrabah on 2007-05-23
Hello!

This problem drives me nuts, as it is almost impossible for me to play games. It arose when I was playing Hopkins FBI, or sdl-jump. The Cpu just maxed out, stayed there - no matter what was going on in the game (it stayed at 100% even at the login screen of the game).
Now for some particulars of my machine:

HP compaq nx9010 laptop (specs: [http://reviews.cnet.com/laptops/hp-compaq-nx9010-series/4507-3121_7-30474669.html]("http://reviews.cnet.com/laptops/hp-compaq-nx9010-series/4507-3121_7-30474669.html")

The main culprit here is, I think, my ATI IGP 345M. I read this card isn't exactly linux friendly.
I somehow feel it has something to do with hardware acceleration - as if it wouldn't kick in, and the cpu would be doing al the work. I had similar problems with globulation, but then I configured openGL to run correctly, and the cpu load dropped more than 40%.
Similarly beryl works just dandy, without overloading my cpu.

Glxgears works (around 350 FPS), and glxinfo says DRI is on. I do not use fglrx, because it crashes my X.
I'm browsing the internet for a solution, but I just don't know really what to look for. I know hopkins fbi uses the sdl libraries... but is there a way to tell if it's rendered with the cpu or the accelerator? And how can I make sdl use the accelerator? Or is it just a bug, like sdl clogging my cpu?

Thanks for all help. It will be welcome.

                       Tine

---

### Post by Topper_H on 2007-06-06
Same problem here in Feisty, any 3d game (defcon, nwn, boson) shoots my cpu to 100% even in the lobby (no 3D there).
I have a Geforce FX5200 with nvidia-glx driver and a AthlonX2 3800+
This is driving me nuts.

---

### Post by Topper_H on 2007-06-09
Maybe a dupicate of the bug reported in this thread : [http://ubuntuforums.org/showthread.php?p=2810704](http://ubuntuforums.org/showthread.php?p=2810704)

---

