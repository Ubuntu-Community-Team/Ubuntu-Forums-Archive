---
title: "Fast forwarding not working anymore"
date: 2009-04-14
forum: Mythbuntu
---

### Post by Caps18 on 2009-04-14
I'm not sure if I need to rebuild my database or if it is something else that is wrong, but I can no longer fast forward when watching recorded tv shows.  The commercial skipping is also having problems and not working.  And I have to wait until the TV show is fully recorded, since I can't play something while it is recording.

I tried the optimize table button on the control panel last night, so I'll see if that helps on new recordings tonight.

And I think this started happening after my recordings partition became full.  The log/system partition hasn't run out of space in 8 months.

Thanks (I had to type this quick, I may have missed something)

---

### Post by klc5555 on 2009-04-14
> **Caps18 said:**
> I'm not sure if I need to rebuild my database or if it is something else that is wrong, but I can no longer fast forward when watching recorded tv shows.  The commercial skipping is also having problems and not working.  And I have to wait until the TV show is fully recorded, since I can't play something while it is recording.

I tried the optimize table button on the control panel last night, so I'll see if that helps on new recordings tonight.

And I think this started happening after my recordings partition became full.  The log/system partition hasn't run out of space in 8 months.

Thanks (I had to type this quick, I may have missed something)

Pull up one of the affected recordings for viewing in myth, and hit the "e" key for "edit recording" (or do it from the on-screen menu). If the error message appears on screen "no seek table", then your partition problem crashed the seektable portion of your database. This can be fixed by running the database repair/optimize utilities in the Mythbuntu control center, or by running optimize_mythdb.pl from a prompt. Until this is fixed, database backups using mysqldump will not function.

Some individual recordings may come out of the repair still with no seektable or a messed-up seektable. If these recordings are analog, then mythcommflag --rebuild will handle the whole batch of them, one after the other.

Mythcommflag will not give you a usable seek table for a dvb recording. For this, you'll need to run mythtranscode --mpeg2 --buildindex -c [channel] -s [starttime] on each individual affected dvb recording. (It will also work on an analog recording) I find running the command on a single recording is sufficiently annoying that, since I seem to crash seektables fairly frequently, I set it up as a user job. So that when I encounter a recording with a crashed table, I can just drop the recording into the job queue from the frontend and eventually it gets fixed.

---

### Post by Caps18 on 2009-04-15
Thanks, I'll try that tonight.

But, I'm not too worried about fixing older shows, I would just like it to work for future shows actually.

And I have digital over-the-air recordings.  Some are HD, some are stardard def, but I only use the digital tuner card now.

---

