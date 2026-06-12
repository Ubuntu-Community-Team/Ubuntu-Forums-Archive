---
title: "Recording lost: recorded, commflagged, expired in one fell swoop"
date: 2011-11-12
forum: Mythbuntu
---

### Post by keepitsimpleengr on 2011-11-12
So I recorded two programs while watch a prior recording, something I often do.  Then I watched one, deleted it, and started to watch the second&#8943;but it was gone.  It was listed on the previously recorded screen, but was not in the watch recording window, nor listed on the web interface.

From the mythbackend log (grep Grimm, the name of the recorded show)
```
···@···:···# cat extract-mythbackend.log | grep Grim
2011-11-11 21:00:01.140 Started recording: Grimm:Beeware: channel 1031 on cardid 3, sourceid 1
2011-11-11 21:00:01.203 scheduler: Started recording: Grimm:Beeware: channel 1031 on cardid 3, sourceid 1
2011-11-11 21:00:01.918 Updating status for Grimm:Beeware on cardid 3 (Tuning => Recording)
2011-11-11 21:00:29.161 JobQueue: Commercial Detection Starting for Grimm:Beeware recorded from channel 1031 at 2011-11-11T21:00:00
2011-11-11 21:00:29.229 commflag: Commercial Detection Starting: Grimm:Beeware recorded from channel 1031 at 2011-11-11T21:00:00
2011-11-11 22:00:01.133 Updating status for Grimm:Beeware on cardid 3 (Recording => Recorded)
2011-11-11 22:00:01.134 Finished recording Grimm "Beeware": channel 1031
2011-11-11 22:00:02.751 scheduler: Finished recording: Grimm "Beeware": channel 1031
2011-11-11 22:00:03.635 Finished recording Grimm "Beeware": channel 1031
2011-11-11 22:00:04.039 scheduler: Finished recording: Grimm "Beeware": channel 1031
2011-11-11 22:00:12.508 commflag: Commercial Detection Finished: Grimm:Beeware recorded from channel 1031 at 2011-11-11T21:00:00 (6 commercial break(s))
2011-11-11 22:01:11.997 Expiring 5836 MB for 1031 at 2011-11-11T21:00:00 => Grimm:Beeware
2011-11-11 22:01:12.030 autoexpire: Expiring Program: Expiring 5836 MB for 1031 at 2011-11-11T21:00:00 => Grimm:Beeware
```
I checked the rule and there was nothing untoward there, and auto-expire was enabled.

I am at a loss (so to speak).  Does this happen occasionally?  Is it a bug?  Am I a victim of the fat finger effect? :confused:

The entire extract is attached…

---

