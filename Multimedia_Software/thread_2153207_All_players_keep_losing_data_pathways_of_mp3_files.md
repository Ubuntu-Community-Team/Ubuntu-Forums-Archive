---
title: "All players keep losing data pathways of mp3 files"
date: 2013-06-10
forum: Multimedia Software
---

### Post by LSHINE on 2013-06-10
I keep dragging them into playlists. I use Clementine, Audacious and Qmmp. All do the same thing - when after a REBOOT I try to play a file that is in the playlist, it keeps skipping all the playlist, so I asume it looses the pathways somehow. Why does this happen?

---

### Post by dentaku65 on 2013-06-10
Are the mp3 files on an external drive?

---

### Post by samigina on 2013-06-10
Or the partition is not mounted on boot, maybe a NTFS partition?

---

### Post by LSHINE on 2013-06-11
Yes it is a NTFS partition. I basicaly use a dual boot. I have my Xubuntu on the same partition that Win7 are (C), and my mp3 files are on DATA(D) partition.
No it is not an external drive. And about mounting, I dont know how else must it be mounted. I dont have to do anything to access the D partition.

---

### Post by dentaku65 on 2013-06-12
You have to mount the partition via fstab
First discover the ntfs partiton
```
sudo fdisk -l
```
Then put the partition at the end of the fstab file
```
sudo nano /etc/fstab
```
Add this line, save and reboot
```
/dev/sd[COLOR="#FF0000"]**XY**[/COLOR] /media/ntfs ntfs defaults,uid=1000,rw 0 0
```

---

### Post by LSHINE on 2013-06-13
[img]http://imageshack.us/a/img10/7015/scr2y.jpg[/img]
After I write down the first 2 lines, this comes up, and I dont know where to put the last line.. Can you help me out here? :)
Cheers.

---

