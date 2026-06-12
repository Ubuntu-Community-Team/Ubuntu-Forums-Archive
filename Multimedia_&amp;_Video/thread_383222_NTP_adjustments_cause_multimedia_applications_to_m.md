---
title: "NTP adjustments cause multimedia applications to momentarily pause"
date: 2007-03-13
forum: Multimedia &amp; Video
---

### Post by hl2040 on 2007-03-13
(I don't think this is strictly ubuntu specific. Please bear with me as I tell my story...)

I've known for a while that I have a fast system clock. Without NTP, I see the system clock get ahead of actual time, in terms of minutes per day. Now this clock drift is fine in principle - as I can utilize NTP over my residental internet connection to keep my system time correct. It's a tad annoying, but I can live with it. And the time does stay correct, but there's a bad side-effect.

When listening to music or watching videos (with Amarok or Kaffeine), occasionally my system would freeze, in that music would just stop, and then commence after a few seconds without any skipped audio or video. The clue it had something to do with the system time was when I changed my screen saver to an "analog" clock. I noticed that sometimes the screensaver would pause, and the seconds-hand would jump back a few seconds. This tipped me off, and caused me to kill NTP thus eliminating the pauses. But without NTP I can't keep my clock in sync.

So, every fifteen minutes or so, my system sets its clock back a few seconds, and timing-sensitive programs like audio applications or video hiccup as a result. Is there a way to make these NTP system time updates effect the system less - say adjusting the clock in small intervals more often? I suppose I could just have an hourly cron job to run ntpdate, but ntp is so sophisticated, I thought that there must be a way.

Any Ideas?

---

