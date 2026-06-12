---
title: "trying to share a folder between to Ubuntu PC's"
date: 2008-12-04
forum: Networking &amp; Wireless
---

### Post by LowSky on 2008-12-04
OK I feel like a real idiot and have done everything I think correctly, so let me list all the steps

I want to share a folder on my hard drive called /Shared
I didn't have file permision so I tried to change the permissions using
```
sudo chown -R 777 /Shared
```
but nothing happen, it still says its owned my Root, when i right clcik on the file and look at the file properties.

OK I have Samba installed through add remove and have tried to mount the folder with using the command ```
sudo nautilus
``` and changing the file permission that way while also marking it shared.

Oddest thing is that the computer seems to be in the Windows Workgroup but I cant see or access the Shared folder.

I have no idea what is wrong, can anybody shed some light on what I might have done wrong..

Thanks

By the way the /Shared folder is a FAT32 Partition that mounts as a folder to  /

---

### Post by utnubuuser on 2008-12-05
Well, for starters, I think **sudo chown** is to change ownership, whereas **sudo chmod 777 <filename>** would change file permissions to read,write,execute for owner,group,others

and did you **right-click the folder** to get to **Sharing Options** (second from bottom -above Properties), then **share this folder**?

---

### Post by LowSky on 2008-12-05
yes I did right click the folder and share the folder. Oddly enought the other machine can see the Workgroup and I can even  share a folder on that machine, but its a moot point because that machine doen't have any files for sharing.

I also noticed that the machine has issues seeing the work group. I have started up samba and even tried to set up a new user.

I don't ge twhy this is so hard. All I should have to do is install samba, make sure both computers are part of the same workgroup (which they are), and share the folder, which I have rights to (I even tried sharing my local home folder to no avail).

---

