---
title: "Rhythmbox: repeat one button lost after last.fm button extend. enabled"
date: 2012-08-10
forum: Multimedia Software
---

### Post by EAZ on 2012-08-10
I have downloaded for rhythmbox, 2 of my favorite extentions:

[LIST]
[*]Repeat One Song (ROS)
[*]LastFM Extension (LFME)
[/LIST]

But since i enabled the LastFM Extension, the Repeat One Song button seems to be vanished of the screen.

Even after the LFME being disabled is doesn't get shown anymore.

I also closed rhythmbox completely and restarted it, with ROS enabled and ROS disabled & re-enabled (both with LFME disabled) but none of this has an effect on showing up.

can somebody please help?

---

### Post by EAZ on 2012-08-10
I got it solved!!

I copied the extension

/usr/share/lib/rhythmbox/plugins/
 to
 /usr/lib/rhythmbox/plugins/

and now it works, system-wide!

---

