---
title: "NAS slow when using fstab."
date: 2011-06-18
forum: Networking &amp; Wireless
---

### Post by mensfort on 2011-06-18
dear Linux friends,

I am using my NAS with settings in fstab, but then I have only 4.4MBytes/sec. However, when I open computer->Network ->Windows-network->WORKSPACE->CH3MNAS, then I have a speed of 18MByte/sec. 

I notice a directory ~/.gvfs/volume_1\ op\ ch3mnas... but when I restart the PC, this directory is gone. It only is there after I use Nautilus first.

Also, I see some directory called  smb://ch3mnas/volume_1

Now I am totally confused... how to get the fast network speed automatically at boot of my PC? 
WHy is this hidden inside ~/.gvfs/.? ... I prefer something like /home/nas 

Which manual can I read about all of this if any..

---

### Post by Morbius1 on 2011-06-18
I can't answer the question of why a classic mount in fstab is slower that a gvfs-mount in Nautilus but I do have a suggestion.

First, instead of mounting it in nautilus use the following command:
```
gvfs-mount smb://server/share
```Substituting the correct values for "server" and "share".

Two things should happen:
* A mount icon will appear on your desktop
* The mount point in /home/username/.gvfs/share on server will be created.

Test the speed to make sure it's the same as when you do it from Nautilus and if everything works the same then use Gigolo to automount the remote share: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

As for the .gvfs mount point that can't be changed unfortunately so you'll have to create a symlink to someplace else if that's a problem.

---

### Post by mensfort on 2011-07-03
> **Morbius1 said:**
> I can't answer the question of why a classic mount in fstab is slower that a gvfs-mount in Nautilus but I do have a suggestion.

First, instead of mounting it in nautilus use the following command:
```
gvfs-mount smb://server/share
```Substituting the correct values for "server" and "share".

Two things should happen:
* A mount icon will appear on your desktop
* The mount point in /home/username/.gvfs/share on server will be created.

Test the speed to make sure it's the same as when you do it from Nautilus and if everything works the same then use Gigolo to automount the remote share: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

As for the .gvfs mount point that can't be changed unfortunately so you'll have to create a symlink to someplace else if that's a problem.
Thanks a lot, this makes my pc lots faster wth the NAS>...


However, now I face a new problem... all files are somehow hidden in terminal, but I can see them in Nautilus...  so Thunderbird cannot find 4,5GByte of e-mails anymore... terrible. I'll post a seperate problem about this.

---

