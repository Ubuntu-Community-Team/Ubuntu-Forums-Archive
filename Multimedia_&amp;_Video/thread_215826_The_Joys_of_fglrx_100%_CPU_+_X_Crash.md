---
title: "The Joys of fglrx: 100% CPU + X Crash"
date: 2006-07-14
forum: Multimedia &amp; Video
---

### Post by montag451 on 2006-07-14
One more ATI driver bug. I've seen a couple references to it in the numerous posts already about fglrx, but I need to vent my frustration and, hopefully, find some fixes.

I'm running an Acer TravelMate 8200 laptop with an ATI Mobility Radeon x1600. Occasionally while running Ubuntu, I'll notice my Intel Core Duo's are churning away at around 60% a piece even though I'm not running anything except Epiphany or GEdit. So, ever curious at what my computer could be doing behind my back, I open the system monitor and notice that the process taking up the most time is, ironically, the gnome-system-monitor itself. But only 5%. Not long after this, X will lock up.

(If needed, I can post my xorg.conf and log info if anyone's curious, but I'm not at my computer currently.)

All descriptions of this problem I've read seem to point to fglrx as the culprit. I did a search and found a couple sources with an accurate description of the problem.

[Bug 102](http://ati.cchtml.com/show_bug.cgi?id=102) in the unofficial driver bugzilla describes my dilema pretty well but has little in the way of a fix. I'm not very experienced with Linux, so I can't do much testing, and my own searches have turned up zilch. Has anyone had any luck finding solid info on this?

---

