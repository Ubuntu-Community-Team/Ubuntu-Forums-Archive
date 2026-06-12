---
title: "having DVD playback issues"
date: 2008-08-07
forum: Multimedia Software
---

### Post by cooltd825 on 2008-08-07
i've only been using linux for maybe 6 or 7 months, but up until now i've had full DVD playback.  i recently installed Fedora 9 KDE4 on a friend's recommendation, and it basically sucked.  KDE 4.1 is better, but it still has its fair share of issues.  anyway, so I just reinstalled Ubuntu 8.04 last night.  everything is working perfectly, except DVD playback.  here's what happens when I try to play something from Xine (the problem is pretty much universal across VLC and Mplayer also, except Mplayer actually crashes)


> This is xine (X11 gui) - a free video player v0.99.6cvs.
(c) 2000-2007 The xine Team.
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading

this seems like a libdvdcss issue, but upgrading doesn't help either.  i'm pretty sure i have all the right plugins installed too.  
again, sorry for the newbie question.  maybe there's something i'm missing?  thanks!

---

### Post by silkstone on 2008-08-07
I have libdvdcss2, not libdvdcss.

EDIT/

It's...

libdvdcss2 version 1.2.9-2medibuntu4

---

### Post by cooltd825 on 2008-08-07
haha, i didn't have the medibuntu repos enabled.  i figured it was something stupid like that. problem solved.

thanks!

---

