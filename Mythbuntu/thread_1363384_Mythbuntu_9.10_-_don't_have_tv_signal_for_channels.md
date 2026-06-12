---
title: "Mythbuntu 9.10 - don't have tv signal for channels higher than 13"
date: 2009-12-24
forum: Mythbuntu
---

### Post by Mathieu Provencher on 2009-12-24
Hi, I'm new to Mythbuntu but I've been using Mythtv for two years now. My previous setup was under Fedora Core 8 with Mythtv 0.22.

My frontend was giving me headaches so I decided to change my setup and try Mythbuntu because I wanted to avoid the trouble of recompiling everything. Mythbuntu setup was a breeze and I was running Mythtv in no time.

Mythbuntu 9.10
mythtv-common:
  Installed: 0.22.0+fixes22994-0ubuntu0+mythbuntu3
  Candidate: 0.22.0+fixes23003-0ubuntu0+mythbuntu3
  Version table:
     0.22.0+fixes23003-0ubuntu0+mythbuntu3 0
        500 [http://us.autobuilds.mythbuntu.org](http://us.autobuilds.mythbuntu.org) karmic/main Packages
 *** 0.22.0+fixes22994-0ubuntu0+mythbuntu3 0
        100 /var/lib/dpkg/status
     0.22.0+fixes22594-0ubuntu1 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages

Intel P4 1.8ghz
2 GB RAM
2x Hauppauge PVR-500
Cable signal from provider (Videotron, Montreal, Canada)

So I tried recording some showings and I noticed that some of the recordings were showing snow instead of the actual show. I assumed I configured one or many of my tuners incorrectly. So I went and checked it out, everything seemed normal. Watching live tv was working but then I noticed something: I can't get a signal on channels that are higher than channel 13. I went and tried plugging my coax cable on a tv to see if the signal was bas on those channels, but everything is fine.

So I decided I would delete all tuners on the backend and start over again, one tuner at a time. I added the first tuner, but when I was to the point where I could choose to scan the channels or use my SchedulesDirect account (which I do usually), I decided to scan the channels instead. And there is was, I can scan every channels up to channel I get a no lock on channel 12 (which is normal since there is nothing at channel 12 at the moment), but I can't get anything out of higher channels. On the terminal window I see messages looking like this:

2009-12-24 10:10:47.378 DTVParamHelper::toString() index out of bounds

Asking google about this message, I see it happened to other people (it was discussed in November 2009) I can't find a fix? Is this a known problem? What can I do? I really like Mythbuntu so far and I don't want to switch back to Fedora and compiling mythtv myself. What I find very strange is why channel 13? Why isn't it not working from channel 1?

---

### Post by benlyboy on 2010-05-15
hi there 

I ran into something like this when I was setting up my mythbox it ended up that I the tunners set to broadcast channels instead of cable.

---

