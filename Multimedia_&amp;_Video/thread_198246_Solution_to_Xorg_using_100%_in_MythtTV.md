---
title: "Solution to Xorg using 100% in MythtTV"
date: 2006-06-16
forum: Multimedia &amp; Video
---

### Post by Cosmic_Crusader on 2006-06-16
I noticed a few days ago that Xorg used 100% CPU when playing MythTV fullscreen.

After many trials I narrowed it down to the type of vsync being used, but also ensured I waqws using gcc-3.4 to compile (mainly because I am running AMD64).

MythTV must be compiled _without_ the "--enable-opengl-vsync" flag when runnign configure.

You can tell if this is a problem as during MythtTV's running you will see:
"[SIZE=2][COLOR=#000000]Video timing method: SGI OpenGL"
on the console (or in .xsession-errors).

You should see:
"[/COLOR][/SIZE][SIZE=2][COLOR=#000000]Video timing method: USleep with busy wait"
instead.

Now my CPU hardly shows Xorg as a running process in top at all.  Playback is smoother and there is no audio skipping.
[/COLOR][/SIZE]

---

