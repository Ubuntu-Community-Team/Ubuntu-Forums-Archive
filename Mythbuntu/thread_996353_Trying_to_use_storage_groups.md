---
title: "Trying to use storage groups"
date: 2008-11-28
forum: Mythbuntu
---

### Post by Panhead Bill on 2008-11-28
I am attempting to understand how to utilize storage groups.  I have a system running 7.10 with a 5 drive LVM, and when I wipe it clean and install 8.10 I would like to use storage groups instead of LVM.

In my searching and cogitation I have pieced together the following steps and assumptions.  

Any information would be helpful.

For the purpose of this list I am using a pc with two drives, one old 10 gig for Mythtv (/dev/sda), and the fractionally newer 40 gig for recording storage (/dev/sdb).  (This pc will end up as a second Frontend/Slave Backend in a three pc system)

1) I assume that the drive has to be formatted and set up with a mount point.  I formatted the drive as XFS, with a mount point of: /var/lib/mythtv/storage

2) As part of the setup of Mythtv on the 10 gig drive I set up a default storage group and add a directory of /var/lib/mythtv/storage

3) I read that I now have to edit /etc/fstab to include a line something like:
# /dev/sdb6   /var/lib/mythtv/storage   xfs   realtime   0   2

So what am I missing?  What do I do to /dev/sda to NOT place recordings on this drive?  

Panhead Bill

---

### Post by Panhead Bill on 2009-07-02
Nevermind.

 From what I can figure out, storage groups can place different items on different disks, Videos on say SDB1, Recordings on SDC1 etc.

Since I have 4 drives that I want to store my recordings on, LVM2 seems the way to go.

---

### Post by tgm4883 on 2009-07-02
> **Panhead Bill said:**
> Nevermind.

 From what I can figure out, storage groups can place different items on different disks, Videos on say SDB1, Recordings on SDC1 etc.

Since I have 4 drives that I want to store my recordings on, LVM2 seems the way to go.

You have figured out incorrectly. You can set up storage groups to save recordings to multiple drives. That is what it was created for.

To go back to your steps.

> 
1) I assume that the drive has to be formatted and set up with a mount point. I formatted the drive as XFS, with a mount point of: /var/lib/mythtv/storage

Good
> 
2) As part of the setup of Mythtv on the 10 gig drive I set up a default storage group and add a directory of /var/lib/mythtv/storage

Good
> 
3) I read that I now have to edit /etc/fstab to include a line something like:
# /dev/sdb6 /var/lib/mythtv/storage xfs realtime 0 2
Good.

So what is the problem? Is the only storage group that is setup /var/lib/mythtv/storage? Is your root partition filling up? It seems setup correctly now, but you haven't said why you think it is broke.



Storage groups have nothing to do with having videos on one drive, recordings on another, etc.

---

### Post by Chuckels550 on 2009-07-07
Did you ensure that mythtv has the necessary permissions to use those new storage directories?

---

### Post by Panhead Bill on 2009-07-14
I think that tgm4883 stated the problem better than my ramblings; Root is filling up.

I think that chuckels550 has put his finger on the missing step.  How do I set the permissions on Mythtv?  Was it on the how-to?

I'm trying to use LVM on this pc - my master back end. 
 
I think Storage Groups would be simpler to use (If I can understand how to make it work) on my slave backend/frontends.  These will be two drive pc's (one strictly for recordings, the other for the os, swap, and storage of the images that would be low useage).

---

### Post by chipppy on 2009-07-19
Good Morning

Sorry to break into a thread but I think the answer t my Storage Group problem my be here (I hope)


I have added a 1TB HDD and tried to setup Storage Groups but it is not working.  After I do all the stuff in the mythtv setup step and then back out it complains about not being able to create //.test, so I think that your permission thought may be what I need to do, so

How to I check to see it Mythtv has the correct permissions on my new HDD?
What should it look like?
How to I change it if it is wrong?

Any and all help is greatly appreciated as I have 1GB of space on my current HDD and the kids what 5 new disc to be burnt into the system.

