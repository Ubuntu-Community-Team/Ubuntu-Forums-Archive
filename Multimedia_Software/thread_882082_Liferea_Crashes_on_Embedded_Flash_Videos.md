---
title: "Liferea Crashes on Embedded Flash Videos"
date: 2008-08-06
forum: Multimedia Software
---

### Post by mocha on 2008-08-06
I have an issue with Liferea on Ubuntu Hardy, issue is that after viewing anywhere between 5 to 10 feed entries that contain embedded Flash videos it causes Liferea to crash.  It's an intermittent problem and the output in the terminal points to /usr/lib/flashplugin-nonfree.  This happens with the repository version as well as the latest version 1.4.18.  I'm using the standard Flash v9 as installed with package flashplugin-nonfree.  I purged and reinstalled just to be sure.  I also have the nspluginwrapper package installed which prevents Firefox crashing, but it doesn't help Liferea.

I spoke to the author of Liferea and he says the problem is external to Liferea, it has something to do with Flash or widgets for HTML or something like that, I don't remember exactly.

Anyway, the strange thing is that this only happens on my Core 2 machine.  I don't have the same issues with my Barton system.  I don't know why other than the Barton was an upgrade from Gutsy and the C2D is a fresh install of Hardy.

I did all kinds of testing on this.  I tried different versions of libflashplayer.so, I tried running Liferea with padsp and aoss wrappers.  I have libflashsupport installed. etc etc.

Another strange thing is that after purging and reinstalling flashplugin-nonfree, now Liferea no longer displays the embedded Flash videos!  After this happened I tried soft linking libflashplayer.so to /usr/lib/xulrunner-addons/plugins/libflashplayer.so and they started working again, however it was back to the intermittent crashing.  Same thing no matter which version of libflashplayer.so I tried.

A final curve ball in all this, when I first installed Hardy fresh, the Flash videos were working in Liferea, so what did I do since then that caused a purge and reinstall to make them stop working?  Clearly some other package(s) installed since the system was new has interfered.

Any ideas what may be causing these issues?

---

