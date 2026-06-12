---
title: "MythArchive Audio Sync Issues"
date: 2007-10-22
forum: Mythbuntu
---

### Post by dmfrey on 2007-10-22
I have been trying to use MythArchive to produce a DVD of the recordings I have.  The audio on the recording plays fine, however, when the resulting DVD is played, it is out of sync by about 5 seconds.  I have tried producing the same DVD with adjusting the MythArchive settings, but the same audio sync issue is the result.

I was able to do this without issue prior to installing the updates for the RC.

The recording was produced by recording HDTV over Firewire.

Has anyone else had any audio sync issues with MythArchive?  Have you been able to solve the issue?

Thanks.

---

### Post by dmfrey on 2007-10-25
I noticed in the logs that it was adding a duplicate audio adjustment.  I would see it saying adding audio sync offset of 450 ms twice.  In mythburn.py, I remove the --fix_sync (saw this on some other posts), but it still seems to be off slightly.

Does anyone have any other options to try?

---

### Post by Dewey_Oxberger on 2008-03-01
I have this problem - mythbuntu 7.1 (early 2008 ).
Anyone have mytharchive transcoding hdtv to a dvd and still have the audio work?  I'm stumped on this one.

---

