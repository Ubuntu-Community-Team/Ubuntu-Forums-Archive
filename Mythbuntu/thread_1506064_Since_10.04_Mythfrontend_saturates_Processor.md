---
title: "Since 10.04 Mythfrontend saturates Processor"
date: 2010-06-09
forum: Mythbuntu
---

### Post by kulinskit on 2010-06-09
Ever since I upgraded to 10.04, mythfrontend sporadically saturates my cpu.  This was not a problem with the 8.xx Long Term Release I was using previously.  Using Myth 0.23 from SVN source and 10.04 now.  For days, this setup does fine playing hd tv using my 2.4 Ghz Athlon XP running the slim profile.  CPU utilization of mythfronend ranges from 65 to 75%.  Then, seemingly out of the blue, mythfrontend starts soaking up 95+% of the cpu playing back HD tv recordings, and this saturation continues long after I have exited out of playing the recorded TV show. Channel doesn't seem to matter.  The most recent occurrence of this event, followed a kernal segfault.  My videocard is a Nvidia GT 6600 so VDPAU is not an alternative for now....

Does anyone have advice which logs to review/post here to try and nail down the cause?  I am a relative newbie with linux (myth was my first introduction to it) but getting better at administering mythbuntu...

---

### Post by kulinskit on 2010-06-12
Last time this stuttery playing happened, I noticed references to MythNetvision updating some feeds in the fronend log.  I have turned off automatic updates for the MythNetvision sites and am hoping this will solve the problem I was having.  Posting for the benefit of others that may also be puzzled by stuttering video due to CPU overload.  Will update subject line in a week or so if this change solves the problem.

---

