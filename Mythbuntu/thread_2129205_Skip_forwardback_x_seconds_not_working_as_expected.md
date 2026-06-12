---
title: "Skip forward/back x seconds not working as expected"
date: 2013-03-25
forum: Mythbuntu
---

### Post by Calmor on 2013-03-25
I'm running 12.04LTS, 0.25+fixes MythTV.  My configuration is one frontend/backend combined machine, with a couple of separate frontend-only machines.  The backend has one tuner - a Motorola cable box connected via Firewire.  The Linux frontends are running a similar setup: 12.04LTS, 0.25+fixes, frontend only.  I also have a couple Macs running the OSX frontend version.  Each frontend has a playback group set up that the right arrow skips forward 30 seconds, and the left arrow skips backward 5 seconds.  Some frontends have remote controls, and each remote has the >>| and the right arrow both mapped to the right arrow key, same with |<< and the left arrow being mapped to the left arrow key.

On each of these frontends, including the combined frontend/backend, I have the same issue on a given recording.

Sometimes, but not always, skipping forward jumps to a specific time in the recording.  Skipping back jumps to another specific time in the recording.  In recordings that are affected, all frontends will jump to the same spots, leading me to think it's a problem with the recording itself.  For example, a recording of a hockey game the other night would jump to 00:09:51 on the first press of the skip forward time.  Skip backward jumped to about 00:01:20.  This could be repeated over and over, and they'd go to the exact same positions.

Sometimes, even within the same recording, the keys will work as expected, skipping 30 seconds and 5 seconds.

This occurs whether or not the recording is finished, and whether or not the recording has been comm flagged (or even marked for comm flagging).

It didn't always work this way, and I don't remember if it was an update that changed or it just happened.  I've scanned/cleaned all the tables (no errors found), and kept the updates current, to no avail.

Additionally, forward 3X seems to work normally, but forward 5X and more is actually slower than normal speed; trying to resume playback after a 3X, 5X, or more forwarding seems to crash the frontend almost always.  (I was trying to use this to compensate for the skipping issue)

One time (and one only) I had a program which was 3 hours long report on the OSD as 05:59:00 in total length.  It played through until about 3:20:00 or so and then dropped out... so I'm wondering, what calculates that time (and the 30-second skip times)... and if that's why the skpping isn't working normally?

I've tried to Google to no avail...

Thanks in advance!

---

### Post by Calmor on 2013-03-25
I should also note it's happened on at least three different channels, some recordings are 720, some are 1080i.

---

### Post by BicyclerBoy on 2013-03-27
To fix the duration error & the bad seeking can you try ?
mythcommflag --rebuild --file "your-recording-filename"

The recording filename does not need full path, just needs to be in a storage group somewhere..
Note: this is not a solution just a temp work-around.

MythTV needs correct seektable info to be able to calculate the jump points.
0.25 uses frame byte offset data & indicated frame rate to calculate jump-points.
0.26+fixes uses seektable frame time offset data.

0.26+fixes got time accurate seeking at being of this year but a bug caused slow seeking for me..This was resolved in last couple of days..

---

### Post by Calmor on 2013-04-01
BicyclerBoy - I can give it a try, but would this help files that are still being recorded, or that are recorded without the commercial flagging job set?  I'm having the problem in 0.25+fixes.

I might consider upgrading to 0.26+fixes if it solves the problem and the upgrade path isn't horrible... I'm down to one Mac frontend in normal use now, which is another concern (0.26 frontend build for OSX)

---

### Post by BicyclerBoy on 2013-04-16
You can run "mythcommflag --rebuild --blah" on a in-progress recording..it just slows down when it catches up..
You do not need any user commflag job enabled..
I mean for you to run that command in a terminal..myth searches for the file in the storage groups..

Please note mythcommflag with --rebuild does **NOT** do any commflagging..

There has been some OSX build fixes in master could be in 0.26+fixes..

Duration & AU/keyframe detection has been bit unstable for H264 AVC from the start..

---

