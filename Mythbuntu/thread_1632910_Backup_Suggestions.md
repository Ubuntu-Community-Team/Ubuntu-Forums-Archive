---
title: "Backup Suggestions"
date: 2010-11-28
forum: Mythbuntu
---

### Post by uncle hammy on 2010-11-28
I just picked up a 2TB external drive for next to nothing this weekend.  I am going to use it to back up my MythTV recording directories (the only thing left in my systems not being backed up due to sheer size and lack of it being "critical"), which are currently 4 different physical drives using storage groups, with no redundancy.

So, I have...

/mythtv_1 (500GB drive)
/mythtv_2 (320GB drive)
/mythtv_3 (500GB drive)
/mythtv_4 (360GB drive)

I formatted the new drive with ext4 and have it being mounted at boot in fstab.  

Currently, I am using a very simple cron script that simply rsync's each mythtv_x directory to a backups folder on the external drive.  This works fine and now that the initial backup is out of the way, is relatively quick.  However, it also is a 1:1 backup, so I am using up a lot of space to store it.

Anyone have any suggestions other than this that will maintain the simplicity of this (very fast due to only working with changes) but perhaps incorporating some compression?  I am not interested in differential or incremental backups which will require multiple files to restore.

The only thing I have been able to think of would require unzipping the archive, rsync'ing, then re-zipping.  This obviously would take an incredible amount of time.

I am well aware of the benefits of moving to a RAID 5 setup for my recordings, however I am trying to work within the parameters of the hardware I already have.  RAID 5 would require purchasing at least 3 more drives (since none of my drives match) plus a decent RAID card.  As drives die and get the wife (the CFO) approval to be replaced, I will likely do so in a fashion that allows me to move to a RAID setup.

---

### Post by nickrout on 2010-11-28
> **uncle hammy said:**
> I just picked up a 2TB external drive for next to nothing this weekend.  I am going to use it to back up my MythTV recording directories (the only thing left in my systems not being backed up due to sheer size and lack of it being "critical"), which are currently 4 different physical drives using storage groups, with no redundancy.

So, I have...

/mythtv_1 (500GB drive)
/mythtv_2 (320GB drive)
/mythtv_3 (500GB drive)
/mythtv_4 (360GB drive)

I formatted the new drive with ext4 and have it being mounted at boot in fstab.  

Currently, I am using a very simple cron script that simply rsync's each mythtv_x directory to a backups folder on the external drive.  This works fine and now that the initial backup is out of the way, is relatively quick.  However, it also is a 1:1 backup, so I am using up a lot of space to store it.

Anyone have any suggestions other than this that will maintain the simplicity of this (very fast due to only working with changes) but perhaps incorporating some compression?  I am not interested in differential or incremental backups which will require multiple files to restore.

The only thing I have been able to think of would require unzipping the archive, rsync'ing, then re-zipping.  This obviously would take an incredible amount of time.

I am well aware of the benefits of moving to a RAID 5 setup for my recordings, however I am trying to work within the parameters of the hardware I already have.  RAID 5 would require purchasing at least 3 more drives (since none of my drives match) plus a decent RAID card.  As drives die and get the wife (the CFO) approval to be replaced, I will likely do so in a fashion that allows me to move to a RAID setup.

Frankly I think compressing it is largely a waste of time. The data is already compressed mpeg2 or h264, compressing it more will not give you much benefit at all.

---

### Post by uncle hammy on 2010-11-28
Good point.  I just ran a quick test on a 6GB recording file, and it was knocked down to 5.6GB and took a while.  Not worth the extra complexity, time and disk activity.

---

### Post by nickrout on 2010-11-28
if you really want to save space, transcoding mpeg2 to h264 would do the trick, but is very cpu intensive.

---

### Post by uncle hammy on 2010-11-29
Nah, I bought the drive specifically to do these backups and it was dirt cheap.  I was just getting greedy :).

---

