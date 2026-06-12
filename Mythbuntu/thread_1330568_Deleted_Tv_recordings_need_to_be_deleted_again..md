---
title: "Deleted Tv recordings need to be deleted again."
date: 2009-11-18
forum: Mythbuntu
---

### Post by williammanda on 2009-11-18
I was looking at my hardrive and saw that I had only 20 GB left on a 1 TB drive. I reviewed my tv recordings via mythtv (since this is the only media I have on this drive) and by my calculation, I could have maybe 500 GB of recordings. I then used the Disk Usage Analyzer and found out that over 900 GB was being used by the recordings directory. The last thing I looked at was System Status > Auto expire and found that all of the recordings that were deleted and not deleted were listed. I selected all the previously deleted recordings and deleted them. My recordings directory reflected the reduction. Now comes the first question. What has changed between ver .21 and .22 concerning permanently deleting recordings when you delete them after viewing? The only place I can see to possibly address this issue is Setup > General > Basic > Autoexpire. I accepted the default settings, which you can see in the attachment, but I'm not sure what to change if anything. If this is the wrong area to address the issue where should I make the change?
Thanks

---

### Post by tgm4883 on 2009-11-18
> **williammanda said:**
> I was looking at my hardrive and saw that I had only 20 GB left on a 1 TB drive. I reviewed my tv recordings via mythtv (since this is the only media I have on this drive) and by my calculation, I could have maybe 500 GB of recordings. I then used the Disk Usage Analyzer and found out that over 900 GB was being used by the recordings directory. The last thing I looked at was System Status > Auto expire and found that all of the recordings that were deleted and not deleted were listed. I selected all the previously deleted recordings and deleted them. My recordings directory reflected the reduction. Now comes the first question. What has changed between ver .21 and .22 concerning permanently deleting recordings when you delete them after viewing? The only place I can see to possibly address this issue is Setup > General > Basic > Autoexpire. I accepted the default settings, which you can see in the attachment, but I'm not sure what to change if anything. If this is the wrong area to address the issue where should I make the change?
Thanks

See where it says "Auto Expire instead of Delete Recording", this means that when you select delete on a recording, it actually moves it to the deleted recordings group, and doesn't actually delete it until it needs the space.

---

### Post by williammanda on 2009-11-18
OK ty for the help.

---

