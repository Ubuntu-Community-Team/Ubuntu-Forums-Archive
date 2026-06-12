---
title: "LVM Victory!  but...."
date: 2009-05-25
forum: Networking &amp; Wireless
---

### Post by dearmrdear on 2009-05-25
I'm quite new to Linux/Ubuntu and have learned a great deal in the last month. I've set up a server using Xubuntu, formated the hd correctly (/boot in it's own primary partition...that was a learning experience) I've set up a LVM sytem and it works great except:
I can't read/write to the folders shared on my XP sys, I made sure that in /etc/fstab that each /var.. line  has "rw, noatime" but it's still not sharing. 
What am I missing? maybe a space or some formatting mistake in fstab? any ideas?
Also, if you know of other great resources like HowtoForge lemmy know, I'm really enjoying learning! Thanks

---

### Post by Girya on 2009-05-25
have you mounted the windows partition? if not search for a how to on mounting partitions. you'll probably need to do something like this open a xterm and paste or type: 

> sudo fdisk -l | grep NTFS | awk '{print $1}' 

this should return the partition that windows is on. it'll look like /dev/sda* (the * will be a number). 

Then type:

> sudo mkdir /mnt/windows 

this command will create a mount point for the windows partition

then type: 

> sudo mount /dev/sda* /mnt/windows

you should be able to acess windows from /mnt/windows

---

### Post by dearmrdear on 2009-05-25
Sorry for not explaining the problem completely...I have a computer with Xubuntu (using LVM) connected to a network, my dual boot Ubuntu/Xp (running Samba) sees the file folder mounted through Lvm but i can't write to them.

I though I set it up correctly, with "rw,noatime" in the options in fstab.

---

### Post by Girya on 2009-05-25
can you write to the windows folder on the local machine? I'm assuming you are booting into ubuntu on the dual boot machine.

---

### Post by dearmrdear on 2009-05-25
Xp says somthing to the effect of folder locked, Ubuntu says "action not supported by backend" somehow I feel this might be a samba issue.  Do you think i should play with SWAT?

---

