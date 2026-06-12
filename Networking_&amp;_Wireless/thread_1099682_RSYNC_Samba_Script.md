---
title: "RSYNC Samba Script"
date: 2009-03-18
forum: Networking &amp; Wireless
---

### Post by BassKozz on 2009-03-18
I am trying to rsync a XP Laptop to my Ubuntu box.
I'd rather not have to mount the XP machine as I only need to run this rsync once a week (the rest of the week the laptop isn't even on), I just use the laptop for work once a week.

My Ubuntu box has a RAID5 Array mounted at "/media/RAID-storage"

So here is my script:
```
#!/bin/sh
###
# 3/18/09
# XPtoUbuntuTransfer.sh
# Transfer Files from XP Laptop to Ubuntu Box
###

SOURCE="//XP-laptop/Soldiers\ and\ Sailors\ Cases/*"
DESTINATION="/media/RAID-storage/Work/Soldiers\ and\ Sailors\ Cases/"
LOG=/media/RAID-storage/Work/scripts/XPtoUbuntuTransfer.log

echo "Transfer Begin: $(date)" >> $LOG
rsync -av "$SOURCE" "$DESTINATION" >> $LOG
echo "Transfer End: $(date)" >> $LOG
echo "###########################" >> $LOG

```

I get the following errors:
```
rsync: change_dir "//XP-laptop/Soldiers\ and\ Sailors\ Cases" failed: No such file or directory (2)
rsync error: some files could not be transferred (code 23) at main.c(1058) [sender=3.0.3]

```
Obviously because //XP-laptop can't be accessed from shell because it's a samba share, so how can I access that share without mounting it and use it in the context of this script?
I searched for how to do this using smbclient, but I came up empty :(
Any/All help is greatly appreciated.
-BassKozz

---

