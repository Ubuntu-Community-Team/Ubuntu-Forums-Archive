---
title: "where to create a network shares dir?"
date: 2010-03-31
forum: Networking &amp; Wireless
---

### Post by michael_j_w on 2010-03-31
Hello all,
 
I just have a quick question; where should my network shares directory be located? I just finished installing the latest ubuntu release onto my fileserver and have it all up and running, but each of the storage drives are individually mounted in the /mnt directory with samba and netatalk each mapping shares from /mnt/DriveName/ShareName. This is getting cumbersome when editting the .conf files, so i would like to create a directory called NetworkShares somewhere on the filesystem and have symlinks pointing the actual shares so i don't have to keep checking which drive a specific share is on. My first thought was the /usr dir but that didn't seem to have anything simmular in it so i thought i'd ask here.  
 
btw, is it posible to expand a partition to include multiple disks in linux, simular to dynamic disks in windows? 
 
Michael

---

### Post by ant2ne on 2010-03-31
I like to put my server side net shares in /data/shares/share1 /data/shares/share2 etc. I keep the perms on /data/shares tight, but modify them as needed on the /data/shares/share1 level as needed. Does that make sense? 

I also like to mount a second hard drive or partition on /data. Like /dev/sda2 is / and /dev/sda3 is /home but /dev/sdb1 will be /data. So in the event of an OS fail and re-install i dont' loose /data.

If you are wondering where to mount client net shares it gets a bit more complicated. I tend to mount them where a user can easily access them. Like /home/user/mountednetshare or even /home/user/Desktop/mountednetshare.

---

### Post by michael_j_w on 2010-04-01
Thank you, yes that makes sense. I do not have a /data directory but that's easy enough to change. Howerver, one thing i don't quite get is why you would not use the /mnt directory for mounting disks. I am kinda new to linux so please offer corrections but isn't that what /mnt is for?
 
Thanks for the reply!
 
Michael

---

### Post by ant2ne on 2010-04-01
From the server side, the shared directories are not mounted network drives. And they may not be mounted at all, unless, like me you use different hard drives or partitions. So it makes no sense to put it in the /mnt. 

Mostly it is just preference

If you have a dozen boxes (like me) putting the shared directories in /data/shares every time makes it easier for me to find the shares regardless of whether the /data folder is a drive or partition mount.

---

