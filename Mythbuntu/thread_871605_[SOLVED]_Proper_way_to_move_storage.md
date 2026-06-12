---
title: "[SOLVED] Proper way to move storage"
date: 2008-07-27
forum: Mythbuntu
---

### Post by GyroTech on 2008-07-27
Hi I have a (mostly) working Mythbuntu 8.04 box and have added another hard drive to increase the capacity.
What is the proper way to 'redirect' MythTV's drive useage to this new drive?? I think the simplest way would be to turn the /var/lib/mythtv/<folders> into links to folders on the new drive.
I guess a more sensible way would be to reconfigure mythtv and samba (and whatever else uses those folders) to simply use the folders on the new drive.

So, can anyone suggest a good way (and where the options are in mythtv to do so)??

Thanks

---

### Post by nickrout on 2008-07-27
in mythtv-setup add it as a storage group. Simple, no more to do.

---

### Post by GyroTech on 2008-07-27
I thought storage groups were for recordings only. Can I use them for imported videos\music\pictures too?? I tried creating a new storage group and pointed the directory at a directory on the new drive with some videos I had on another machine, but they didn't show up in the video manager, nor did a rescan of the video manager find them.

---

### Post by newlinux on 2008-07-27
You can point to multiple directories in mythvideo by separating them with a colon in the video directory field.

---

### Post by nickrout on 2008-07-27
> **GyroTech said:**
> I thought storage groups were for recordings only. Can I use them for imported videos\music\pictures too?? I tried creating a new storage group and pointed the directory at a directory on the new drive with some videos I had on another machine, but they didn't show up in the video manager, nor did a rescan of the video manager find them.

sorry I slightly misunderstood your question.

You can use storage groups for recordings only. But if you move lots of recordings from the old location to the new disk (and new storage group) then you will free up your older hard drive for more videos and music. 

Or you can do as suggested by newlinux.

---

### Post by frego on 2008-07-28
And then there's always LVM.  It will do what you want.  That's how I have mine setup.  But God help you when a drive fails.  It's a real pain to get things back when something goes wrong.  And your most likely to lose everything on the entire array.

---

### Post by nickrout on 2008-07-28
Indeed, which makes LVM a very dangerous soution. Stick to storage groups. Thats why they were developed.

---

