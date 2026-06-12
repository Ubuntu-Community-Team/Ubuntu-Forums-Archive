---
title: "No sound on .pps file"
date: 2010-11-09
forum: Multimedia Software
---

### Post by one_iota on 2010-11-09
Someone emailed me a .pps file (MS PowerPoint presentation) which contains slides with accompanying music.

When I double click the file it opens with OpenOffice.org Presentation and the slide show plays but the music does not. My sound is fine for all other applications. I'm running Ubuntu 10.10 and the version of OpenOffice I have is ooo-build 3.2.1.4. I run Update Manager frequently so my system is up to date.

What could be causing the lack of sound?

---

### Post by pgoetz on 2010-12-26
I have a bug posted for this on launchpad: Bug 680560

This seems to be a problem with Ubuntu 10.10 (maverick) only; i.e. when I try playing the same .ppt presentation on an Ubuntu 10.04 (Lucid) system, I don't have any problems.

It has been suggested that the problem lies with Ubuntu's packaging of OOo, and that the solution is to uninstall the default open office pages and re-install from the .debs on openoffice.org.  I will try this next.

---

