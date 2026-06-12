---
title: "How Do I Set Password for Shared Folders"
date: 2011-12-04
forum: Networking &amp; Wireless
---

### Post by Lutalo on 2011-12-04
Ok First, I'm not sure which network client I'm using, but its the default one that came with 11.04 where all you do is navigate to the folder, right click and hit 'sharing options'.

Here's the issue:

1) User has two Ubuntu computers, both on 11.04; 
2) User can successfully navigate to shared folders on both laptops
3) When User attempts to access shared folders, the password does not validate.
4) User was not able to change/set password for shared folders and was using admin password. 
5) User would like to know how to specify password for shared folders or which password to use.


Additional info: Setting the sharing option to guest will work around the password. I'd rather not do this for security purposes as I need to set write permissions to the folder.

---

### Post by Morbius1 on 2011-12-04
** You have to create a user on the server first. If the only reason for that user is for sharing across the lan then create him this way:

Let's assume the remote user's name is morbius:
```
sudo useradd -s /bin/true morbius
```This will create a user account that has no home directory or login capabilities on the machine itself.

** Then create a samba password for that user:
```
sudo smbpasswd -a morbius
```It will ask you for sudo's password first and then morbius' samba password. This is the password that morbius will use to connect to your share.

---

### Post by Lutalo on 2011-12-05
Thank you, 

Part of the problem was that I set passwd on this machine but not the other doh

---

