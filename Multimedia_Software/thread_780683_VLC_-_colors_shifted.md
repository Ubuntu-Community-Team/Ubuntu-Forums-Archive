---
title: "VLC - colors shifted"
date: 2008-05-03
forum: Multimedia Software
---

### Post by violinmandan on 2008-05-03
I just fixed a sound problem with VLC (as described [here]("http://ubuntuforums.org/showthread.php?t=776755")), but now all of the colors are shifted.

As with the sound issue, video worked perfectly for a while, but then suddenly stopped working correctly.

This seems to be independent of the codec used (I tried XVID, AVC1, and DX50).

Did anyone else have the same problem?

---

### Post by hellgate on 2008-05-03
go preferences-video-output modules-advanced optionsradio button rightbottom corner-and try different video output modules.

---

### Post by violinmandan on 2008-05-03
I did as you suggested and found that X11 video output worked, but looked worse than the default.

I rebooted, and the colors were back to normal on the default output.

I don't know why rebooting solved it though...

---

