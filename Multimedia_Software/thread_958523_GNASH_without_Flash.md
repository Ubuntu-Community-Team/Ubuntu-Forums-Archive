---
title: "GNASH without Flash?"
date: 2008-10-25
forum: Multimedia Software
---

### Post by Aurora on 2008-10-25
Greetings,

When I installed Hardy, I decided to see how far I could get without any non-free software, so I installed GNASH but not Flash. The comprehensive multimedia sticky in this forum says to install all kinds of non-free stuff, so I didn't follow its instructions.

So far I haven't been able to see YouTube or any websites using Flash. I see the "install plugin" dialog box all the time. I was surprised to find out from gnu.org that YouTube is supported; I figured it just didn't work yet.  Is there more I can do?  I am running Ubuntu Studio, if that makes a difference.

Thanks,

Paul

---

### Post by gandaran on 2008-10-25
gnash doesn't work with youtube, I believe gnash only supports flash 8 videos, maybe a new version will
if you don't want to use adobe flash 10 remove gnash and try swfdec flash plugin

did you just install gnash but not the gnash plugin for firefox?

---

### Post by BetaMaster on 2008-10-25
Gnash *does* work with YouTube. I'm running the latest version of Gnash (0.8.4) and YouTube plays fine.

You probably don't have the Gnash Firefox plugin, as gandaran asked. Not only that, but to properly view YouTube with Gnash, you need to have the ffmpeg plugin for gstreamer installed (it's in the sources as gstreamer0.10-ffmpeg)

Good luck!
Incidentally, on my recent reinstall of linux (going from Hardy to Intrepid) I decided to see how far I could go on free software too. So, for the most part, I'm in the same boat you're in!

---

### Post by gandaran on 2008-10-25
> Gnash does work with YouTube
didn't know that, I have never used it, I just said it doesn't work because I read so many posts here about gnash and youtube problems, maybe it's the ffmpeg plugin that does the trick, learning new things everyday!
> I decided to see how far I could go on free software too
you must mean  open source software! adobe is free too only proprietary software

---

### Post by BetaMaster on 2008-10-25
> **gandaran said:**
> didn't know that, I have never used it, I just said it doesn't work because I read so many posts here about gnash and youtube problems, maybe it's the ffmpeg plugin that does the trick, learning new things everyday!
It partly is, but it's also very dependent on the version of Gnash you're running. IIRC, the sources for Hardy have 0.82, which didn't work with YouTube. Intrepid's sources contain the latest version, 0.84, which does work with YouTube (with the ffmpeg plugin installed).
You can compile 0.84 from source, but I had a lot of trouble doing it. Lots of dependencies that were a pain to track down and install all of.

> **gandaran said:**
> you must mean  open source software! adobe is free too only proprietary software
Adobe Flash is non-free, or proprietary - I don't mean free in the monetary sense, I mean that it's open for modification, distribution, and open - Flash is not open for modification. So, I do mean open-source software, but Flash is not free :)

---

### Post by Aurora on 2008-10-26
> **BetaMaster said:**
> It partly is, but it's also very dependent on the version of Gnash you're running. IIRC, the sources for Hardy have 0.82, which didn't work with YouTube. Intrepid's sources contain the latest version, 0.84, which does work with YouTube (with the ffmpeg plugin installed).
You can compile 0.84 from source, but I had a lot of trouble doing it. Lots of dependencies that were a pain to track down and install all of.

Well, I installed the ffmpeg gstreamer plugin and the Firefox GNASH plugin.  If I'm lucky they'll backport GNASH 0.84; I really don't want to compile, and I'm sticking with Hardy for awhile. Whenever I get 0.84, it will hopefully work. Thanks for your help.
--PD

---

### Post by bieber on 2008-10-26
> **gandaran said:**
> 
you must mean  open source software! adobe is free too only proprietary software

[http://www.gnu.org/philosophy/free-sw.html](http://www.gnu.org/philosophy/free-sw.html)

---

