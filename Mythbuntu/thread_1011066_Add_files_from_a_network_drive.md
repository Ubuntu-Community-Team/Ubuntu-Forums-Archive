---
title: "Add files from a network drive"
date: 2008-12-14
forum: Mythbuntu
---

### Post by camdagr8 on 2008-12-14
Is there a way to add a directory to MythTV from a network drive? 

I have all these video files on another samba server and was hoping I could just scan that folder and viola! they would show up in my list. But for the life of me I can't seem to find this functionality. I'm sure I'm overlooking something, so if anyone can help me out, I would totally appreciate it.

Thanks!

---

### Post by ian dobson on 2008-12-14
Hi,

You need to first of all mount the samba share, I usually do by adding a line to rc.local, something like:-

mount -t cifs  //192.168.0.2/data /mnt/video -o username=<user>,password=<password>

Then just set myth video (Setup n myth-frontend) to use the directory defined in the mount (/mnt/video)

Regards
Ian Dobson

---

### Post by Caps18 on 2008-12-15
Or if you have nothing currently in your video directory, and only want to use the network drive (although file transfer speed may come into play), you can mount it to /var/lib/mythtv/videos.  Then you won't have to change anything in MythTV, it should just find them.

---

### Post by bah1976 on 2008-12-15
Or, do a combination of both...  

Do the mount like Ian says.  Then, let's assume that you have videos already on your myth box that you want to keep.  go to your videos directory (default listed):
```
cd /var/lib/mythtv/videos
```
then, link to your mounted folder
```
sudo ln -s /mnt/video Network\ Videos
```
Next time you scan, or if you have it set that it scans everytime (I forget the wording of the option - something about newly added videos being shown by default), you'll see the Network Videos folder in your videos list, and you can browse everything that's there.

---

