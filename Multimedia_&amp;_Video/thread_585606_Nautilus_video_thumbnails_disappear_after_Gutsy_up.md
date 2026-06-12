---
title: "Nautilus video thumbnails disappear after Gutsy upgrade?  Try this."
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by rokclimb15 on 2007-10-21
I just found that video thumbnails were not working anymore after my Feisty-Gutsy upgrade.  I found a solution.

[LIST=1]
[*]sudo apt-get remove totem-gstreamer
[*]sudo apt-get install totem-xine
[*]rm ~/.thumbnails/fail/*
[*]killall -9 nautilus
[/LIST]

For some reason the totem-gstreamer package just won't generate thumbnails for some AVIs.  Evidently totem-xine does a better job.

---

### Post by MetalMusicAddict on 2007-10-21
> **rokclimb15 said:**
> For some reason the totem-gstreamer package just won't generate thumbnails for some AVIs.  Evidently totem-xine does a better job.

Not really better, just different. For me, -gstreamer worked better than -xine. I do use them both to get all the thumbnails correct.

---

