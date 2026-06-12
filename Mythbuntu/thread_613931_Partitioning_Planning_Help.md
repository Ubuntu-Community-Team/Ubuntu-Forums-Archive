---
title: "Partitioning Planning Help"
date: 2007-11-15
forum: Mythbuntu
---

### Post by tonyr1988 on 2007-11-15
I'm waiting to get my new hard drive before I fully go to Mythbuntu, but I'm trying to plan as much as possible beforehand to make transitioning easier. My disk space will be:

15GB Internal Drive
160GB Internal Drive
500GB External Drive

On the small 15GB drive, WinXP has been there for a while. I plan on keeping it there - I only boot it once or twice a year, and it's small enough to not be a bother.

But how should I split up the other two drives? I need space not only for recordings, but also for normal video / music / pictures / etc. It will be a backend/frontend/normal desktop set up. I was thinking about having a 20-ish GB root partition (ext3) and /home for the rest (probably xfs?). I would just have ~/Videos, ~/Recordings, ~/Music, etc. within my home directory.

It looks like, with LVM, I can have one partition span my 160 and 500 drives. Is that right? If so, could I do this:

First 20GB of 160GB Internal drive is /. 140GB + 500GB = 640GB for /home.

Am I missing something? Would that work?

---

### Post by Abishye on 2007-11-17
I tried redirecting my media files to a large /home directory on a large XFS partition but that ended up biting me.  I had to delete the /home partition and create my large partition as /var/lib so mythtv would be happy.  Same results installing everything by hand, installing mythtv on top of ubuntu, or installing mytybuntu.  Just something to think about.

[http://www.mythtvtalk.com/forum/viewtopic.php?t=6764](http://www.mythtvtalk.com/forum/viewtopic.php?t=6764)

---

### Post by tonyr1988 on 2007-11-18
What directories does myth not like storing stuff in?

I currently use /mythtv/recordings, and it has no problem, so I assumed it could use ~/Recordings.

Also, is my understanding of LVM correct, that I could have one partition spanning multiple drives?

---

### Post by Abishye on 2007-11-18
Everything I have read indicates that LVM will work fine, although a bit more complicated.

"Adding Another Disk with LVM
If you are using LVM, adding more disk space is easy. You first need to create a physical volume
on the new disk. You will need to replace the device name, volume group name, logical volume
name, and mount point in these examples with those from your own system; you can retrieve
most of this information from the output of df –h. In the following example, you can see that
the MyVolumeGroup volume group has a logical volume named home that is mounted on /home.
You can also see other logical volumes and their mount points: root on /, tmp on /tmp, var on
/var, and usr on /usr."
Taken from Practical MythTV
Building a PVR and Media Center PC

As far as difficult recording to another directory I'm sure that was just my lack of knowledge preventing me. :)

---

### Post by Abishye on 2007-11-18
Not sure if you saw this one too:

[http://ubuntuforums.org/showthread.php?t=584473](http://ubuntuforums.org/showthread.php?t=584473)

---

