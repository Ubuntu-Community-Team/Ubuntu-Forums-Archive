---
title: "hold my hand (fstab mounting)"
date: 2007-08-15
forum: Multimedia &amp; Video
---

### Post by godsyn on 2007-08-15
I've reformatted a partition that was ntfs to ext3 for storing mythTV media.
All I want to do now is mount said partition to /var/lib/mythtv/ , but i'd like to save the media I already have.
/dev/hdb1 has already been formatted from NTFS to EXT3 and is mounted at /media/hdb1/ .

Please check over my proposed order of operations and see if it seems logical.

```

remote@synserv:/var/lib/mythtv$ sudo /etc/init.d/mythtv-backend stop
remote@synserv:/var/lib/mythtv$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb2
UUID=1c9ba20f-6516-4ef0-9cf0-252da39409e7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
# UUID=98F48D42F48D241A /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb1
/dev/hdb1 /media/hdb1/               ext3    defaults,errors=remount-ro 0       1
# /dev/hdd1
UUID=0690AE4D90AE42D3 /media/hdd1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb5
UUID=7ae3ef33-d2bd-4d45-afe2-9a3c9c48bbd3 none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0

```the following are what I am thinking needs to be done.```
sudo mkdir /media/hdb1/mythtv
sudo cp -p -R /var/lib/mythtv /media/hdb1/
umount /dev/hdb1
sudo nano /etc/fstab
```and edit fstab entry to: ```
# /dev/hdb1
/dev/hdb1 /var/lib/mythtv/recordings/               ext3    defaults,errors=remount-ro 0       1
``````
sudo mount -a
```Look right? or am I missing something?

the directory's current permissions that i'm wanting to mount to are ```
remote@synserv:/var/lib/mythtv$ ls -l -a
total 12
drwxr-xr-x  3 root   root   4096 2007-07-18 11:35 .
drwxr-xr-x 46 root   root   4096 2007-08-14 05:34 ..
drwxrwsr-x  2 mythtv mythtv 4096 2007-08-15 08:45 recordings
```

Will this be an issue?

---

### Post by raijinsetsu on 2007-08-15
Only found one error (I think)
In the second code snippet, you umount hdb1, but don't you also need to umount hdd1, as hdb1 is going to take it's place?

---

### Post by godsyn on 2007-08-15
I'm sorry for not being more clear. No, as /dev/hdb1 has already been formatted from NTFS to EXT3 and is mounted at /media/hdb1/ .  Modifying top post for clarity.

---

### Post by raijinsetsu on 2007-08-16
Oh! So, you were storing the mythtv stuff in your root partition...
Then everything looks good :)

---

### Post by godsyn on 2007-08-22
nooo..
# /dev/hdb2
UUID=1c9ba20f-6516-4ef0-9cf0-252da39409e7 /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb2 is /

---

