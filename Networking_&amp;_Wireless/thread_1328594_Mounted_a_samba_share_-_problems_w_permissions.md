---
title: "Mounted a samba share - problems w/ permissions"
date: 2009-11-16
forum: Networking &amp; Wireless
---

### Post by spaceballl on 2009-11-16
Hi there,
I'm working on writing a script that mounts a samba share, rsyncs a remote folder to the local machine, and then unmounts the share. I've never written shell scripts before so this is a bit of a primer / learning experience for me :D. I'm going to then use this script w/ cron to automate the syncing of my MacBook Pro's (don't hate me!) music to my Ubuntu server.

In any case, that's too much background. Using the following command, I can mount the share no problem...

```
sudo mount -r -t smbfs //10.0.1.100/itunes\ music/ /mnt/test -o user=user,password=pass
```

The issue is that I cannot get into the /mnt/test/ directory unless I use su to become root. Is this a server configuration or does it have to do w/ my local system? Any way to fix this? Woudl be nice if my user could mount SMB shares without having to use sudo... I appreciate the help. Thanks!

---

### Post by doas777 on 2009-11-16
have you tried a userspace or custom mount directory? /mnt is primarily for system-space mounts.

---

### Post by spaceballl on 2009-11-16
Yeah I tried my home directory as well and I had the same issue.

---

### Post by doas777 on 2009-11-16
would a fuse mount work? if it's just a user, then they shouldn't require a system-space mount.

---

### Post by spaceballl on 2009-11-16
> **doas777 said:**
> would a fuse mount work? if it's just a user, then they shouldn't require a system-space mount.
I don't know what a fuse mount is or how it might work in this situation. Googling is not giving me the most easy to understand answers as well. Would appreciate any help in this regard.

---

### Post by doas777 on 2009-11-16
ok, if you, as a normal user, open a nautilus window, and type in:
```
smb://<server>/<share>
``` and press enter, the share should mount to a location in the users home, and place a shortcut to it on your desktop (like with any mount).

fuse is a userspace mounting system, so it is designed to work without admin access.

---

### Post by spaceballl on 2009-11-16
> **doas777 said:**
> ok, if you, as a normal user, open a nautilus window, and type in:
```
smb://<server>/<share>
``` and press enter, the share should mount to a location in the users home, and place a shortcut to it on your desktop (like with any mount).
fuse is a userspace mounting system, so it is designed to work without admin access.
Yes in regard to getting it to work in nautilus, I've done that, and it works without issue. But I'm trying to write a script to mount, rsync, and unmount a share. I'll do some research on fuse, though... Maybe that's what I need..

---

### Post by doas777 on 2009-11-16
usually people use the smbfs or smbclient scripts when writing scripted connections. 
check this out (under manual client configuration): 
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

another thing to look into that may get you more hits than fuse, is gvfs. I think it may have replaced gfuse somewhere along the line.

---

### Post by spaceballl on 2009-11-17
I have figured out a couple things...
1) I don't need to use Samba. I can RSYNC over SSH.
2) If I were to use samba, here's the command to use! (no root needed)

Instead of using...
```
sudo -t smbfs /10.0.1.XXX/share/ /place/to/mount/
```

```
mount.cifs /10.0.1.XXX/share/ /place/to/mount/
```

the command to unmount is...
```
umount.cifs /place/to/unmount/
```

---

### Post by undertakingyou on 2009-11-23
So strange, I have used 
```
sudo mount -t cifs //server/share /mountpoint
```
for a long time. Never have had a permissions problem until today. I am not sure why, but it wouldn't work starting today. 

Changing "sudo mount -t cifs" to "mount.cifs" fixed the issue.

---

