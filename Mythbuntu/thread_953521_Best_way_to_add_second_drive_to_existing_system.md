---
title: "Best way to add second drive to existing system"
date: 2008-10-20
forum: Mythbuntu
---

### Post by seattlebuoy on 2008-10-20
I am running Mythbuntu 8.04.  I plan on adding a second 500MB drive to an existing singe 500MB drive system for additional media storage.  Primarily recordings.

Is there are preferred way to mounting the drive to a specific location or configuring Mythbuntu to use a second medial folder?  I want both drives to be available for storage.

I have searched the forums here and elsewhere and not found an obvious answer (at least to me).

Thanks for the input.

---

### Post by ilrudie on 2008-10-20
I just did this.  I added a temporary mount point in /media while I'm working with the drive (for the convenience of having the drive show up on my desktop).  Later I will probably end up putting the drive on a mount point like /export/media1 so it won't show on my desktop anymore.  Then I will sym link any folders I want back into my home directory.  

I also set it up to use lvm2 so I can grow and shrink my new media drive easily.  I'd recommend looking into lvm2.  If I had more drives I would have built a raid5 array using mdadm and then made a LVM2 logical volume on top of it for good data protection and flexibility.  Just some food for thought.  Hope that helps.

---

### Post by newlinux on 2008-10-20
LVM is unecessary if you are using mythtv .21. You can mount the drive anywhere you'd like and then setup a storage group to point to that mount point and it will increase your recording capacity. IF you want more capacity for mythvideo storage you can still mount it where you'd like and and then just add a second directory to your mythvideo storage setting (multiple directories are separated by a colon).

---

### Post by 4dognight on 2008-10-20
Myth is also smart enough to balance your recordings between the directories , so they fill up evenly(at least for tv recordings) . Just add the new directory using the myth backend setup menu. I created a mount of /var/lib/mythtv/storage. You could then create sub directories under it for recordings,videos etc, if you want to divide it up logically.

---

### Post by seattlebuoy on 2008-10-21
thanks for the advice.  Seemed like an obvious issue, but could not dig out the right solution.

---

### Post by Caps18 on 2008-10-21
Do you have to put something in the fstab file to get it to show up each time without user interaction?

I bought a 1TB drive just for movies, MythVideo, and backup files, but I haven't messed with getting it to show up automatically after restarting yet.

---

### Post by ilrudie on 2008-10-21
yes.  you must put a line in /etc/fstab

---

