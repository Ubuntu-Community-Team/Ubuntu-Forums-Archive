---
title: "MythTV losing scheduled recordings"
date: 2016-02-08
forum: Mythbuntu
---

### Post by raidensix2 on 2016-02-08
Managed to get a Mythbuntu 14.04 set up working but I have run into a problem with the scheduled recordings disappearing.
MythWeb still shows the Recording Schedules but the shows are no longer listed in the Upcoming Recordings. Previously, Upcoming
Recordings would show a program to be recorded the next day or later in the week but then they would simply be gone. 
Anyone have any ideas?

---

### Post by bilkay on 2016-04-29
Having the same or similar problem. If you schedule a new program, does it show in "Upcoming Recordings"? Does it record?

Mythbuntu 14.04
Hauppauge HVR-2255 video card
3.16.0-hvr-test kernel

All my scheduled programs in "Upcoming  Recordings" have disappeared. If I schedule a new recording, I still  get the message "You haven't scheduled a program to record," and of  course it doesn't record.

Also "Watch TV" doesn't work at all - just black screen.

Ran optimize_mythdb.pl script. Also re-seated card. Also restored previous dump of mythconverg database. No change.

I should add that I have to manually schedule everything because I'm recording QAM off cable and Schedules Direct doesn't have the data for it.

I'm at a complete loss.

**UPDATE:  **My problem was self-induced by changing (and forgetting I'd changed it) the database IP address in the backend.

---

### Post by raidensix2 on 2016-05-02
I ended up using custom recordings with power search, for example

Search phrase: program.title like "Marvel%Agents of S.H.I.E.L.D." and program.chanid = 9999 AND program.previouslyshown = 0

9999 - channel in the Mysql DB
program.previouslyshown = 0 - for first showings only.

No problems so far.

---

