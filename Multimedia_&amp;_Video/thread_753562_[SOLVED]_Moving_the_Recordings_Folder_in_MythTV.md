---
title: "[SOLVED] Moving the Recordings Folder in MythTV"
date: 2008-04-12
forum: Multimedia &amp; Video
---

### Post by Weidbrewer on 2008-04-12
Is it possible to move where the recordings end up in MythTV?  I really don't have enough space on my main hard drive, but more than enough on my 500GB raid.  As of right now, I have all of my videos, pictures and music there, but haven't figured out how to the move the recordings there.

The problem right now is, I'm losing recordings when I record something new, and I think that's because of space.

---

### Post by tamoneya on 2008-04-12
just go into the myth back end configuration and go to option 6: Storage directories.

---

### Post by Weidbrewer on 2008-04-12
Wow...is it really that simple?


So, does it make sense that this is why I'm losing recordings (that myth doesn't like the amount of space I have left on that HD)?

---

### Post by tamoneya on 2008-04-12
makes perfect sense. You should be all set now.

---

### Post by Weidbrewer on 2008-04-12
Groovy, thanks.   I'll give it a try a little later tonight.



Also, to defuse any possible landmines before they happen, is there also a setting for how much drive it looks for?   For example, I'm going to move the fold to the massive RAID system, but I want to make sure that Myth doesn't think that it still has only X amount of space.

---

### Post by Weidbrewer on 2008-04-12
Well.....that didn't work.


I went in to option 6, and first I created a new storage group.   In this case, I named it Movies/TV and set the path to /media/raid/recordings

When I set something to record with that set as the storage option, it went a second or two and then stopped...and said that the file was not found.

So, I tried again, and this time changed the default path to the above from /var/lib/mythtv/recordings.


Same result.   Any suggestions, anyone?

---

### Post by warp99 on 2008-04-12
If your having trouble with moving the directory why don't you move the recordings from /var/lib/mythtv/recordings to the new location and just symlink the directory.

---

### Post by Weidbrewer on 2008-04-13
I actually had the same thought.   In the meantime, I realized I'm an idiot.  A "sudo chmod" on the raid, and everything worked right

Go figure....:oops

---

