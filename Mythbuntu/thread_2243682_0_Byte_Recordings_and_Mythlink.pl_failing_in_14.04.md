---
title: "0 Byte Recordings and Mythlink.pl failing in 14.04"
date: 2014-09-10
forum: Mythbuntu
---

### Post by senator32 on 2014-09-10
I recently decided to move all my MythBuntu DVRs to 14.04 - instead of upgrading I did a fresh install to avoid issues (that was the plan anyway :) ). 

Since the move to 14.04, I am having two strange issues: 

1. Most of my recordings are not recording and are instead resulting in 0Byte recordings. I am checking my capture card setup now and trying ne w hardware to be sure, but was curious if others have ran into this. See attached picture:
[IMG]http://www.larrystendebach.com/wp-content/uploads/2014/09/MythRecordingError.png[/IMG]

2. Renaming the files via the MythLink.pl user job never works: mythlink.pl --link /mnt/pretty --chanid "%CHANID%" --starttime "%STARTTIME%"  --format '%T/%T%-%S'

I did not have either of these issues in 12.04 and could switch back, but I would prefer to be on 14.04.1 if possible. 

Any ideas on how to solve this / troubleshoot this? 

Thanks in advance.

---

### Post by senator32 on 2014-09-10
I think I am going to break down and reinstall 12.04. I will update the forum if this resolves it.

---

### Post by dannyboy79 on 2014-09-10
hmmm, check your myth logs, the backend log most of all. check for errors about possible write permission issues. also, have to mapped a capture card to a video source? i'm running Xubuntu 14.04 and MythTV 0.27.3+fixes along with a PVR-350 and a PVR-500 and it works great.

---

### Post by khPWXxF on 2014-09-11
I'll add:  Check the logs at recording start time AND proposed end time.  Some errors 'hang' and are not discovered until end of recording.
Phil

---

### Post by tgm4883 on 2014-09-11
Yep, this looks like a permissions issue, but I suppose it could also be a tuner issue.

---

### Post by senator32 on 2014-09-11
After some digging in the logs, I saw a lot of SignalStrength errors. I am thinking that it is either: 

1. an issue with the TV strength coming into the box (something I will test today with external testers)
2. A driver issue with the HVR2250 (I have seen several posts about these cards having signal / tuning issues). 

Oddly though, the switch back to 12.04 did fix the renaming process. Wonder what is up with Mythlink.pl ? 

If the HVR2250 tuners turn out to be the issue, do any of you all have suggestions for good QAM tuners? I am trying to get about 12 total tuners (3 dual tuners with 2x multiplex) in a single box. The HVR2250 was working, but seems to be a pain.  

Thanks for the feedback everyone!

-Larry

---

### Post by neutron68 on 2014-09-15
I have been using HD Homerun networked tuners from Silicon Dust with Mythbuntu for the last 4 years with good results.
I'm still using Mythbuntu 12.04, at present.

I have one of each of these models:
[http://www.amazon.com/SiliconDust-HDHomeRun-HDHR-US-Networked-Definition/dp/B0010Y414Q](http://www.amazon.com/SiliconDust-HDHomeRun-HDHR-US-Networked-Definition/dp/B0010Y414Q)
[http://www.amazon.com/SiliconDust-HDHomeRun-Definition-Digital-HDHR3-US/dp/B004HO58SO](http://www.amazon.com/SiliconDust-HDHomeRun-Definition-Digital-HDHR3-US/dp/B004HO58SO)

---

