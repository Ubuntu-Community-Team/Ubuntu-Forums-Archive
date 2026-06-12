---
title: "Only root can write to cifs mount"
date: 2012-09-18
forum: Networking &amp; Wireless
---

### Post by ndog on 2012-09-18
Hi All.

I am booting into ubuntu from PE, so a live environment, not installed onto disk

I am having some trouble with mounting a samba share and then writing to it. Since only root user can mount a samba share, eg **sudo mount -t smbfs -o username=user,password=password //10.1.1.2/images /a** Therefore only root can write to the mounted **/a** folder. This means if I want to write to the folder I need to **sudo nautilus /a** and work like that.

This means I cannot use freefilesync to synchronise a folder pair over cifs mounted network share. I even tried **sudo FreeFileSync** however this does not work.

I had to resort to **chmod 777 /a -R** which was the only way to unlock this folder and allow FreeFileSync to sync a local drive to the cifs mounted share.

I wonder is there an easier way, more straight forward way to do this?

Thanks

---

### Post by luvshines on 2012-09-18
Which is the user you are using in the mount command(username=user,password=password) ? Does this user have write permission on that share ?

Since root can mount that doesn't necessitate that only root can write. Read/write to CIFS mount work with the credentials of the user for which the mount was done, 'username=user' in your case.
If this user has the permission to write to that share, your write should succeed

You may also try 'force user' option in smb.conf. Refer to the man page for the details.

---

