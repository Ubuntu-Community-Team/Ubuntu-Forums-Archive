---
title: "Tearing and choppy video w/ ION 330 vdpau in Xinerama"
date: 2010-08-24
forum: Multimedia Software
---

### Post by CryingFreeman on 2010-08-24
I have a ASRock ION 330 with **512 Mbyte** shared graphics memory. I use the **256.44** closed source nvidia drivers and have a Xinerama display consisting of one Asus 1440x900 monitor and one video projector with displaysize of 1280x720. 

Display: **1440x900 + 1280x720** in Xinerama

I have tried **with and without desktop effects** enabled, and I have followed the [http://tombuntu.com/index.php/2009/09/20/make-compiz-run-smoothly-and-without-tearing/](http://tombuntu.com/index.php/2009/09/20/make-compiz-run-smoothly-and-without-tearing/) guide to manually set the refresh rate to 60 Hz. The **sync to Vblank** option is checked, both in **CCSM** and **nvidia-settings** under **X Server Xvideo Settings** and under **OpenGL Settings**, to no avail.

The files I play are **MPEG-2 Transport Stream** in 720p. Some are and some are not in **Matroska** containers. 

I use **SMplayer** with **vdpau** enabled.

I've made a comparison of Windows Vista and Ubuntu 10.04 below:

[http://vimeo.com/14385969](http://vimeo.com/14385969)

It's not entirely clear from the video, but the end scroller is choppy on Ubuntu and relatively smooth in Windows Vista. 

This setup is to be run in a public cinema, and the chopping and tearing is a complete showstopper. :( It would be a nice showcase to have Ubuntu in the wild like this, but it can't be used if these issues are not resolved.

I'm desperate for help. Thanks in advance. :)

My xorg.conf: [http://paste.ubuntu.com/482850/](http://paste.ubuntu.com/482850/)

---

### Post by hsoulen on 2010-08-24
Hi there,

I have an Asus 1201n (ION with Atom 330) so similar specs in terms of the CPU and Vid. For my the solution is to turn off ALL compositing (no compiz at all) this is the only way I can avoid the tearing using Smplayer + VDPAU, I used to get the tearing all the time with any video (not just HD) but this has solved it for me.

I know you stated that you turned off all desktop effects so I apologize if this is just redundant, but you could try pure metacity as your window manager (no Gnome/KDE), may help.

Have you looked at XBMC? :[http://xbmc.org/](http://xbmc.org/)

They have a liveCD you can give it a shot, my preferred media front end and they support VDPAU now out of the box.

Cheers,

Hank

---

