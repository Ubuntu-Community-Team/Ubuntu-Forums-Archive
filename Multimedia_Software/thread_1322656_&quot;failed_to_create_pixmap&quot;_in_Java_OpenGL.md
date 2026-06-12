---
title: "&quot;failed to create pixmap&quot; in Java OpenGL (with Radeon driver)"
date: 2009-11-11
forum: Multimedia Software
---

### Post by cobratbq on 2009-11-11
Okay, so I'm a pretty long time Ubuntu user, but whatever I try, I simply can't seem to get rid of Windows ... :P

So my current problem:
I'm working with Java OpenGL (jogl) for a school project ... and after some tweaking to get the code running on linux, I'm stuck with the following message "failed to create pixmap".

I haven't been able to find the error in the source code, which leads me to believe that it's from one of the libraries. I have found this [URL="http://groups.google.com/group/comp.soft-sys.math.mathematica/browse_thread/thread/de61c0159bc64421/fe69b93b1c430dbd?#fe69b93b1c430dbd"]
Plot3d causes crash with radeon driver and Debian testing[/URL], but I can't determine where that exactly puts the problem.

Since I'm not at all a OpenGL-guru I was wondering if someone could shed a light on the kind of problem and if there is a fix available.
If I could get some confirmation that it's not a silly configuration issue, then I'll create a bug on launchpad.

Running on: Karmic, open source radeon drivers, FireGL v5250 card. (anymore info needed?)

---

### Post by sjoerd.vanderveen on 2010-03-22
Hi,

I have this same problem trying to run Abaqus CAE on a system with a Radeon Xpress 200M.  It would be great if anyone who's solved the problem could communicate the configuration.

---

### Post by sjoerd.vanderveen on 2010-03-29
OK, not really a fix, but it took me quite a bit of time to figure it out, so it may save you same: if I deactivate all visual effects, the "failed to create pixmap"-error still appears, and the screen is not always correctlt refreshed, but at least the application runs!

---

### Post by cresent on 2010-07-02
Hi,

I am also new to Ubuntu and Linux world..

I found this in the Abaqus Licensing & Installation manual, which seemed to fix pixmap error:

./abaqus cae -mesa

good luck
C

---

