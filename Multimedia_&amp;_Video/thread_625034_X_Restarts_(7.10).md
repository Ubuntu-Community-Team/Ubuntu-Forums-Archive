---
title: "X Restarts (7.10)"
date: 2007-11-27
forum: Multimedia &amp; Video
---

### Post by ntay on 2007-11-27
Whenever I attempt to play a video, run an OpenGL game, and things like that, X seems to restart.

I have little experience with Linux, especially Ubuntu, so bear with me.

I have an ATi Graphics card, and I'm running Compiz Fusion w/ xgl.  I'm running Ubuntu 7.10.

Any suggestions? 

Thanks!

-Nick Taylor

---

### Post by nzadLithium on 2007-11-27
it could be the way your driver is setup. when you say it restarts do you mean it goes black then comes back or it goes back to the login screen?

---

### Post by ntay on 2007-11-27
It goes to black, then to the login screen.

---

### Post by nzadLithium on 2007-11-27
im not sure but try running this in terminal it might fix.

sudo aticonfig --overlay-type=Xv
i think you have to restart pc to get it to take effect.

---

