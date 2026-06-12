---
title: "Problem with dualhead setup with intel-driver"
date: 2007-12-03
forum: Multimedia &amp; Video
---

### Post by kuse on 2007-12-03
I have a dualhead setup with my mythbuntu-box. I use a motherboard with the intel g35-chipset.
I have a pt-ae500 projector connected to my box with DVI-D cable.

When I start the box and gdm is loaded I have correct pixel-mapped resolution to my projector (720p) but after some time (a couple of minutes) the signal to the projector is lost and I have to restart X to get it back. 

I read on another forum that a guy had similar problem and his solution was to NOT use gdm cause it changes resolutions in some way. 
If I start the box without gdm autoloading and start X manually (startx) I get no signal at all to my projector (really wierd), no changes made In /etc/X11/xorg.conf.

Is gmd using some other X-setup merging it that with the existing xorg.conf?

I see 2 solutions to my problem. Find out why the signal is lost to the projector when using gdm or find out why I dont get any signal at all with the same xorg.conf without using gdm.

Anyone here have any clue to why my box is acting like this?

---

### Post by kuse on 2007-12-04
bumping, anyone got any clue?

---

