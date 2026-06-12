---
title: "totem/gstreamer buffer size"
date: 2007-06-12
forum: Multimedia &amp; Video
---

### Post by alexrait1 on 2007-06-12
Is it possible to increase somehow the buffer size of gstreamer?
I want it to cache much more stream than it does by default before playing.

---

### Post by alexrait1 on 2007-06-22
No one knows? In mplayer is quite easy... it is in the configuration file...
Is it a feature that is not supported yet?

---

### Post by bo2367 on 2007-06-22
I was having the same problem, that is, when I streamed movies from stage6 using the totem movie player, the player would keep buffering every few seconds.  That was very annoying.  I think I have found a solution.

Using firefox:
Edit -> Preferences -> Advanced
Increase the cache size.  I believe the default is 50 MB.  I increased mine to 5GB.

Maybe an  overkill, but now when I watch stage 6 divx movies, There is no interruption concerning buffering

Hope this helps.

---

### Post by jamis on 2007-07-07
It would really be helpful if there was a way to fix this problem.  Totem/gstreamer (and with vlc) doesn't buffer properly, at least at my connection speeds (max. download of ~140KB/s).  Is there an alternative to gstreamer that might work?

---

### Post by RomeReactor on 2007-07-07
Hi. Open a terminal (Applications->Accessories->Terminal) and enter:
```
gconf-editor
```
Once it opens, go to "apps->totem->network-buffer-threshold" and increase its value. Personally I've never done that, so I wouldn't know what value to suggest; I do recommend, however, that you take note of the default value (2), in case you eventually want to revert it.

---

### Post by jamis on 2007-07-08
> **RomeReactor said:**
> Hi. Open a terminal (Applications->Accessories->Terminal) and enter:
```
gconf-editor
```
Once it opens, go to "apps->totem->network-buffer-threshold" and increase its value. Personally I've never done that, so I wouldn't know what value to suggest; I do recommend, however, that you take note of the default value (2), in case you eventually want to revert it.

Thanks for the advise but I'm still having the same problem.  I noticed the same thing happens with vlc (pausing at exactly the same time).  It must be something other than the player (gstreamer?).  I just want to be able to stream higher quality (stage6 divx) video without this happening with my connection speed (~140KB/s).  Any other ideas?

---

