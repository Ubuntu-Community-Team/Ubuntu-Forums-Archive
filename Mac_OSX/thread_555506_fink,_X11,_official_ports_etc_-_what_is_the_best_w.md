---
title: "fink, X11, official ports etc - what is the best way to use open source on OSX?"
date: 2007-09-20
forum: Mac OSX
---

### Post by Tommerz on 2007-09-20
Hey guys,

I was about to install inkscape using the package from their website when it occurred to me that using fink to install it might be a better idea.

So i was wondering, what is the best way to install unix software in osx? Is it to install direct from website's packages, or to use fink?

And what about Gentoo?

One small thing I noticed is that there is no xara xtreme port for osx yet - would compiling it with it's dependencies installed work? Is there a package in gentoo/fink?

---

### Post by cmeeks2662 on 2007-09-20
With lots of applications like Gimp and Open office X11 is about your only option.  NeoOffice runs native on OSX and is a port of OpenOffice.org.  I used OpenOffice.org and Gimp in X11 for over a year with no problems I have switched to NeoOffice and no longer run Gimp, I would use gimp again just that I did a clean install and did not reinstall X11 or Gimp.
All in all it would be nice if X11 would go away and everything would run native.

---

### Post by hanzomon4 on 2007-09-20
Can OSX use the bsd style ports system

---

### Post by tgalati4 on 2007-09-21
I use a combination of Fink, ported applications to native OS X, and compiling from scratch.  Some applications are easier to port than others into the Mac environment.  Fink provides a good start to get useful packages.  3rd-party ports to the Mac environment look cleaner and sometimes run better.  I compile applications that I can't find othersize.  The XDarwin server runs OK.  I can run an entire remote Dapper desktop on one of my 8 workspaces under OS X.  I'm using Desktop Manager to get multiple workspaces.

It's not ideal, but OS X runs much better than Ubuntu on a powerbook G4.  It's a little more bloated than Ubuntu, but all of the hardware works as predicted.  Since Canonical dropped support for ppc, I'm OK with using OS X.

---

### Post by mcduck on 2007-09-25
> **hanzomon4 said:**
> Can OSX use the bsd style ports system

yes, there is MacPorts project: [http://www.macports.org/]("http://www.macports.org/")

---

### Post by FredB on 2007-10-18
When I used MacOS-X, I was fond of Fink. Older software than MacPorts (called darwinports at this time), but at least, no need to wait an hour to get the source built.

---

### Post by atlascomplete on 2007-10-30
When I used OpenOffice.Org on my Mac, I just used X11, which I installed from the Mac OSX installation discs.

---

