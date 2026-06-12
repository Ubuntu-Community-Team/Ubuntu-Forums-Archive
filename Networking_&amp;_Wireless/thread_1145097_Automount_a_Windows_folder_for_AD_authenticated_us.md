---
title: "Automount a Windows folder for AD authenticated user"
date: 2009-05-01
forum: Networking &amp; Wireless
---

### Post by ddice on 2009-05-01
Ok, I'm a very newbie Linux user, we're almost 99.99% Windows only. However, I'm trying to learn to use Ubuntu for students. 
 
I've got windows auththentication working fine using likewise-open (great article [http://anothersysadmin.wordpress.com/2008/04/06/howto-active-directory-authentication-in-ubuntu-804/](http://anothersysadmin.wordpress.com/2008/04/06/howto-active-directory-authentication-in-ubuntu-804/))
 
1. I want my users to have their home folder on their windows 2003 or 2008 file & print server automatically mounted as their primary document folder.
 
2. I'd like similarly to grab their windows printer (all are networked printers)
 
3. I'd like the user not to see any reference to the local drives on the Ubuntu box at all, as this would most closely mimic their Windows experience.
 
Can anyone help me out, or guide me to some good articles on doing this? Right now I'm struggling with mounting a shared windows folder at all.
 
Thanks.
 
David Dice
Computer Services Manager
Saskatchewan Rivers School Division # 119

---

### Post by ajgreeny on 2009-05-01
> 1. I want my users to have their home folder on their windows 2003 or 2008 file & print server automatically mounted as their primary document folder.I can't help with your other queries, but for this one, I don't think it is possible to do it that way.  You can put their data, ie docs, photos, music, etc, etc, on the windows file system, and allow them access to that in the /etc/fstab file, but not their home folders as they contain a lot of hidden configuration files which will not work, or not work as expected, anyway, if on a fat32 or ntfs file system.

Think again, I'm afraid.

---

### Post by ddice on 2009-05-01
That's not true.  You are confusing profile folders (which can be the same as home folders, but in our system are not) with home folder which is just a share that contains files.  Yes, some are windows application files, but they show up that way in windows too, so users are going to be able to see them either way.

---

