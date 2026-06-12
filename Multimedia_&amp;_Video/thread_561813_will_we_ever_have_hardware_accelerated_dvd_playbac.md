---
title: "will we ever have hardware accelerated dvd playback?"
date: 2007-09-28
forum: Multimedia &amp; Video
---

### Post by syxbit on 2007-09-28
DVD's look better in windows and powerDVD with my nVidia card, as it's hardware accelerated.
i'm assuming it's just donw by the CPU in linux.
will this ever change?

---

### Post by shirilover on 2007-09-28
Sure, with MPlayer you can use -vo xvmc; with xine it's xxmc.
This only works for MPEG-2, but that's what DVD-Video is.

---

### Post by syxbit on 2007-09-28
i use VLC
is it possible with this?

---

### Post by shirilover on 2007-09-28
After looking through the mailing list for vlc and vlc-devel, it appears that xvmc support is currently broken. So, it does not appear possible at this time.

---

