---
title: "Basic filesystem question"
date: 2008-12-03
forum: Mythbuntu
---

### Post by Caps18 on 2008-12-03
I got around to adding a second hard drive to my system and it seems to be working now.  I have a simple question though.  It is currently mounted as /videos, but MythTV looks for videos in the /var/lib/mythtv/videos directory.  Could I copy all of the files from the current /var/lib/mythtv/videos directory onto the new hard drive and then use fstab to mount it in the /var/lib/mythtv/videos location?

Right now sda2 (700GB) is mounted at /var/lib.  It would be sdb1 (850GB) that I would like to mount at /var/lib/mythtv/videos  

I would hope that this would work, but I really don't want to accidently cause problems doing something wrong.

Thanks.

---

### Post by Archmage on 2008-12-03
Yes, you could do this, or you simply change the video-settings from var/lib/mythtv/videos to /videos.

---

### Post by newlinux on 2008-12-03
or since you currently have videos in both /var/lib/mythtv/videos and /videos you could just put them both in your video location in mythtv (separate them with a colon) and myth will look in both places.

---

### Post by timcredible on 2008-12-03
or you could move your files to the new drive like you said, then make the /var/lib/mythtv/videos directory point to your new drive 
```

mv /var/lib/mythtv/videos/* /videos
rmdir /var/lib/mythtv/videos
ln -s /videos /var/lib/mythtv/videos

```

---

