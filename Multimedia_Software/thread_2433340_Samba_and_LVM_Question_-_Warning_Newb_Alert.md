---
title: "Samba and LVM Question - Warning Newb Alert"
date: 2019-12-17
forum: Multimedia Software
---

### Post by drelliott06 on 2019-12-17
I got stuck in a password loop on my ubuntu server for plex which ultimately ended in performing a clean install with 18.04

Everything is up and running but I made a few changes this time around. 

I created an LVM using two hard drives for a total of 10TB and I mounted this volume to /mnt/media

I then installed samba and edited the configuration file path to /mnt/media

Windows recognized the media folder without any issues and I can now transfer files easily back and fourth

However, I just noticed that windows is reading media at 5TB and not 10TB

Is this because windows can not understand LVM or did I setup the smb.conf incorrrectly?

Thanks in advance for your expertise

---

### Post by drelliott06 on 2019-12-17
I believe the answer is on this page

[https://unix.stackexchange.com/questions/329162/setting-samba-share-hdd-space-available-to-win10](https://unix.stackexchange.com/questions/329162/setting-samba-share-hdd-space-available-to-win10)

I will keep at it and hopefully figure it out.  

Not that I can't type other peoples code, I want to understand the steps and reasoning.

---

### Post by drelliott06 on 2019-12-17
Additional information

lsblk shows the mountpoint as /mnt/media

sdb                8:16   0   5.5T  0 disk
&#9492;&#9472;sdb1             8:17   0   5.5T  0 part
  &#9492;&#9472;media-volume 253:0    0  10.9T  0 lvm  /mnt/media
sdc                8:32   0   5.5T  0 disk
&#9492;&#9472;sdc1             8:33   0   5.5T  0 part
  &#9492;&#9472;media-volume 253:0    0  10.9T  0 lvm  /mnt/media


My fstab enty 

/dev/media/volume /mnt/media ext4 0 1


My smb.conf

[media]
path = /mnt/media
   browseable = yes
   read only = no
   guest ok = yes
   force user = root
   force group = root
   force directory mode = 0777

---

