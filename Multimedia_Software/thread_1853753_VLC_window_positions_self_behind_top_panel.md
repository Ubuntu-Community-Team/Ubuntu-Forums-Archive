---
title: "VLC window positions self behind top panel"
date: 2011-10-02
forum: Multimedia Software
---

### Post by foogoo on 2011-10-02
I've searched both here and Google and am surprised to not see this already posted. Running Ubuntu 11.04 and VLC 1.1.9.

If I'm using VLC to play a video in fullscreen mode and let the video end, VLC will reposition itself in the top left corner of my desktop with it's title bar under the Ubuntu panel. That way, I can't close the VLC window unless I right-click on the bottom bar. This doesn't happen if I'm not in fullscreen mode, the VLC window will stay below the panel.

Any idea how to fix this? It did not happen with 10.10. Thanks.

---

### Post by wolfen69 on 2011-10-03
If you don't care about losing vlc's settings, try deleting the vlc config file (or rename it) and try it again.

---

### Post by foogoo on 2011-10-03
> **wolfen69 said:**
> If you don't care about losing vlc's settings, try deleting the vlc config file (or rename it) and try it again.

I ran "vlc --reset-config" and that worked! Thank you!

---

