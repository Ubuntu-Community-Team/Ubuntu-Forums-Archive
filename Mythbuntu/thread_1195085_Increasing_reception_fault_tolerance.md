---
title: "Increasing reception fault tolerance?"
date: 2009-06-23
forum: Mythbuntu
---

### Post by mathog on 2009-06-23
Some of the stations we watch are a bit iffy, reception wise, and from time to time the signal falls below some quality level that either MythTV, or possibly the HDHomeRun tuner, demands.  This manifests in one of two ways:

1.  When changing to that channel, the "you should have had a lock by now... OK" screen comes up.  If we do NOT click OK, but just wait instead, it eventually tunes in.  I suspect, but have not yet observed, that if this happens at the beginning of a scheduled recording, that recording will abort.

2.  When recording on that channel, if a particularly bad patch is encountered, the recording terminates.

Is there some way to override the relevant defaults?  Is it maybe the same timeout value?  Wwe would much rather have a 2 hour recording with a few holes in it than the first 23 minutes and then nothing.  Similarly, we don't want to skip the entire recording if the station happens to be very poorly received just at the beginning. 

Note, the stations in question are quite watchable most of the time, with just the occasional blocky pixelation type of low signal artifacts.

Thanks.

---

### Post by uncle hammy on 2009-06-24
You can change the timeout value.  Go to your backend setup and I believe it's under the tuner itself.  Set it for each tuner of your HDHomeRun unit.  I believe the default value is 3000, I have mine set to 10000 due to a station that used to be iffy.  There are 2 "timeout" values, increase the bottom one.

---

### Post by mathog on 2009-06-25
> **uncle hammy said:**
> You can change the timeout value.  Go to your backend setup and I believe it's under the tuner itself.  Set it for each tuner of your HDHomeRun unit.  I believe the default value is 3000, I have mine set to 10000 due to a station that used to be iffy.  There are 2 "timeout" values, increase the bottom one.

I changed both timeout values for both tuners to 10000 (10 seconds) and rescanned.  It picked up one additional station.  So far this has been working much better than before.

Thanks!

---

