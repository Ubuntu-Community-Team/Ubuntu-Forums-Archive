---
title: "Sharing additional folders via samba"
date: 2009-05-18
forum: Networking &amp; Wireless
---

### Post by prhammer on 2009-05-18
I'm using Ubuntu 8.10, I have set up samba and it is working fine for the initial folder I shared. I now want to share another folder. It is on an external drive. I thought that I could just change the sharing settings on the sharing tab in properties. I did this and the folder became visible from my windows (virtual machine) and mac computer. When I try to open folder I get an error message. In windows it says not accessible and you might not have permission to use this network resource.

I ran chmod and changed permissions to 0777, but this did not seem to resolve the problem.

Can someone explain what I am doing wrong?

Thanks,
Ron

---

### Post by superprash2003 on 2009-05-18
is it an ntfs drive?? have you configured samba correctly?

---

### Post by prhammer on 2009-05-18
> **superprash2003 said:**
> is it an ntfs drive?? have you configured samba correctly?

It is FAT32. Samba seems to be configured correctly. I shared a folder on my main hard drive using the same method (adjusting sharing settings in properties) and it worked fine. Is there different when using an external drive? 

-Ron

---

### Post by superprash2003 on 2009-05-18
i dont think fat32 works well with samba.. only NTFS would work..

---

### Post by swerdna on 2009-05-18
Fat32 works fine with Samba. I see you've chmod-ded to 777. That's guest access. If you haven't also allowed guest access in the configuration stanza for the share (in the Samba config file -- smb.conf) then that will cause an access problem.

Another possibility is that the chmod-ding didn't stick because the partition was mounted non-writeable. So check the permissions on the mount with this command in a console window: ```
ls -l /path_to/mount_directory
```
and review the configuration stanza for the share with this command in a console window: ```
cat /etc/samba/smb.conf
```

---

### Post by Iowan on 2009-05-18
As I recall, Samba can only tighten permissions, so if partition is (for example) mounted read-only, Samba cannot grant write permissions.

---

### Post by swerdna on 2009-05-18
> **Iowan said:**
> As I recall, Samba can only tighten permissions, so if partition is (for example) mounted read-only, Samba cannot grant write permissions.
Both Samba and Linux permissions can tighten the sharing situation. The best way to think about it is that the final permissions for a Samba Linux share are set as the stricter of the individual permissions of Samba and of Linux.

For this reason, prhammer needs to look at both "cat path_to smb.conf" and "ls -l path_to directory" as advised above.

---

### Post by prhammer on 2009-05-18
Swerdna:
It appears that the partition is mounting as unwriteable. So none of the changes are sticking. I'm not sure how to prevent that.

-Ron

---

### Post by swerdna on 2009-05-18
> **prhammer said:**
> Swerdna:
It appears that the partition is mounting as unwriteable. So none of the changes are sticking. I'm not sure how to prevent that.

-Ron
Well you could test if changing the permissions in the mount will help the situation. It should and if it does you could then make it a permanent affair. So check what the drive mount config look like with this command:
```
sudo mount 
```
That should tell you what drive and partition is being allocated to the FAT device, something like e.g. for sake of illustration /dev/sdc5. And also where it is being mounted (e.g. for sake of illustration /path_to/some_directory).

Unmount it with this command: ```
sudo umount /dev/sdc5
```(change sdc5 to match your situation).
Then remount it in the same place with this command in a console window:
```
mount -t vfat -o umask=0000,gid=users,utf8=true /dev/sdc5 /path_to/some_directory
```
Then check the Linux permissions on the shared directory and the accessibility over the LAN in windows. See if that's given access. If "yes" then you can make it permanent.

At this point, a question, is this FAT(32) partition mounting by being autosensed as a plug-in USB drive OR is it a permanent mount with a line in the fstab file that controls the process? (you can check fstab with the command: cat /etc/fstab).

---

### Post by prhammer on 2009-05-19
> **swerdna said:**
> 
At this point, a question, is this FAT(32) partition mounting by being autosensed as a plug-in USB drive OR is it a permanent mount with a line in the fstab file that controls the process? (you can check fstab with the command: cat /etc/fstab).

It is being autosensed as a plug-in USB drive. I had attempted to do an fstab entry, but I think I botched it - because it didn't mount where I wanted it to mount after a restart.

I'll do the diagnostics that you suggested a bit later today.

thanks,
Ron

---

### Post by prhammer on 2009-05-19
I was able to unmount and then mount the drive properly. I used the following for mounting:
```
sudo mount -t vfat -o umask=0000,gid=users,utf8=true /dev/sdc1 /media/winfiles/
```

This did mount it as writable, but the owner is root. I tried to change the owner and group for one of the folders on the drive:
```
 sudo chown persyst:persyst /media/winfiles/BIG_A
```
but I received the error: chown: changing ownership of `/media/winfiles/BIG_A': Operation not permitted

---

### Post by swerdna on 2009-05-19
> **prhammer said:**
> I was able to unmount and then mount the drive properly. I used the following for mounting:
```
sudo mount -t vfat -o umask=0000,gid=users,utf8=true /dev/sdc1 /media/winfiles/
```

This did mount it as writable........... 
That's good -- That proves the problem is with the default automount coded into Ubuntu for fat32 by the devs. They have made it a policy to mount read-only. You can work around that.

> **prhammer said:**
> but the owner is root. I tried to change the owner and group for one of the folders on the drive:
```
 sudo chown persyst:persyst /media/winfiles/BIG_A
```
but I received the error: chown: changing ownership of `/media/winfiles/BIG_A': Operation not permittedYou can't chown a mounted FAT drive. It remains bound to the permissions prescribed earlier in the mount command.

Use this instead: ```
sudo mount -t vfat -o umask=0000,uid=yourname,gid=users,utf8=true /dev/sdc1 /media/winfiles/
```In reality the owner can be root or yourname or anyone. FAT32 doesn't support ownerships at all. The Linux devs have made an overlay that makes it appear that ownership is supported but under the covers all files remain world writeable at drwxrwxrwx. They just temporarily behave as if they belong to a user and a group. When the drive is unmounted, that all falls away again until the next mount.

Now if you want that drive to mount at boot time the line in fstab would be this:
> /dev/sdc1 /path_to/mount_point   vfat   uid=your_name,gid=users,utf8=true 0 0That will make the permissions drwxr-xr-x IIRC with owner yourname:users. You can add a mask like 0000 if you wish but there's no real point if it's made in your username.
Tip: you can make /path_to/mount_point a directory in your home territory of you like; e.g. /home/yourname/fatfiles

---

