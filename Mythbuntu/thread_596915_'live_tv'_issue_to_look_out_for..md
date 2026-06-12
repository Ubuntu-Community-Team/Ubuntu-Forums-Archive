---
title: "'live tv' issue to look out for."
date: 2007-10-30
forum: Mythbuntu
---

### Post by rusty0101 on 2007-10-30
I just freed up nearly a terrabyte of storage, and currently have no recorded shows on my back end. Kind of miffed because there were several shows that I was hoping to spend some time watching over the next couple of days, but now I'll have the opportunity to watch those of them that I record and re-record.

LiveTV was 'watching' a HDTV channel. That was somewhat odd as far as I can tell, because none of the front ends were currently tuned to watch LiveTV. But that didn't stop the back end from hanging in there and recording the channel. 6.1 gigabytes per hour. That turns into about 150 gig per day. Or a little over a TByte a week. And watching 'Live TV' takes priority over any recorded TV show that doesn't have the "Don't ever over write" flag set. (Ok, requirement being that the file involved is in the /var/lib/mythtv/recordings folder)

Would like to recommend that the LiveTV thread automatically break recordings into shows at scheduled show time changes. i.e. if show A runs from 9:00 to 11:00, then show B starts, the LiveTV thread should break the recording at that event.

Actually I think that LiveTV threads should auto-expire after 24 hours. If you want to record a Muscular dystrophy marathon, that should be a recording, not live TV. Granted you should be able to watch it in nearly real time, but that's a different issue.

As it is I'm planning on setting up a scheduled event to restart the backend process Monday, Wednesday and Friday at 4:00 am. (Nothing I watch is on at those times, and any movies I might record at those times can stand the interruption I think.)

---

### Post by dwarrenku on 2007-11-02
I'm no genius, and I've only been using MythTV for < 2 months, but this happened to me when I hit the R button and began recording to test something without telling it to stop.  I filled up my measily 80G hdd in a day.

Either way, sorry that it upset you.

---

