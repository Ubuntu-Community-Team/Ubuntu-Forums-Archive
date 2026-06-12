---
title: "Intermittent VLC Crashes during playback"
date: 2010-04-08
forum: Multimedia Software
---

### Post by aeternitas on 2010-04-08
I've been running into issues with VLC crashing now and again, particularly when seeking through the current item using the bar (as opposed to Ctrl-Right Arrow/Left Arrow); it may have happened in a few other spots, but that's usually when I'm not at my keyboard. All files are stored locally on my HD, mostly .avi video.  For the most part, when I'm using VLC, I've got Firefox and maybe a Nautilus window running as well.  CPU use, Memory use, and System load stay pretty well down (and I've never managed to get my swap usage above 120MiB of the 1.2GiB on the Swap partition).  I've tried removing and reinstalling VLC, no dice; about screen lists Ver 1.0.2 Goldeneye.  

A side effect of this is that, until I restart the system, the screen is unable to be put to sleep at it's timeout; in the notification bar of the top panel, an icon appears and (if the mouse is left there) a little box will appear with text as follows:

Session active, not inhibited, screen idle.
If you can see this text, your display server is broken and you should notify your distributor.
Please see [http://blogs.gnome.org/hughsie/2009/08/17/gnome-power-manager-and-blanking-removal-of-bodges/](http://blogs.gnome.org/hughsie/2009/08/17/gnome-power-manager-and-blanking-removal-of-bodges/) for more information. 

The URL there listed doesn't have any information that seems to be useful, but, I'd presume that VLC does something to prevent the screen turning off while it's playing (a situation where most folks aren't going to be typing or mousing around), which is undone when VLC ends cleanly (and re-opening, then exiting doesn't fix it).  Any ideas/suggestions?

---

### Post by URGettingADull on 2010-05-20
Go to tools>>>preferences>>>video and set the display output to x11 output and see what that does.  I was having a similar problem after updating my xserver through synaptic and this did the trick.

---

### Post by aeternitas on 2010-05-21
Thanks for the reply.  Giving it a go, doesn't seem to be hitting me as bad after upgrading to Lucid but still an occasional problem. Hopefully, this gets it done :)

---

