---
title: "[SOLVED] Feisty, nautilus and movie previews"
date: 2007-01-28
forum: Multimedia &amp; Video
---

### Post by siddartha on 2007-01-28
I installed on feisty all the codecs from mplayer, I even installed mplayer (with a weird error). I expected to see the thumbnails for the movies once I change the gstreamer backend to xine (ugly thing totem). But no. I checked the settings and gxine says is looking for the codecs not in the usual /usr/lib/win32 but in /usr/lib/codecs. Changed that... yet no change in reaction. I still get the same icon with all my movies. What could be done?

---

### Post by siddartha on 2007-01-28
My fault somehow - it said broken xine-lib on startup. I installed the other libxine* packages, deleted the thumbnails directory and now it works.

---

