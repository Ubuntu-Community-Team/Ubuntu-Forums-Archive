---
title: "Cannot update Storage Group directories, invalid path error"
date: 2015-12-31
forum: Mythbuntu
---

### Post by innocuous_name on 2015-12-31
I'm paraphrasing as it's not in front of me.  And I apologize if this ground has been trod before, I can't find it.  

I have an SSD boot disk, and a 3tb HDD I want to use for storage.  I formatted (ext4) and mounted the HDD, and created a directory there.  In all it's path is /media/HTPCstorage/recordings.   If I go into terminal I can cd /media/HTPCstorage/recordings no problem.

So I go into the mythtv setting to change the storage directories (because /var/lib is a silly place for recordings to go, though since it's guaranteed to exist, I can see why they'd use it) but I get an error (on exit) everytime! Paraphrasing, but it's one of two things:  I either get 'path doesn't exist' or it appends an extra / at the end and says /media/HTPCstorage/recordings//.test couldn't be saved.  I have tried every variant on the path name I can think of, with and without the appended or prepended /, even ../../ in case it was stuck in /var/lib/

Can anyone point me in the right direction?  I was working on this until very late last night and waited until I could sleep on it to post.  No nighttime epiphanies.  :(  TIA!

Edit:  Wondering if I screwed up permissions - what user/group does MythTV use?  Which permissions should it be allowed?

---

### Post by aelfric55 on 2015-12-31
If you just added and mounted the drive, it and its contents are  probably all set with owner and group "root:root". This is wrong. If there is a mythtv group in your installation, the storage should be set "mythtv:mythtv", permissions about 755. Some installations have no mythtv group and make mythtv a user. In this case "mythtv:users" ; permissions about 755.

---

### Post by innocuous_name on 2016-01-01
Thanks very much, it was permissions.
I found an old answer here as well.  [http://ubuntuforums.org/showthread.php?t=1410419](http://ubuntuforums.org/showthread.php?t=1410419)

---

