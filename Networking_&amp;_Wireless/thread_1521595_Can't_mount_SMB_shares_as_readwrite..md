---
title: "Can't mount SMB shares as read/write."
date: 2010-07-01
forum: Networking &amp; Wireless
---

### Post by seshomaru samma on 2010-07-01
I have a strange problem . We have a network with several computer. We have two file servers (don't ask why) an Ubuntu and an XP as well as many clients. Setting shares on Ubuntu was easy and all clients can see them read and write. but I can't get the Ubuntu clients to see the SMB shares on the XP properly.
This is my fstab:
```
 //192.168.0.100/resources   /media/resources smbfs iocharset=utf8,credentials=/home/boss/.smbcredentials,dmask=775,gid=1009 0 0     
    //192.168.0.9/summer       /media/summer   smbfs  iocharset=utf8,credentials=/home/boss/.smbcredentials1,dmask=775,gid=1009 0 0

```
192.168.0.100 is the Linux server
192.168.0.9 is the XP server
I have two smbcredentials files cause each server has a different admin password
But when the shares are mounted the Linux share ("resources") mounts as read/write while the XP share ("summer") mounts as read only.
Here are the permission before they are mounted:

```
drwxr-xr-x 2 root root 4096 2010-05-25 13:19 resources
drwxr-xr-x 2 root root 4096 2010-06-30 15:10 summer
```
but after they are mounted the permissions change :
```
drwxrwxrwx 1 root 1009    0 2010-06-30 15:50 resources
dr-----rwt 1 root 1009    0 2010-07-01 11:53 summer
```
why is that? what can i do to fix it?
I suspect that my smbcredentials file is wrong , but i put in the XP administrator name and password, in teh same way i did for the Linux server.
Ubuntu client is 9.10 if that's important.

---

### Post by byStanderone on 2010-07-01
...it may have something to do with ntfs, the xp server is on an ntfs format. there may be a need for the ntfsprog / ntfs-3g for read/write access from an ubuntu machine.

---

### Post by seshomaru samma on 2010-07-01
I found the answer [here]("http://ubuntuforums.org/showthread.php?p=9533360#post9533360") 
for some reason i needed to add
```
client ntlmv2 auth = yes
```
to smb.conf 

and mount is with cifs rather than smbfs

why did i need to add that and why does smbfs work with one server but not with the other? who knows......

---

