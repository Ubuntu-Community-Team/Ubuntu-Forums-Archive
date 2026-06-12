---
title: "Monitor changing -- Help needed"
date: 2007-01-05
forum: Multimedia &amp; Video
---

### Post by RjBanker18 on 2007-01-05
Hey all, I just got a brand new 20" widescreen monitor (use to have a 19" CRT).  The only problem is it has incorrect resolutions and refresh rates.  Would I have to put them in manually to the config file(xorg.conf right?) or is there a quick way of getting the resolutions to be right?  I use Beryl + latest video drivers, some of the refresh rates include 50 and 55 Hz ](*,) .

Thanks in advance!

---

### Post by Dekunuts on 2007-01-05
i think you have to edit the xorg.conf file, there you need to fill in the correct values for  horizsync and vertsync (should be in screen manual). Also fill in the resolutions you want under your default color depth.

---

