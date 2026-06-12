---
title: "choppy dvd playback in Unity but not in Gnome"
date: 2011-11-09
forum: Multimedia Software
---

### Post by gleedadswell on 2011-11-09
Hi everyone,

This is not an "I hate Unity" post.  I've installed 11.10 plus the Gnome fallback (just in case) on an HP laptop with dual AMD E-350 Processor and an AMD Radion HD 6300 graphics card.  I'm giving Unity a try and cautiously reserving judgment.  Here is one problem I've noticed, though.

Under Unity my dvd playback in both Movie Player and vlc is choppy.  I've tried to resolve this in all the usual ways (installation of proprietary graphics drivers, getting the libdvdread4, libdvdnav4, libdvdcss2, etc. packages, changing video output format in vlc...).  None of this changes the choppy playback.

The one thing that does fix the choppy playback is logging in under Gnome classic instead.

Any ideas why this might be?  Could it be something to do with the different ways compositing is handled in these two desktops??  It doesn't worry me overly.  I'm guessing Unity is still new enough that a lot of problems like this are just normal teething pains.  I figure a few weeks of saying "yes" to upgrades and the problem will go away.  By that time I might have switched back to Gnome anyway.  But like I say, I'm cautiously reserving judgment for now.

---

### Post by BicyclerBoy on 2011-11-10
Unity is "just" a compiz profile albeit an unflexible one.

Worth trying composite manager ccsm..
- composite/un-redirect full screen

There are other options that may help in workarounds & openGL.

Be very careful with ccsm settings, unity turns into a mess with just a little help.

unity --reset

VA-API is the h/w decode acceleration api that works with AMD XvBA. Need the catalyst driver & splitted-desktop-systems packages.

---

### Post by gleedadswell on 2011-12-17
Yeah, I'm currently leaving ccsm alone.  I've broken Unity a few times with ccsm and had to do a unity-reset.  Sure hope its stability increases in 12.04!

Despite that I'm liking Unity a lot.  As long as I leave its settings alone it is stable and I'm finding it a very efficient work environment.

---

