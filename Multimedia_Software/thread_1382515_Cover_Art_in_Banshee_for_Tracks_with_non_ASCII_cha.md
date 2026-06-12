---
title: "Cover Art in Banshee for Tracks with non ASCII characters"
date: 2010-01-16
forum: Multimedia Software
---

### Post by wintercorn on 2010-01-16
Banshee (Version 1.5.2) doesn't seem to support cover art for tracks that include non ascii characters in any way. All manual methods that work with ascii tracks failed
(folder.jpg in album folder, copying appropriately named jpg in ~/.cache/album-art, embedding jpg in mp3 metadata). 

This is really quite a drawback for users who don't have an English-only music collection. Is there any workaround or bugfix that I missed or do I have to go back to Rhythmbox to have non-English cover art?

---

### Post by boombox1387 on 2010-01-21
Here's the [bug report]("https://bugzilla.gnome.org/show_bug.cgi?id=520516") that you want.  I don't know of any workarounds, but the bug is "high" priority and targeted for a fix in Banshee 1.6 (scheduled for release on March 31).  Right now you can find a working (I think?) patch at that bug report.  It's true that this is a pretty annoying issue.

---

