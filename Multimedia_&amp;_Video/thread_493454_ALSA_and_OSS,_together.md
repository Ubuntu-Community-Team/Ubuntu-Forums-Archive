---
title: "ALSA and OSS, together?"
date: 2007-07-05
forum: Multimedia &amp; Video
---

### Post by Riel on 2007-07-05
I installed OSS and it worked perfect.
Now there's no sound in Firefox , as many of us have.

But is it possible to install BOTH OSS and ALSA drivers?



function snd_ctl_open failed for default: No such device
my usr/src/alsa is empty/

GNOME gives me the -pc-speaker- beeps, annying.
Welcome sound works, I believe. All sounds work as far as I  know?

---

### Post by Thies on 2007-07-25
HI there!

No solution o your question (sorry for that) but I've been thinking of ALSA vs OSS lately much as well. Maybe some sound experts find a minute to post an reply.
I'm running an M-Audio Delta 66 with an M-Audio Omni I/O, which gives me all I need for my home studio. M-Audio points to OSS drivers for their products in Linux, but Ubuntu (as most (all ?) linux distributions) have now the modern ALSA drivers there. For sure there is ALSA-OSS support for "old" programmes that still use OSS as I/O but well, that's not the "real" OSS - is it?

My experience so far is, that one has to chose either ALSA or OSS. But then how to test the one or the other and be able to reconfigure ALSA after OSS install? :confused:
OSS is now available under GNU Public License and comes with a DEB installer; but this "kills" your ALSA settings and still many programs want to use ALSA instead.

Anyone for some links to a decent ALSA / OSS side-by-side How-To ???

/Thies

---

