---
title: "nfs trouble mounting 2nd drive"
date: 2012-09-21
forum: Networking &amp; Wireless
---

### Post by kaio123 on 2012-09-21
hello,
i just cant figure out what i am doing wrong. i have tried 2 methods: one from the nfs doc on ubuntu. Let me know if you can help. Here's what i am trying to do. i have 2 drives. I have Movies in 2nd drive with 777 permission. i have the main drive that has ubuntu running and another share called /ubuntushare in main drive in it.

#ftab
/dev/sda5  /SecondDrive                 ext4  defaults  0  0

#/etc/export
/ubuntushare       192.168.1.0/24(rw,fsid=0,insecure,no_subtree_check,async)
/SecondDrive       192.168.1.0/24(rw,fsid=0,insecure,no_subtree_check,async)/SecondDrive/Movies   192.168.1.0/24(rw,fsid=0,insecure,no_subtree_check,async)    

Client:
Mac Lion sees the 2 mounts but the files are the same on both SecondDrive and ubuntushare. So i assumed something was wrong. 

I try 2nd method using ubuntu nfs guide change my fstab and export to:

@fstab
/dev/sda5  /SecondDrive                 ext4  defaults  0  0
/SecondDrive/Movies /export/Movies      none    bind    0  0
/ubuntushare /export/ubuntushare        none    bind    0  0

#/etc/export
/export                    192.168.1.0/24(rw,fsid=0,insecure,no_subtree_check,async)
/export/Movies         192.168.1.0/24(rw,fsid=0,insecure,no_subtree_check,async)
/export/ubuntushare 192.168.1.0/24(rw,fsid=0,insecure,no_subtree_check,async)           


with this 2nd setting i see movies and ubuntushare in mac but dont see any files now.

What am i doing wrong. Which is the correct method ? Why am i seeing wrong files in my 2nd drive ?

---

### Post by Deepak A on 2012-09-21
what is *showmount -a*  showing?

---

### Post by kaio123 on 2012-09-22
for the first case showmount -a shows
All mount points on ubuntuhtpc:
192.168.1.4:/SecondDrive
192.168.1.4:/SecondDrive/Movies
192.168.1.4:/export
192.168.1.4:/mediashare
192.168.1.4:/multimedia
192.168.1.4:/ubuntushare

not sure why mediashare and multimedia are still in there. i removed/deleted those 2

---

### Post by LewisTM on 2012-09-24
fsid=0 should be only for the 'root' share, i.e. /export
That way you can mount the share on the client with [FONT="Courier New"]<IP.ADDRESS>:/share[/FONT] instead of [FONT="Courier New"]<IP>:/export/share[/FONT]
Note that this is only to make a nice export tree for your NFS server. You could very well use NFSv3 style and export/mount all shares with their full path names (and no fsid=0).

Also, when you make changes to your exports, run [FONT="Courier New"]sudo exportfs -ra[/FONT] to apply them.

Cheers!

---

