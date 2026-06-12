---
title: "Jaunty + KDE4 effects + Radeon X1950XTX = no go?"
date: 2009-05-16
forum: Multimedia Software
---

### Post by CHaoSlayeR on 2009-05-16
Hi all,

I have a serious problem. I've replaced my rather slow HD2400Pro with an X1950XTX because I got tired of hacking the xorg.conf from scratch each time a new driver gets released only to find out that something simply doesn't work. E.g. enable desktop effects in KDE4 and than play a video in mplayer. Result is a lot of flickering. 

So I wanted the fastest card I could get that is supported by the open-source drivers and as I had really good experience with a X1300Pro at work I thought it would work the same way for an X1950XTX.

So I installed the "new" card and all things where fine using the "radeon" driver. Dual-head? No problem. KDE4 effects? No problem. GLXGEARS? ~4800 FPS. Warzone2100? Smooth.

Well, and now to the problems:

When I run "glxgears" and then play a movie with "gmplayer" then the screen freezes completely although the mouse can be moved around smoothly but keyboard is not responsive. I then logged in through SSH from another machine and all seems fine, no errors in Xorg.0.log, high CPU usage of Xorg or some other strangeness. I then killed KDM - no change. I killed all processes successfully without a change on the screen. So as a last resort I isseud a reboot and when the BIOS came up the screen worked as expected again. This behavior can be reproduced, but only within KDE4 and with effects enabled. I tried to get the same or another misbehavior under XFCE without success, in addition I noticed that in XFCE even when using transparent windows, shadows or the like the video playback is completely stable, whatever I do. I simply couldn't get the playback to get stuck or being non-smooth.

In addition to that specific graphics card freeze I encountered another complete system freeze (including monitors turning off) occasionally when switching to another KDE desktop that has some application windows opened that are GTK apps. This never happened with non-GTK apps, which is really strange so I think this couldn't be a bug in the graphics driver but rather in KDE4.

Does anyone get similar freezes or even has a workaround (except switching off the effects) or a real solution?

Kernel: 2.6.28-12-generic
KDE version: 4.2.2
Video driver: radeon 6.12.1

I haven't tested the latest 6.12.2 driver yet. Does anyone have those build against jaunty?

Thanx,

C]-[aoZ

---

