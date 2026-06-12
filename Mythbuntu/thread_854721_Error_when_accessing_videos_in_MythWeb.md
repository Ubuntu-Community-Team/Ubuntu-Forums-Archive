---
title: "Error when accessing videos in MythWeb"
date: 2008-07-09
forum: Mythbuntu
---

### Post by lingenfr on 2008-07-09
When I click on the Videos icon in MythWeb, I get a webpage with the follow:

Error

Could not create a symlink to /var/lib/mythtv/videos, the local MythVideo directory for this hostname (MYTHTV-BACKEND). Please create a symlink to your MythVideo directory at data/video in order to use the video portions of MythWeb.


Has anyone else seen this? I don't have any database errors and this has worked previously.

---

### Post by maxim99 on 2008-07-09
I received this message too. I'm unsure as to how to fix it. The error message kinda says what the problem is but not really. Maybe i'm just reading it wrong.

---

### Post by Lindsay.Mathieson on 2008-07-10
You need to create two symbolic symlinks in the /var/www/mythweb/data directory.

off the top of my head:
```


cd /var/www/mythweb

sudo ln -s /var/lib/mythtv/videos video 
sudo ln -s /var/lib/mythtv/videos video_covers 


```

assuming "/var/lib/mythtv/videos" is where your video dir is

---

### Post by jmail524 on 2008-07-10
I had the same problem and I used Lindsay.Mathieson's advice from the previous post.  However, I needed to remove 2 files called "video" and "video_covers" already in my /var/www/mythweb/data, then I setup the new symbolic links.  Now everything seems to be working. (Be advised that I am new to MythTV and Linux in general.)

```

cd /var/www/mythweb/data

sudo rm video
sudo rm video_covers

sudo ln -s /var/lib/mythtv/videos video 
sudo ln -s /var/lib/mythtv/videos video_covers

```

Hope this helps.

Thanks.
Brian

---

### Post by mark467 on 2008-07-26
That worked for me but my covers were in a different location
I used this where (username) is my local username on system
sudo ln -s /home/(username)/.mythtv/MythVideo video_covers

---

### Post by lingenfr on 2008-09-14
The combination of the previous two posts worked for me as well. Thanks.

---

