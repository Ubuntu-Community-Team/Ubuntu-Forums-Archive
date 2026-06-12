---
title: "NAS Permissions"
date: 2009-08-29
forum: Networking &amp; Wireless
---

### Post by mcc28x on 2009-08-29
Hi,

I'm trying to sort out write access to my nas. I have the following line in /etc/fstab

//192.168.1.50/qmultimedia /mnt/nas/qmultimedia smbfs iocharset=utf8,credentials=/home/mark/.smbcredentials,gid=1003 0 0

I have a group called 'nasqm' with gid=1003 and have made myself a member of the group.

I can't write to drive though, I was hoping someone could help me figure it out?

regards

mark

---

### Post by ahood on 2009-08-29
> **mcc28x said:**
> Hi,

I'm trying to sort out write access to my nas. I have the following line in /etc/fstab

//192.168.1.50/qmultimedia /mnt/nas/qmultimedia smbfs iocharset=utf8,credentials=/home/mark/.smbcredentials,gid=1003 0 0

I have a group called 'nasqm' with gid=1003 and have made myself a member of the group.

I can't write to drive though, I was hoping someone could help me figure it out?

regards

mark

I find that permanently mounting a shared folder on a client machine is very geeky, while simply browsing the same shared folder temporarily is easy as cake.

I have used the syntax you describe, but it was several versions ago. Since Ubuntu 8.04 I have had to replace 'smbfs' with 'cifs' in the fstab line, which still requires the smbfs libraries I believe.

Thus, if your version is relatively recent, may want to try cifs (see below).

> //192.168.1.50/qmultimedia /mnt/nas/qmultimedia cifs iocharset=utf8,credentials=/home/mark/.smbcredentials,gid=1003 0 0

If that doesn't solve the problem, then I would temporarily mount command from the command line.

> sudo mount -t cifs //192.168.1.50/qmultimedia /mnt/nas/qmultimedia -o username=*name*,password=*pw*,users,rw

Note: The command to unmount is sudo umount *localdirectoryname*

If the contents of the shared folder is visible and read/write access from the /mnt/nas/qmultimedia directory, then you know settings on the server are correct and suggests that the smbcredientials file may need to be edited.

I hope the above helps.

If you think that permanently mounting a shared folder should be made easier for users, then consider voting for my solution that appears in my signature below.

---

### Post by mcc28x on 2009-08-29
After reading some other posts then I've changed /etc/fstab to:

//192.168.1.50/qmultimedia /mnt/nas/qmultimedia cifs credentials=/root/.credentials,directio,iocharset=utf8,noacl,noperm,nosetuids,rw

If I browse to network>windows network>workgroup/qnap/qmultimedia I can read and write no problems (group/owner/permissions all shows as unknown)

but

if I try to write to /mnt/nas/qmultimedia I get permissions error message permissions are -rw-r--r-- in nautilus window.

I need to be able to write to the mount point for recording CD's etc. It's driving me nuts, so yes a simpler system would be great!

---

### Post by mcc28x on 2009-08-29
Got it working now, have the above in /etc/fstab and on the nas I added myself with read/write access.

cheers

---

