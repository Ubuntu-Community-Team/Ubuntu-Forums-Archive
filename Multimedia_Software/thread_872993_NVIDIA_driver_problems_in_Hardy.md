---
title: "NVIDIA driver problems in Hardy"
date: 2008-07-28
forum: Multimedia Software
---

### Post by Randybob on 2008-07-28
I'm stuck in 800x600 resolution right now. Let me tell you how I got here.

1) I upgraded from 7.10 to 8.0.4.1
2) I did some tinkering which I can't remember to get the graphics driver to work like it should.
3) I thought it would be a good idea to upgrade the driver (from nvidia-glx-new to nvidia-glx-new-envy in Synaptic)
4) I was stuck in low-res
5) I did some tinkering, which I can't remember all of. Part of it included specifying 1600x1200 in xorg.conf.
6) The login screen was still stuck in low-res.
7) I said "screw it" and decided to revert to the older driver, where everything worked. I uninstalled nvidia-glx-new-envy in Synaptic, and installed nvidia-glx-new. I log out.
8) I tried configuring the graphics card when Ubuntu told me it was running in low-graphics mode.
9) Now I'm stuck in 800x600 with a low refresh, in both the login screen and after I've logged in. And xorg.conf is specified to 1600x1200, which fixed it last time, IIRC.

How do I clean this mess and get everything working right again?

---