Cheers
chipppy

---

### Post by tgm4883 on 2009-07-19
> **chipppy said:**
> Good Morning

Sorry to break into a thread but I think the answer t my Storage Group problem my be here (I hope)


I have added a 1TB HDD and tried to setup Storage Groups but it is not working.  After I do all the stuff in the mythtv setup step and then back out it complains about not being able to create //.test, so I think that your permission thought may be what I need to do, so

How to I check to see it Mythtv has the correct permissions on my new HDD?
What should it look like?
How to I change it if it is wrong?

Any and all help is greatly appreciated as I have 1GB of space on my current HDD and the kids what 5 new disc to be burnt into the system.

Cheers
chipppy

you should have mythtv group ownership on your recording dir
what is the output of
```
ls -l /path/to/recording/dir
```

---

### Post by chipppy on 2009-07-21
Good Morning

As my HTPC is a standalone unit I an typing the result and not copy/paste

My path is /mnt/store/d2.  Inside this directory I have created directories the same as the normal mythtv storage directories (videos, recording, music, etc)
The (green highlighted letters/blue letters) at the end of each line to to mention the colour of the folder names incase this helps.

[B]chipppy@chipppy=htpc: /mnt/store$ ls -l 
total 0
drwxr-xr-x 8 chipppy chipppy 160 2009-07-19 19:52 d2      (blue letters)

chipppy@chipppy=htpc: /mnt/store/d2$ ls -l
total 0
drwxrwxrwx 2 chipppy chipppy 6 2009-07-19 20:01 LiveTV     (green highlighted letters)
drwxrwxrwx 2 chipppy chipppy 6 2009-07-19 20:02 music      (green highlighted letters)
drwxrwxrwx 2 chipppy chipppy 6 2009-07-19 20:03 pictures   (green highlighted letters)
drwxrwxrwx 2 chipppy chipppy 6 2009-07-19 20:04 poster     (green highlighted letters)
drwxrwxrwx 2 chipppy chipppy 6 2009-07-19 20:05 recordings (green highlighted letters)
drwxrwxrwx 8 chipppy chipppy 142 2009-07-19 20:06 videos   (blue letters)[/B]

I have already transfered a heap of dvd's into the videos folder ready for once I get storage groups working.


For clarity the actual error message that comes up when I exit out of Mythtv backend setup, after setting up my storage group, is **Cannot create a file //.test, directory is not writeable.**

My new stoage group is called **mnt/store/d2**

Hope this helps

Cheers 
chipppy

---

### Post by crez79 on 2009-07-21
Did you edit the default storage group, or did you create a new one. With those errors, it seems like there isn't a default group set up. Also, make sure there isn't a '/' at the end of the directory when you enter it into the storage group. Also, be sure to enter the entire directory you want the recording to go (/mnt/store/d2/recordings). d2's subdirectories are writable by everybody, but d2 itself isn't.

If you created a new storage group and didn't edit the default storage group, I recommend deleting the group (press 'm') you made and editing the default group.

---

### Post by chipppy on 2009-07-21
Good Evening

I have deleted the new group that I created and entered the new HDD folders into the default storage group as new directories.
This has fixed the **cannot create file //.test** error.

I cannot see the movies that I have already placed into /mnt/store/d2/videos.  I did notice that there is an extra **/** at the end of the directory path.  I have gone back in and edited it and deleted the extra **/** but for some strange reason Mythtv keeps putting it back in.

Any ideas on how to fix this extra **/** problem.  

I feel we are close to getting this working

Thanks for the assistance so far

Cheers
chipppy

---

### Post by newlinux on 2009-07-21
are you trying to view the videos in /mnt/store/d2/videos using mythvideo? Did you add it to the mythvideo folder and rescan?

---

### Post by chipppy on 2009-07-21
Good Evening

[SIZE="7"]Yeah baby![/SIZE]

My problem is all fixed and working great.
I delete my new group and just edited the default group as per above reply-post.  So simple a fix to my mistake

Again thanks heaps for the assistance.  

Cheers
chipppy

---

