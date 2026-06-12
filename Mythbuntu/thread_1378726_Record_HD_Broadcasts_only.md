---
title: "Record HD Broadcasts only?"
date: 2010-01-11
forum: Mythbuntu
---

### Post by Digicrat on 2010-01-11
I"m assuming (hoping) there's an easy answer to this, but Google has failed me so far, though I thought I had this working at some point in the past.


Is there an option to set a scheduled recording to only match 'HD' broadcasts?  I know I can search for HD-only, but I can't seem to schedule using said option.  Certain shows are often shown in syndication on multiple networks, but most of the time I only want the HD versions - which the syndicated channels often are not.  

On a related note, I've also tried 'Exclude Generic' and "New Episodes Only" for certain series (ie:Boston Legal), however Myth is still insisting on recording every syndicated/repeat airing.  


Thanks,
- David

---

### Post by ZedThou on 2010-01-11
When I set up a recording schedule, I use the "Record at any time on channel XXXX" so that it only records the airings on a specific HD channel instead of all the SD offerings.

---

### Post by the_pod on 2010-01-12
Zed's answer will work. You can set it to record on a specific channel only.  For example, I have The Office recorded only on NBC (or whatever network is on) so I don't pick up old re-runs.

For my system, I get the networks in both SD and HD.  I've actually deleted the SD stations from the backend using MythWeb so that there is never a question of whether a network will be recorded at optimal performance.  This was really annoying me when NFL games were recorded on the wrong channels...

---

### Post by Digicrat on 2010-01-12
That solution doesn't work for me though (at least not for certain shows).  I have one QAM and one ATSC tuner, so if I choose to only record on channel XXX, it will tend to record it only on that channel AND tuner.  

I did use the "Record only on channel X" option a few times in the past, but I've been moving away from that since the last time I had to rescan channels and discovered that somehow it didn't recognize the new QAM channel as the same as the old one, and stopped recording that show. 

I've been disabling several of the pure SD-only channels, however there are a few SD-only channels I receive that also have some unique content on them, in addition to these annoying syndicated repeats I'm trying to block from recording.  

I also tend to be lazy in updating my TV listings, so I prefer not using the "any channel in this timeslot" option, as the networks tend to change timeslots more often than I look at an actual TV guide - and that's not even counting special schedule changes.  


The TV listings do include the HD flag, so I find it odd that there's no option to filter on that in the recording schedule - I was hoping I had just missed it.  Maybe I need to find the mythtv dev list / feature tracker and suggest it...

---

### Post by grenloch101056 on 2010-01-12
what about setting the tuners that have HD capability as a higher priority than SD ones?

---

### Post by Digicrat on 2010-01-17
It's an HDHomeRun - both tuners are HD-capable, it's just that certain stations don't always broadcast HD signals.  There are also certain shows that I do want recorded at any time, on any channel ... but only if that broadcast is in HD.  

The database clearly has the fields to support this ... the question is how to modify the recording schedules to add this criteria.  A simple checkbox to add to the appropriate query hdtv=1 would do the trick.  

```

mysql> select listingsource, chanid, originalairdate, starttime, hdtv from program where title LIKE "Boston Legal"; 

+---------------+--------+-----------------+---------------------+------+
| listingsource | chanid | originalairdate | starttime           | hdtv |
+---------------+--------+-----------------+---------------------+------+
|             2 |   2022 | 2007-10-02      | 2010-01-24 00:30:00 |    0 | 
|             2 |   1071 | 2007-10-02      | 2010-01-24 01:35:00 |    1 | 
|             2 |   2665 | 2007-10-02      | 2010-01-24 00:30:00 |    1 | 
|             2 |   2022 | 2005-12-06      | 2010-01-25 00:50:00 |    0 | 
|             2 |   2665 | 2005-12-06      | 2010-01-25 00:50:00 |    1 | 
|             3 |   2022 | 2007-05-29      | 2010-01-10 00:30:00 |    0 | 
|             3 |   2665 | 2007-05-29      | 2010-01-10 00:30:00 |    1 | 
|             2 |   1071 | 2007-05-29      | 2010-01-10 01:35:00 |    1 | 
|             3 |   2022 | 2005-11-08      | 2010-01-11 00:50:00 |    0 | 
|             3 |   2665 | 2005-11-08      | 2010-01-11 00:50:00 |    1 | 
|             3 |   2022 | 2007-09-25      | 2010-01-17 00:30:00 |    0 | 
|             3 |   2665 | 2007-09-25      | 2010-01-17 00:30:00 |    1 | 
|             2 |   1071 | 2007-09-25      | 2010-01-17 01:35:00 |    1 | 
|             3 |   2022 | 2005-11-15      | 2010-01-18 00:50:00 |    0 | 
|             3 |   2665 | 2005-11-15      | 2010-01-18 00:50:00 |    1 | 
+---------------+--------+-----------------+---------------------+------+
15 rows in set (0.00 sec)


```

---

### Post by xinix on 2010-01-18
> **grenloch101056 said:**
> what about setting the tuners that have HD capability as a higher priority than SD ones?

This is what I do.  it has worked well for me and I like that it can fall back to an analog recording if it needs to.

---

