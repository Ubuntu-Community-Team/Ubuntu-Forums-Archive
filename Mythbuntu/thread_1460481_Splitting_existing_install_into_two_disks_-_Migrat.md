---
title: "Splitting existing install into two disks - Migrating,"
date: 2010-04-22
forum: Mythbuntu
---

### Post by rramesh on 2010-04-22
Hi,

 I have a stock 9.04 mythbuntu. The install has everything on one 1TB disk. While debugging occasional video stutter, it was pointed out to me that the single disk install of OS/DB/Myth may be an issue. So, I want to move my OS and DB to a new disk leaving 1TB to myth only. 

Is there a simple solution for this? I know that grub is setup with UUID root setup. So simple disk disk addition and copying is not going to work. 

BTW, due to disk sizes, it is best to get a new (smaller) disk and move OS and DB there. But this is not a must. I am mildly open on this.

Ramesh

---

### Post by laffinet on 2010-04-22
I would suggest going the other way around: 

Leave your OS and database on the existing drive. Install the second drive and set everything up so that recordings, liveTV, videos are on the new drive.

All you have to do is:

1. Install the second drive, format it, edit your fstab to mount it on boot
2. Set up directories for liveTV, recordings, videos on the new drive
3. Copy your data (as in videos, recordings, liveTV stuff) across to the new drive.
4. In mythbackend setup, point the backend to the new directories (storage directories)

Let us know if you need more detail.

---

### Post by rramesh on 2010-04-23
> **laffinet said:**
> I would suggest going the other way around: 

Leave your OS and database on the existing drive. Install the second drive and set everything up so that recordings, liveTV, videos are on the new drive.

All you have to do is:

1. Install the second drive, format it, edit your fstab to mount it on boot
2. Set up directories for liveTV, recordings, videos on the new drive
3. Copy your data (as in videos, recordings, liveTV stuff) across to the new drive.
4. In mythbackend setup, point the backend to the new directories (storage directories)

Let us know if you need more detail.

I thought about this but did not have the heart to waste 1TB for OS+DB. But this may be the easy route. Do I have to setup mythbackend? Can't I simply copy and make a symbolic link and be done with?

Ramesh

---

### Post by laffinet on 2010-04-23
> **rramesh said:**
>  Do I have to setup mythbackend? Can't I simply copy and make a symbolic link and be done with?

Not really setting up the backend, just changing a few settings in mythbackend setup.

> **rramesh said:**
> I thought about this but did not have the heart to waste 1TB for OS+DB.

Oops, I misunderstood something here. You're obviously planning to use a smaller disk for the OS and DB. That makes things a bit more complicated since you do have to move/copy your current installation. Shouldn't be too hard, though.

What partitions do you have on your current drive 

```
sudo fdisk -l
```

Hopefully all your "data" (videos, recordings, etc.) resides on a separate partition.

***If ***that's the case, you would have to:
1. install the new drive
2. copy the existing OS partition to the new drive. Lots of ways to do this, clonezilla is one easy solution
3. reinstall/reconfigure grub to boot from the new drive
4. run mythbackend setup to point mythtv to the recordings, videos, liveTV locations on the old drive
5. Once you're satisfied everything runs, delete the OS partition on the old drive and add that space to the data partition

---

### Post by rramesh on 2010-04-23
I simply increased the backend video buffer to 96M (the max possible) and the stutter seem to have gone. 
I will experiment some more before calling this a solution. 

BTW, memory is (relatively) cheap (I have 2G), so  why limit backend to 96M max video buffer? More the better as long as we do not swap. So user should have freedom to set it to, say, 1min video =150M (20M*60/8 bytes - I think OTA  is 20Mbits/sec/channel) or even 300M. 

Ramesh

---

