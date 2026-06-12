---
title: "monitor powered on?"
date: 2007-12-03
forum: Multimedia &amp; Video
---

### Post by spotspot on 2007-12-03
i am looking for a way to determine if the monitor is powered on.  i believe you can query the monitor (the EDID block) for the resolutions and timing it supports, for example the information reported by xrandr.  but it seems this program reports data that was queried and cached when the X server started.  is there any way to force a query?  in this case there's an dvi-to-hdmi to a plasma screen.  thanks, -spot

---

### Post by spotspot on 2007-12-04
I checked out [http://john.fremlin.de/programs/linux/read-edid/](http://john.fremlin.de/programs/linux/read-edid/) but it didn't work.  the author pointed me at "xset q" which does indeed report "Monitor is On".... but it does so even if it's off.  this seems like a bug in xset, no?

---

