---
title: "USB drives are recoverable?"
date: 2008-07-05
forum: Multimedia Software
---

### Post by arashiko28 on 2008-07-05
So... some idiot pulled out my USB memory before I could end my work. Now it says that is writing protected on windows and doesn't allow me to format it. On Ubuntu I can't mount it. I tried to boot on DSL and install it on the drive but it denies permissions to do that. On DSL, it does recognizes it and I can see the files inside with ls on terminal, but can't delete them no add anything.

Is this in someway recoverable or it's just trash?:(

---

### Post by damis648 on 2008-07-05
If you do not mind losing data on it, install gparted with
```
sudo apt-get install gparted
```
and then run it via System>Administration>Partition Editor. Select your Flash Drive in the upper-right-hand corner. Delete all the partitions and then create a new FAT32 partition and apply.

---

### Post by falcon61102 on 2008-07-05
Were you using the drive in Windows when it got pulled out?

If so, re-insert it into a windows machine and use the safely remove hardware ap and you should be good.

---

### Post by damis648 on 2008-07-05
> **falcon61102 said:**
> Were you using the drive in Windows when it got pulled out?

If so, re-insert it into a windows machine and use the safely remove hardware ap and you should be good.

Yes, but he has no access to it. Ubuntu also has this feature. Just right-click the drive and click "Unmount".

---

### Post by falcon61102 on 2008-07-05
Check out this thread... may be able to help you

[http://ubuntuforums.org/showthread.php?t=848424](http://ubuntuforums.org/showthread.php?t=848424)

---

### Post by arashiko28 on 2008-07-05
The drive doesn't mount, so gparted won't recognize it, even though i did it and it doesn't only my HDD.

---

### Post by falcon61102 on 2008-07-05
> **damis648 said:**
> Yes, but he has no access to it. Ubuntu also has this feature. Just right-click the drive and click "Unmount".

What do you mean he has no access to it?  It being the windows box?

---

### Post by damis648 on 2008-07-05
> **arashiko28 said:**
> The drive doesn't mount, so gparted won't recognize it, even though i did it and it doesn't only my HDD.

gParted finds all drives, and will not perform any operations unless the drive is unmounted. The drive MUST be unmounted... you did try it?

---

### Post by arashiko28 on 2008-07-05
> **falcon61102 said:**
> Check out this thread... may be able to help you

[http://ubuntuforums.org/showthread.php?t=848424](http://ubuntuforums.org/showthread.php?t=848424)

It's a memory stick and I don't know the exact location to write it on terminal, on computer I only see USB DRIVE but it doesn't mount, nor shows anything on else on properties. Via terminal it isn't shown with ls on /media.

---

### Post by damis648 on 2008-07-05
> **falcon61102 said:**
> What do you mean he has no access to it?  It being the windows box?

The filesystem/partition table is corrupted. Maybe even something more serious. This would do no good. There is no access to the partition. (Or the drive??)

---

### Post by arashiko28 on 2008-07-05
> **damis648 said:**
> gParted finds all drives, and will not perform any operations unless the drive is unmounted. The drive MUST be unmounted... you did try it?

It doesn't see the drive, only my hard drive, I tried with device, with refresh devices, It doesn't exist for it.

---

### Post by damis648 on 2008-07-05
> **arashiko28 said:**
> It doesn't see the drive, only my hard drive, I tried with device, with refresh devices, It doesn't exist for it.

That is too bad.. I do not know if it is recoverable at all...

---

### Post by arashiko28 on 2008-07-05
:-|:-|:shock: I guess it can't be helped... there goes a 4GB memory... on windows keeps looping on an error about not being able to remove the drive, so I must eject it from my pc... that's even worse, right?

---

### Post by falcon61102 on 2008-07-05
It gives you that error when you try to do the safely remove hardware?

---

### Post by arashiko28 on 2008-07-05
YES

But, It happens that I tried it on another PC with a fresh install of windows, it gave me this message when I tried to see the files inside...
> Remove the writing protection of the drive at unit \Device\HardDisk1\DR5

It's translated from spanish, so... where is this and HOW do I do this on windows? It's and XP SP2 installation.

---

### Post by falcon61102 on 2008-07-05
Try right-clicking on My Computer and going to Manage.  From there go to Disk Management and see if you can see the drive.  If you can see it, you should be able to partition/format it there.  The data will of course be lost but you won't be out a drive.

---

### Post by arashiko28 on 2008-07-05
I can see it, but don't have the option to format, where is it? by right clicking I have remove, set free, all tasks (same as above) cut, properties and help.

---

### Post by falcon61102 on 2008-07-05
Normally by right clicking on the drive there is a format option.  Try going into the Disk Manager and seeing if it will allow you to delete the current partition and creat a new one.

---

### Post by arashiko28 on 2008-07-05
Can't format it like that it says it's writing protected...

On the other hand I went to help to see if for a time, this would have the solution... nope, it doesn't, it's the same old windows I left a year ago...

---

