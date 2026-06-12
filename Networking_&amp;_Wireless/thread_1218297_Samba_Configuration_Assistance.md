---
title: "Samba Configuration Assistance"
date: 2009-07-20
forum: Networking &amp; Wireless
---

### Post by iTrascurato on 2009-07-20
Hey guys,

I have Samba working as I want it to, sharing specific folders to specific users on my external HD over the network.

I tried doing the same sequence of events to add a user and folder as I did a few weeks ago, and now it "works" but when the user logs in and then goes to mount that specific folder, all goes as planned except they are only getting read only permissions to that given folder.

NOTHING is different for this user then the others.  Any ideas?

```

 # useradd resource
 # smbpasswd -a resource

```

smb.conf Entry:
```

[Test]
    path = /media/Slave/Test
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    valid users = resource
    admin users = resource

```

---

### Post by swerdna on 2009-07-20
This directory: /media/Slave/Test
Probably doesn't have permissions that allow user "resource" to write as a Linux user. You can change the permissions to drwxrwxrwx or you can change the owner to resource and the group to resource. Either should work. There are a couple of other ways to match the permissions but two are probably enough to give you a good choice. I'd change the owner.

In fact I'd make a directory owned by "resource" and a share like this:
```
[Test]
    path = /media/Slave/Test
    read only = no
    force user = resource
    valid users = resource
```
and for added security I'd chmod the directory to 750 (drwxr-x---) and chown it to resource:resource

For more on crafting shares see the linked sections in a Samba/Ubuntu tutorial titled:
[Secure Read-write Shares; no Guest Access]("http://ubuntu.swerdna.org/ubusambaserver.html#rwauth")
and
[Special Purpose Modifications for Enhanced Privacy and/or Security]("http://ubuntu.swerdna.org/ubusambaserver.html#special")

---

### Post by iTrascurato on 2009-07-20
Thanks, I'll try this first thing in the morning.  I didn't chown anything, but I have tried chmodding to 777 for ***** and giggles.  This sounds right though and it's a stop I forgot to take. 

Thanks again and I'll let you know how it goes.

---

### Post by iTrascurato on 2009-07-21
Oddly, no matter which method of chown I try, I cannot get it to allow the command.  

Under a ROOT shell, chown resource:resource Resource       (while in /media/Slave)  does not work.

"chown: changing ownership of "Resource" : Operation not permitted.



GAH!

---

### Post by swerdna on 2009-07-21
> **iTrascurato said:**
> Oddly, no matter which method of chown I try, I cannot get it to allow the command.  

Under a ROOT shell, chown resource:resource Resource       (while in /media/Slave)  does not work.

"chown: changing ownership of "Resource" : Operation not permitted.



GAH!
That sounds very much like and external NTFS or FAT32 partition/driv, neither of which respond to chown or to chmod. Assuming it's NTFS, you have to remount it writeable. check for fat or ntfs partitions with this command in a terminal: ```
sudo fdisk -l | egrep "FAT|NTFS"
```for example here's mine:
```
ubu904:/home/john # sudo fdisk -l | egrep "FAT|NTFS"
/dev/sda1               1          64      514048+   6  FAT16
/dev/sdb1   *           1        2550    20482843+   7  HPFS/NTFS
ubu904:/home/john # 
```
That shows that for me there is an NTFS drive at /dev/sdb1. So I would edit my filesystem table (the file /etc/fstab) and change the line that controls the permissions on sdb1 to the following:
```
/dev/sdb1    /path_to/mount_point    ntfs-3g    defaults    0 0
```
That line allows the users to write to the drive. Reboot after the edit. You would change sdb1 and the path to match your situation.

Of course, it might not be NTFS, or this might all be a bit confusing. If it's not NTFS or you are confised, then post here the contents of the file /etc/fstab and post here the return you get in a terminal when you run this command:```
sudo fdisk -l
```

---

### Post by iTrascurato on 2009-07-29
> **swerdna said:**
> That sounds very much like and external NTFS or FAT32 partition/driv, neither of which respond to chown or to chmod. Assuming it's NTFS, you have to remount it writeable. check for fat or ntfs partitions with this command in a terminal: ```
sudo fdisk -l | egrep "FAT|NTFS"
```for example here's mine:
```
ubu904:/home/john # sudo fdisk -l | egrep "FAT|NTFS"
/dev/sda1               1          64      514048+   6  FAT16
/dev/sdb1   *           1        2550    20482843+   7  HPFS/NTFS
ubu904:/home/john # 
```
That shows that for me there is an NTFS drive at /dev/sdb1. So I would edit my filesystem table (the file /etc/fstab) and change the line that controls the permissions on sdb1 to the following:
```
/dev/sdb1    /path_to/mount_point    ntfs-3g    defaults    0 0
```
That line allows the users to write to the drive. Reboot after the edit. You would change sdb1 and the path to match your situation.

Of course, it might not be NTFS, or this might all be a bit confusing. If it's not NTFS or you are confised, then post here the contents of the file /etc/fstab and post here the return you get in a terminal when you run this command:```
sudo fdisk -l
```

Sorry for the slow response but thanks for the help!  I've been very busy.

```
root@ITGuy:~# fdisk -l | egrep "FAT|NTFS"
/dev/sda1   *           1       49798   400002403+   7  HPFS/NTFS
/dev/sdb1               1      121601   976760001    c  W95 FAT32 (LBA)
root@ITGuy:~# 
```

Thats what it brings up.  The network drive is /media/Slave.  Should I be unmounting Slave and then finding it in /dev or do you think the second drive in that /dev grep is it?  It is a 1TB external HD, btw.

---

### Post by swerdna on 2009-07-29
You said it was an external usb drive. So that's likely sdb1. You can check that by running the commands:```
df -Th
sudo fdisk -l
```The first command should show a fat partition in /media/Slave. Tell me if it's different.

Then we if it's sdb1 that we're looking at: it needs to be remounted as outlined in this reference:
[HowTo [Suse / openSUSE] mount FAT32 (VFAT) partitions with read-write access]("http://opensuse.swerdna.org/susefat32.html")
That wasn't written for Ubuntu but the principle is exactly the same.

I think that "Test" is a directory that you created on sdb1 and that "Slave" is not located on sdb1 but is located on the Ubuntu partition as a place for sdb1 to be mounted, is that right? I need to know if I understand it properly. If I'm right, do this:

Unmount the drive with this command:```
sudo umount /dev/sdb1
```
Then check the directory Media is intact by going there in Nautilus and looking to see if it still exists. If it's not there then run this command to remake it:```
sudo mkdir /media/Slave
```

Then edit a line into the file system table, fstab, a text file located at /etc/fstab. Open it for editing with this comman```
gksu gedit /etc/fstab
```

Place this line at the end of the file but MAKE SURE there is a blank line after it:```
/dev/sdb1 /media/Slave vfat uid=billy,gid=billy,umask=0000,utf8=true 0 0
```

Run the mount command:```
sudo mount -a
```

The drive should appear permanently mounted at /media/Slave and with permissions drwxrwxrwx and owner billy:billy. Check with this:```
ls -l /media
```you should see like this:```
drwxrwxrwx  2 billy billy  4096 2009-07-30 09:27 Slave
```

End of task.

---

