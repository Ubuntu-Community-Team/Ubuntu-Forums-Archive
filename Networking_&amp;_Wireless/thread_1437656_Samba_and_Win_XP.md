---
title: "Samba and Win XP"
date: 2010-03-24
forum: Networking &amp; Wireless
---

### Post by zoomiest on 2010-03-24
I have a family file server that is Ubuntu 9.x with the latest Samba, and I have the weirdest permissions issues. What am I missing:

[LIST]
[*]Family desktop is win xp
[*]When my wife and I log in, we can see all the network shares on Samba - no problem.
[*]When my children log in they cannot see any network shares
[*]Everyone is a member of the group that owns the directory.
[*]I have checked that the passwords on the XP desktop and Samba do match.
[/LIST]

_Group Membership is as follows:_
```
allan@GraniteMount:/shares$ members users
laura jr elizabeth steven gordon EPJ
allan@GraniteMount:/shares$ members speech
allan laura jr paul steven elizabeth
allan@GraniteMount:/shares$ members music
allan laura jr paul steven elizabeth
allan@GraniteMount:/shares$ members users
laura jr elizabeth steven gordon EPJ

```

_The share permissions look like this:_
```
drwxr-xr-x  11 root  root     4096 2009-12-26 09:24 .
drwxr-xr-x  22 root  root     4096 2010-02-05 07:05 ..
drwxrwxr--  13 allan users    4096 2010-02-04 05:57 fam_library
drwxrwxr--   3 allan jr       4096 2010-01-01 09:32 j_files
drwxrwxr--  55 allan laura   12288 2010-03-23 23:04 l_files
drwxrwxr--  61 allan music    4096 2010-03-15 11:34 music
drwxrwxr--   5 allan paul     4096 2010-02-22 16:39 p_files
drwxrwxr-- 473 allan users   28672 2010-02-16 11:06 pictures
drwxrwxr--   4 allan resumes  4096 2010-02-27 15:41 resumes
drwxrwxr--  41 allan speech   4096 2010-02-17 19:58 speech
drwxrwxr--  44 allan users    4096 2010-03-22 07:24 videos

```

So, specifically, JR and Paul can't access anything on the network. When I try to go through Win XP Network neighborhood, it  just recognizes them as guests, and when I type in their passwords, it won't let them on - but my wife and I can log in and get everything. Is this a Windows problem?

Any help would be terrific!

---

### Post by Iowan on 2010-03-24
Another opportunity to show how little I know about Samba...
How do elizabeth, steven, gordon, & EPJ work - do they have access/problems? If you've verified the passwords are the same, I presume that means you've verified that the usernames exist, too (Samba and Linux).

---

### Post by jrssystemsnet on 2010-03-24
What do the share definitions look like in /etc/samba/smb.conf?

The permissions you showed are the folder permissions in the filesystems, which are only part of the story - the other part are the share permissions for Samba.

Also, have you created Samba accounts for these users?

**sudo pdbedit -w -L** will give you a list of the users who actually have Samba accounts on the system.  (System users do not necessarily have Samba accounts - you have to create the matching Samba account for a system user with **smbpasswd -a username** or they can't log in using Samba.)

---

