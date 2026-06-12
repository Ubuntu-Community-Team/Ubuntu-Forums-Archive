---
title: "Openbox + NVidia + compositing = tearing."
date: 2010-06-22
forum: Multimedia Software
---

### Post by DucentiVigintiDuo on 2010-06-22
Hey everyone.

I am on a [Macbook Pro 5,5]("https://help.ubuntu.com/community/MacBookPro5-5/Lucid"). I'm an old Ubuntu convert that turned back to the sinful ways of OS X only to come back to the pure and awesome world of Linux. I tried several distros and passing through Crunchbang I realized I really like the Openbox manager. As a result, I've been using Openbox on Ubuntu (both as a window manager for GNOME and on its own).

The problem I'm having is with compositing and video tearing.
I'll try to make it as simple as possible:

1) Gnome + Openbox + Compositing (xcompmgr, cairo-compmgr) = Video tearing.

2) Openbox + Compositing (xcompmgr, cairo-compmgr) = Video tearing.

3) Gnome + Compiz Fusion Compositing = Video Tearing.

4) NO COMPOSITING (all scenarios) = Regular video output.


I've tried the instructions [here]("http://www.omgubuntu.co.uk/2010/01/how-to-stop-video-tearing-vlc-nvidia.html") when using Compiz Fusion and in all scenarios Sync to VBlank is enabled both on the XVideo Settings and the OpenGL settings within the Nvidia X Settings panel.

I'm pretty happy keeping compositing off and having my video play normally but I'd also like to have a nice dock like Docky. Is there any way for me to get a nice dock working under Openbox without compositing or for some sort of compmanager to work without having tear on my videos? It's not something crucial but it would really make my Linux experience quite perfect as the combination of Openbox and a sort of dock would be a very powerful one.

Thanks in advance!

---

### Post by cbrunhaver on 2010-06-23
For me, (not on a mac though) I had to install CompizConfig Settings Manager.

Under System -> Preferences -> CompizConfig Settings Manager -> General Options, there is a tab called Display settings.  Make sure that "synch to Vblank is checked and set the refresh rate to twice your actual refresh (e.g. 120 for a 60 Hz refresh).

---

