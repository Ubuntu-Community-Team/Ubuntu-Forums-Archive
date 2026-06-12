---
title: "capture splits at 30 minutes, later parts not visible in Myth"
date: 2009-04-02
forum: Mythbuntu
---

### Post by mathog on 2009-04-02
When I capture from our camcorder through the SAA7130 device as channel 100 in mythtv, it saves the results into a NUV file.  So far so good.  However, whenever the capture extends past a half hour mark the current NUV is terminated and a new one started.  That is ok too, I guess.  Except that in "Watch Recordings" only the first part is visible.  For instance, the one I just recorded shows up there as

```
Unknown
100 C...    Thu Apr 2, 6:04 PM - 6:30 PM

```
and the last 8 minutes seem not to be available through Myth.  I can see them in /home/mythdbstorage, and play them with mplayer though.

Is this a bug in Mythtv, or do I have something configured incorrectly?

Thanks.

---

### Post by mathog on 2009-04-03
A further problem - the parts after the split are automatically deleted after a day.  Rats!

---

### Post by SiHa on 2009-04-04
I assume you are just selecting 'Record' when watching the camcorder output? To Myth you are simply watching Live TV, but without any EPG data. Without an EPG, it looks like Myth records in half-hour segments, so as not to just record a single huge file if it gets left on live TV for 48hrs (for example). 
So it records up until the next half-hour, and stores this as a recording. The rest is just stored as LiveTV, which Myth always records to disk then auto-expires (deletes) it after a day. 

You can change the number of days after which Myth will autoexpire:
Utilities/Setup > Setup > TV Settings > General > Page 2 > **LiveTV Max Age**
Utilities/Setup > Setup > TV Settings > Playback > Page 5 > **Display LiveTV in 'All Programs'**

This should allow you to view all the recording (in 1/2 hr chunks) and alter the length of time before they are deleted. You may be able to turn off autoexpire completely, but I'm not sure.

...but this doesn't really solve your problem

I think the only way to record a single file that won't be expired is to schedule a manual recording
**Schedule recordings > Manual Schedule**, then start the camcorder when Myth has started recording. When the tape ends, if you want to stop recording immediately, you can go into **'Upcoming Recordings'**. The manual schedule shouldbe displayed at the top (in green if you're using Blootube) as currently recording. If you select it, there is an option to stop recording, I think.

Hope this helps.

---

