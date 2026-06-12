---
title: "How do I mount the contents of two hdd into /videos"
date: 2012-11-01
forum: Mythbuntu
---

### Post by blkbx on 2012-11-01
Hi 
I've recently added a 2gig hdd to my mythbuntu system. Now I find myself mounting both hdd into /var/lib/mythtv/videos/drive1, drive2. Can I do this another way so that I can show the contents of both drives(Thriller, SiFi, Drama etc) making it a little easier to navigate the contents of videos.
thanks

---

### Post by nickrout on 2012-11-01
> **blkbx said:**
> Hi 
I've recently added a 2gig hdd to my mythbuntu system. Now I find myself mounting both hdd into /var/lib/mythtv/videos/drive1, drive2. Can I do this another way so that I can show the contents of both drives(Thriller, SiFi, Drama etc) making it a little easier to navigate the contents of videos.
thanksmount the drive anywhere and then add the path to your videos storage group.

---

### Post by jerome1232 on 2012-11-01
You could combine them into a single LVM volume and mount the logical volume onto /videos

You would create a partition on each drive as a physical volume for LVM, create a single volume group which includes both partitions, then create a single volume in the volume group.

Here is some more info about LVM [https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)

---

### Post by nickrout on 2012-11-02
> **jerome1232 said:**
> You could combine them into a single LVM volume and mount the logical volume onto /videos

You would create a partition on each drive as a physical volume for LVM, create a single volume group which includes both partitions, then create a single volume in the volume group.

Here is some more info about LVM [https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)LVM is the wrong answer here. Lose one disk and you use the lot.

Storage Groups are the right answer under mythtv, and are designed specifically for this purpose.

---

### Post by AlecJ on 2012-11-02
Separate the paths with colons.


> **nickrout said:**
> LVM is the wrong answer here. Lose one disk and you use the lot.

Storage Groups are the right answer under mythtv, and are designed specifically for this purpose.

I have my video path set in the general video settings set to

/media/store1/Videos1/:/media/store3/Videos3/

to see both drives and folders in the Video list etc.

I have added the two paths into storage groups in the backend after reading this, but what do I need to set the General path set to?

would it be any different ?

---

### Post by nickrout on 2012-11-02
> **AlecJ said:**
> Separate the paths with colons.




I have my video path set in the general video settings set to

/media/store1/Videos1/:/media/store3/Videos3/

to see both drives and folders in the Video list etc.

I have added the two paths into storage groups in the backend after reading this, but what do I need to set the General path set to?

would it be any different ?Blank it out.

---

