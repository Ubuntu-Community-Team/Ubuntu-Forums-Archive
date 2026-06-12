---
title: "Videos on my network??/"
date: 2009-02-23
forum: Mythbuntu
---

### Post by ghostwalker50 on 2009-02-23
Hi guys, 

im trying to map a network drive on my mythtv system and then tell myth to look at that mapping  for my video liberary.


thanks 
fernando

---

### Post by murchball on 2009-02-24
I have a similar setup. I use samba to mount the video directory on my file server on my frontend, then I set the videos directory to that mount point.

Something like:

```
sudo apt-get install smbfs
sudo mkdir /mnt/videos
```
add the following to /etc/fstab
      ```
//ipaddress/sharename /mnt/videos smbfs default 0 0
```
```
sudo mount -a
``` (this tests your edit, make sure you fix any errors before continuing)
```
ls /mnt/media
``` should list your video files
Then go into Myth and set your videos directory to /mnt/videos

---

### Post by theophile on 2009-02-24
If the remote directory is on a Linux box, NFS would be easier than SMB.

---

### Post by ghostwalker50 on 2009-02-24
you guy are best, how can i get the videos to play full screen.

thanks

---

