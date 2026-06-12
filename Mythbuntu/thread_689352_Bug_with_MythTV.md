---
title: "Bug with MythTV"
date: 2008-02-06
forum: Mythbuntu
---

### Post by Caps18 on 2008-02-06
Or did I install it wrong?

I have recorded a few shows and now the buffer (is it 4 hours?) will fill up the hard drive.  When this happens, MythTV crashes and won't start up again until I manually delete recordings from the command prompt.

So, the question is, is there some way to reduce the number of hours the buffer records on one channel?  In TiVo it was 30 minutes, which was too small.  1 or 2 hours would be right for me.

Is there some way to partition the hard drive so that the recordings can't fill up the entire hard drive?  The software would work still.

Why wasn't there a warning that I selected too many shows to record and it was going to run out of hard drive space?  This was just a test to see what happened, but I'm going away for a week, so I record a bunch of stuff.

I will be getting a very large hard drive one of these days, but I haven't yet and would like this to still work for recording stuff this week.

---

### Post by newlinux on 2008-02-06
What are you autoexpire settings (are you recordings set to allow to autoexpire)? As the the hard drive fills up myth should delete liveTV recordings and scheduled recordings to make room for other recordings, depending on your settings. 

You can also set myth to delete old shows to make room or not to record new shows when a certain episode limit is reached per show.  You do this per recording schedule.

As for the partitioning, It is pobably best to create a separate partition for your recordings. But you can also set it up so that it will always leave a certain amount of space on the drive open. I think this setting is in  the setup->Utilities/Setup->TV Settings->General section. You can also setup your default autoexpire settings here.

---

