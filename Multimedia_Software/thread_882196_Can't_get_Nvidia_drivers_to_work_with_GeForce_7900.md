---
title: "Can't get Nvidia drivers to work with GeForce 7900GT"
date: 2008-08-06
forum: Multimedia Software
---

### Post by littlejborn on 2008-08-06
I'm having problems getting the official nvidia drivers to work with my GeForce 7900GT.  I just did a clean install of Ubuntu 8.04 (running Gnome).  I am able to use Ubuntu on a single monitor at 1600x1200 using the original (generic?) drivers that installed with Ubuntu (without 3D support), but when I try to install nvidia drivers using synaptic, apt-get, envyng, or the .run installer from nvidia's website none of them work. For any of the installation attempts the same thing happens: When I start up gdm it goes to a video configuration menu. I can pick the resolution for both my monitors (I really want my dual monitor setup to work as well as Compiz Fusion and AWN) and change the graphics card from the generic VESA driver to the "nvidia" driver but then after closing that menu the screen goes black and eventually comes up to the GDM login screen running at 800x600. I've also tried leaving it at the VESA driver and specifying "nvidia" as my driver in the xorg.conf file but after restarting X it did the same thing. Also, if I go into the screen resolution app I am only given the options of 800x600 and 640x480, even when my xorg.conf file has the higher resolutions specified in it from the video configuration that I changed after starting up gdm.

Help?!

---

