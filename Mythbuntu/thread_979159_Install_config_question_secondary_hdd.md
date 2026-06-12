---
title: "Install config question secondary hdd"
date: 2008-11-11
forum: Mythbuntu
---

### Post by Saxomophone on 2008-11-11
I've decided to give mythbuntu another try, since there's been some progress on mythprime since my last go.

I have my primary hdd, and i have a secondary 500gb hdd which is formatted for jfs

Is there an easy way during the partitioning to mount the secondary hdd to where mythbuntu will store the media, so I don't have to tweak that later? If i tell the partitioner to put its mountpoint as /home, will that work?

Also, I do have an nvidia 8800 gts, am I better off using 8.04? I wanted to put the new kubuntu desktop on so i could see KDE 4, so if I go with 8.04 that won't work. Do I need 3d support for mythbuntu?

---

### Post by Saxomophone on 2008-11-12
Bump

---

### Post by Liviu-Theodor on 2008-11-12
I will answer about HDD, as I really didn't understood your other questions.

So, you can instruct the partitioner to mount the new HDD as /home, but is not enough.

After declaring the new partitions (eventually formatting them) and mount points, you should run the following command in command prompt:
```
blkid
```
Note your partitions and their ID and type.
```
sudo cp /etc/fstab /etc/fstab.backup
```
Just in case somethin wrong is happening... And finally:
```
gksudo gedit /etc/fstab
```
Or open /etc/fstab with your editor of choice. Edit /etc/fstab to indicate your new partition(s), with UUID, mount point, filesystem.

---

### Post by Saxomophone on 2008-11-12
Thank you. I'll try to do this tonight.

My other question is, I know there've been issues with nvidia drivers on 8.10. I have an Nvidia card, so am I better off using 8.04 -- as in, will I need the advanced graphic support with the real nvidia driver to use mythbuntu effectively, or is the default driver going to be adequate. I wanted to do 8.10 so I could add kubuntu desktop to it, so I could check out KDE version 4, since it's not on 8.04, and I heard great things about it.

---

### Post by johnnybirdman on 2008-11-12
> **Saxomophone said:**
> Bump

For my setup (1-40GB HD and 1-500GB HD) all I did was, during the partitioning stage, is give the 500GB HD a mount point of /home/media and that was it (and tell it NOT to format since I already had videos and music on the HD).  then symlink the music and video folders.
J.

---

### Post by Caps18 on 2008-11-12
Could you have a separate partition for a second Kubuntu OS?  It would keep them from impacting each other if something doesn't quite work.  You would just have to restart to switch, and getting the backend to work in the second OS to record shows while you are using the computer would take a little work.

The mythTV partition should be accessible from both operating systems I would think.

---

### Post by Liviu-Theodor on 2008-11-14
I have here NVIDIA GeForce 7200 and Ubuntu 8.10, using proprietary drivers. Haven't seen any issue with it. I can use it, maybe you can too. But I don't say that nobody encountered any issue with NVIDIA and Intreprid. And you can install also any desktop manager, like KDE or XFCE or Enlightenment or your choice. After doing that, at login prompt you could chose one of them.

---

