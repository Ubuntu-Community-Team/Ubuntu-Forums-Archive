---
title: "ATI Graphics card benchmark between Windows and Linux using Quake 3"
date: 2007-12-30
forum: Multimedia &amp; Video
---

### Post by altenor on 2007-12-30
Hello,

I've used the "\timedemo 1" function of Quake 3 to compare FPS rates between Ubuntu Gutsy 7.10 and Windows XP on my laptop.

On Ubuntu using wine to run Quake 3 I get 60 FPS, on Windows 150 FPS. This factor 2.5 is kind of a pain. Is it the best I can hope for or did I not configure the fglrx driver properly ?

My chipset is :
ATI Technologies Inc M22 [Mobility Radeon X300]

I have a fresh Ubuntu Gutsy 7.10 installed and the ATI proprietary driver installed via Ubuntu's restricted drivers manager.

Direct rendering is activated. Glxgears runs at 1200 FPS, fgl_glxgears at 300 FPS.
fglrxinfo :
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X300
OpenGL version string: 2.0.6473 (8.37.6)


Thanks.

---

### Post by mgmiller on 2007-12-30
The problem, I think, is you are running the game in wine.  There are Linux ports available for Quake III and several other ID games.  Try looking here:  [http://zerowing.idsoftware.com/]("http://zerowing.idsoftware.com/")

I only play UT 2k4, which had a native linux installer on the retail disk, so I'm not sure how to do it for Quake, but if you google around a bit, you should find answers.

Good Luck.

Edit:
I just found a nice howto for installing quake 3 in ubuntu, give this a try:
[http://www.errorforum.com/gaming-tutorials/623-installing-quake-iii-ubuntu.html]("http://www.errorforum.com/gaming-tutorials/623-installing-quake-iii-ubuntu.html")

---

### Post by tkmn on 2007-12-30
Try ioquake 3

[http://ioquake3.org/get-it/](http://ioquake3.org/get-it/)

---

