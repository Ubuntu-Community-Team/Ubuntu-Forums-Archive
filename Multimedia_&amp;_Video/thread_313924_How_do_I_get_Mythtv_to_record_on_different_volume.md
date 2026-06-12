---
title: "How do I get Mythtv to record on different volume"
date: 2006-12-06
forum: Multimedia &amp; Video
---

### Post by Panhead Bill on 2006-12-06
I'm working on my Mythtv PVR.  I have an 80G drive for the system (dapper) Mythtv and it's add-ons.  Using lvm2 I set up a 480g storage area for my recorded video (4x120G drives).

The Video volume appears in the tree under File system. (file system > video)

Mythtv has been set to output the video to the store and buffer directories:     (file system > home > mythtv > mythtv > store > buffers)
(file system > home > mythtv > mythtv > store > recordings)

I can't move the video volume into store using the mv command, so how do I set up mythtv to store video onto the lvm volume?

---

### Post by superm1 on 2006-12-07
mythtv-setup

Will allow you to change where the recordings will be stored.

Stop the backend and then you can reconfigure as per the normal backend setup
```
https://help.ubuntu.com/community/MythTV_mythtvsetup
```

---

### Post by Panhead Bill on 2007-01-03
Found it.  Of course I had to finagle the permissions on the lvm to give Mythtv access, and then open several directories on the LVM.  Finally I had to modify permissions on a directory that Myth created, but now I'm recording and playing back to my monitor.

Output from the HPG - 350 card is the next hurdle.

---

### Post by majoridiot on 2007-01-03
> **Panhead Bill said:**
> Output from the HPG - 350 card is the next hurdle.

save yourself a LOT of trouble and follow one of these:

for dapper- [https://help.ubuntu.com/community/Install_IVTV_Dapper?highlight=%28IVTV%29](https://help.ubuntu.com/community/Install_IVTV_Dapper?highlight=%28IVTV%29)

for edgy- [https://help.ubuntu.com/community/Install_IVTV_Edgy?highlight=%28IVTV%29](https://help.ubuntu.com/community/Install_IVTV_Edgy?highlight=%28IVTV%29)

GREAT guides :D

---

### Post by Panhead Bill on 2007-01-03
Thanks for the links, this will make the process much more straightforward.

---

