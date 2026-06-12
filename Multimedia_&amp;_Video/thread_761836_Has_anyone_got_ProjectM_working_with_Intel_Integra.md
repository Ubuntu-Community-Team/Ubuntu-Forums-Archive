---
title: "Has anyone got ProjectM working with Intel Integrated graphics?"
date: 2008-04-21
forum: Multimedia &amp; Video
---

### Post by dixonstalbert on 2008-04-21
Hello

I was able to install ProjectM (port of Winamp's Milkdrop visualizations) from repositories on my desktop/nvidia 5200 without a problem.

Not having much luck with laptop/Intel integrated graphics 915G.


Both ubuntu package and subversion source package install on my laptop, but they run at 100% cpu usage and the visualizations run at only 2 frames per second if you enlarge them any bigger than a postage stamp.


Can someone else with  Intel graphics try ProjectM and see what their frames per second is?

The easiest way to do this is to search synaptic package manager for projectm and install packages. 

If you have Amarok music player, select Tools>Visualizations> then check projectm.
Click on projectm window and press F5 and it will tell you how many fps it is running at.

Thanks 

Dixon




so far I have tried

1. Posting on ProjectM sourceforge page. Developer (Pete) answered saying my glxinfo did not list GL_EXT_framebuffer_object extension. My glxinfo reports about a dozen other open gl extensions and  direct rendering on and glxgears is running at around 1000. I don't how to turn this particular OpenGL extension on. I have tried reinstalling all my glib libraries but this did not seem to help. 

2. fiddling with all the options listed in man intel for my xorg.conf file; no luck 

3.fiddling with driconf tool- could only make glxgears worse with these settings

---

### Post by dixonstalbert on 2008-06-10
I installed Fedora 9 on same hardware and projectm works properly; ie runs at 17 fps and no drain on cpu.

I will have to do a little detective work and see what FC9 is doing differently that allows projectm to work correctly.

---

