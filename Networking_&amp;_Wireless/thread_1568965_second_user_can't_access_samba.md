---
title: "second user can't access samba"
date: 2010-09-06
forum: Networking &amp; Wireless
---

### Post by fpdragon on 2010-09-06
Hi!
Sorry to ask but I'm trying to fix this for some days and had no luck.

The goal is the following: I want one samba network share with all my family data. Multiple users should have access to this share from Win7 pcs but not all folders should be access able by everyone. The old windows server managed this by changing ntfs rights for these folders.

I've installed Samba and this recommended gnome utility (Ubuntu 10.4). First for testing I made a samba share with access right for everyone. Everything fine on Win...
Then I only allowed for my user. Also worked after a little bit of playing with the global samba settings and the pw encryption...
Then I created a new ubuntu user and configured a new samba user with the connection to this ubuntu user (like described in many tutorials using the samba config tool). I changed the access right of the samba share to allow the new user also but no connection was possible. At this point the original user was working from the same pc without any problem.

I started thinking of the windows time and decided to search for the file system rights like it was with the ntfs. I'm using ext4 by the way.
I made chmod 777 -R from the new users login... (i'm not sure why there is no user dependency for chmod)
I used chown -R but it seems that there is only one owner allowed so I switched back to my main user...
I installed an additional feature called ACL and was able to set users and groups for the root folder but there is no possibility to recursively change all subdirs. I used such a ACL gui extension for gnome which is in the ubuntu repository to do that. It also wasn't helping for the problem that the new user has no access to the folder (even if I change the rights manually)

I'm very confused right now.
User A & B have access rights at least for the root of the share.
Both users have a ubuntu and a samba account.
Only user A is working with samba.

Please help! I don't want to move back to windows because of such a stupid configuration issue.

---

### Post by Iowan on 2010-09-06
Depending on which method you used to set up the shares, it might be helpful to see your */etc/samba/smb.conf*

---

### Post by fpdragon on 2010-09-07
New information:
I've managed that user B also is able to access the share. This folder has chmod 777 right now...

I tried to change a subdir to 770 and user B is not in the group configured for this folder.

The strange thing is, that i can access to this directory with user A and user B. It seems that samba ignores the UNIX folder/file permissions. How can I change that?

Sorry but I can't show you the config file right now since I am not at home but maybe someone can help anyway.


I've read in the Samba-HOWTO-Collection.pdf the following:
There a 4 types for permissions in samba.
 * UNIX File and Directory Perm.
 * Samba Share Def.
 * Samba Share ACLs
 * MS Windows ACLs through UNIX POSIX ACLs
 
I'm not sure but I think I need the UNIX style for my whish to deny subfolder's access with user B. From the description I think right now I have the Samba Share Def. How can I change that?

please help!

---

