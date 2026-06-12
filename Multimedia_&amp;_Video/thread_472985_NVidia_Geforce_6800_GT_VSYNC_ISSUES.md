---
title: "NVidia Geforce 6800 GT VSYNC ISSUES"
date: 2007-06-13
forum: Multimedia &amp; Video
---

### Post by Iniquity2012 on 2007-06-13
I have recently installed Ubuntu 7.04 (Feisty Fawn) as a replacement for Windows XP on my desktop.  At this point, I have everything working and no longer need Windows XP for anything.  The only issue I am having is with Vsync.  I have an NVidia GeForce 6800 GT installed in my machine and I'm using the non-free glx drivers installed through Synaptic Package Manager.  I've used nvidia-settings to setup my videocard settings, but some of the options do not seem to work.

For example, even if I setup the XVideo and the OpenGL settings to enable VSync, I still get visual tearing when moving windows, using 3D, or watching videos.  I've tryed it with or without.   Also, I found a program called nvclock which can be used to overclock the card and enable several other options.  It has an option to query the card to check what features are on or off, and also to enable or disable them.  I queried the vsync and it shows as off, and even after I enable it -- I still have tearing.  I checked using glxgears and I'm getting around 4000 frames per second.  

Is there anyway to FORCE vsync on?  Maybe through xorg.conf?  Or is something wrong with VSync in Ubuntu?

---

