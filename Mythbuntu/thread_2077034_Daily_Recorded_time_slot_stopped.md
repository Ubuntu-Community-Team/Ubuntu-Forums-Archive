---
title: "Daily Recorded time slot stopped"
date: 2012-10-27
forum: Mythbuntu
---

### Post by k7_madman on 2012-10-27
Hello,

I set my mythbuntu to manually record a time slot daily.  This worked for about 2 weeks.  Then it stopped altogether.  At first I thought it was because of size but the recordings are set to auto expire plus I am nowhere near to a full drive 1.8 TB (1.6 TB free).

I noticed if I go back into Recording Schedules and re-save the manually record a daily time slot, it will record again but only show upcoming recordings for about 2 weeks. (IE I just set it before posting this and shows upcoming recordings until Thu Nov 8, 2012)

How do I set it to continuously record this time slot without stopping or going back to reactive?

---

### Post by dannyboy79 on 2012-10-29
theres only 2 weeks of EPG data is my guess why it only shows 2 weeks of upcoming recordings. I haven't done a manual tv schedule in a long time but are you sure you aren't missing a check box or something that tells it to always record this time slot every day.

---

### Post by nickrout on 2012-10-29
> **k7_madman said:**
> Hello,

I set my mythbuntu to manually record a time slot daily.  This worked for about 2 weeks.  Then it stopped altogether.  At first I thought it was because of size but the recordings are set to auto expire plus I am nowhere near to a full drive 1.8 TB (1.6 TB free).

I noticed if I go back into Recording Schedules and re-save the manually record a daily time slot, it will record again but only show upcoming recordings for about 2 weeks. (IE I just set it before posting this and shows upcoming recordings until Thu Nov 8, 2012)

How do I set it to continuously record this time slot without stopping or going back to reactive?What EXACTLY is your recording rule?

---

### Post by k7_madman on 2012-10-29
I have my digital cable box going into PVR-150.  My cable box tunes to the correct channel and outputs on channel 3.  I have my recording set to channel 3 everyday in the same time period. One thing dannyboy79 did say.  There is no EPG data...I have it set to record the same show so I don't have any real need for EPG...is it required to do a daily recording past 2 weeks?  Is there a way to have it keep going?

---

### Post by nickrout on 2012-10-30
> **k7_madman said:**
> I have my digital cable box going into PVR-150.  My cable box tunes to the correct channel and outputs on channel 3.  I have my recording set to channel 3 everyday in the same time period. One thing dannyboy79 did say.  There is no EPG data...I have it set to record the same show so I don't have any real need for EPG...is it required to do a daily recording past 2 weeks?  Is there a way to have it keep going?What EXACTLY is your recording rule.

Why do you have no EPG?

How does mythtv change the channel on the cable box?

---

### Post by k7_madman on 2012-10-30
I only record 1 show...the PBS new hour (kind of like npr for tv).  I could actually watch the show online but the most recent shows are not on and I don't like the commercials.

Anyway the show is on the same time everyday.  My cable box has a EPG, I can set it to tune to a certain channel at certain time (I guess this is for a old school vcr).  So everyday the cable box is set to tune into correct channel/time.

I did have a schedule direct account at one time...but I didn't see the need to renew since I would be recording this one show.

Recording rule
Record this program in this timeslot every day.
Recording Profile: Default
Transcoder:Autodetect
Recording Group: Default
Storage Group: Default
Playback Group: Default
Recording Priority: 0
Duplicate Check method:None
Check for duplicates in:All recordings
Auto-expire recordings: (check)

---

### Post by dannyboy79 on 2012-10-30
> **k7_madman said:**
> I only record 1 show...the PBS new hour (kind of like npr for tv).  I could actually watch the show online but the most recent shows are not on and I don't like the commercials.

Anyway the show is on the same time everyday.  My cable box has a EPG, I can set it to tune to a certain channel at certain time (I guess this is for a old school vcr).  So everyday the cable box is set to tune into correct channel/time.

I did have a schedule direct account at one time...but I didn't see the need to renew since I would be recording this one show.

Recording rule
Record this program in this timeslot every day.
Recording Profile: Default
Transcoder:Autodetect
Recording Group: Default
Storage Group: Default
Playback Group: Default
Recording Priority: 0
Duplicate Check method:None
Check for duplicates in:All recordings
Auto-expire recordings: (check)
that all looks good, and how long does it make it before this recording schedule is removed?

---

### Post by nickrout on 2012-10-30
> **k7_madman said:**
> I only record 1 show...the PBS new hour (kind of like npr for tv).  I could actually watch the show online but the most recent shows are not on and I don't like the commercials.

Anyway the show is on the same time everyday.  My cable box has a EPG, I can set it to tune to a certain channel at certain time (I guess this is for a old school vcr).  So everyday the cable box is set to tune into correct channel/time.

I did have a schedule direct account at one time...but I didn't see the need to renew since I would be recording this one show.

Recording rule
Record this program in this timeslot every day.
Recording Profile: Default
Transcoder:Autodetect
Recording Group: Default
Storage Group: Default
Playback Group: Default
Recording Priority: 0
Duplicate Check method:None
Check for duplicates in:All recordings
Auto-expire recordings: (check)OK I see, I think you need a manual rule, rather than a custom rule. You r rule relies on finding that programme in that timeslot every day. If the EPG is not there it fails.

You can do a manual rule under mythweb, and I am sure the frontend will program one too, but I don't have a frontend near at present.

---

### Post by dannyboy79 on 2012-10-30
that is a manual recording, NOT a custom recording. custom recording uses search terms etc.

---

### Post by k7_madman on 2012-10-31
Yea I tried to do a custom record but there is no place for me to select channel or time.  With no EPG there is nothing to search for.

---

### Post by k7_madman on 2012-11-13
Is there a script I can run to add the recording time slot back each 2 weeks?

---

### Post by dannyboy79 on 2012-11-14
you could but it would involve manual manipulation of the mysqldatabase and tables. I have no idea about any of that sorry. I still am not sure why its losing the recording schedule though. Doesn't make sense. I have recording schedules for a show like The Walking Dead that I set up for season 1 and finally when season 2 came around since it was on the same channel and on same time, it started up recordings the series again for season 2. I would think a manual recording schedule would act any different.
You may want to take your question to the mythtv-users IRC channel and ask them there. (it's on freenode I believe)

Good luck and sorry I couldn't help more

---

### Post by k7_madman on 2012-12-16
Is there a script I can run to have it re add the recordings?

---

### Post by nickrout on 2012-12-16
> **k7_madman said:**
> Is there a script I can run to have it re add the recordings?
please give us the output of the following sql statement:

```
select * from record;
```

---

