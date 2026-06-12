---
title: "Sharing Folders with Win (Vista and XP)"
date: 2009-05-21
forum: Networking &amp; Wireless
---

### Post by karlytospr on 2009-05-21
Hi all,
 
Im very new to Ubuntu and Linux in general. Nevertheless Im eager to learn it as well as I know Win. However I have an issue that I haven't been able to solve:
 
This is what I want to do:
 
Im using Ubuntu 9.04 to share files in a Windows Network. I want to create user specific folders in it, and that only that user can enter it and write to it. I don't want other users to be able to enter and view the contents of the folders. I was able to create the folders in one general user profile, and I can see the folders from the Win PC, when I click on one of the folders it ask me for a user name and password, (so far so good) Once I entered my user name and password in Ubuntu, I was able to open the folder designated to me, However I was also able to open the rest of the folders which weren't assigned to me. 
 
Question: How can I share the folder exclusively with just one user and not the rest of the folders I have shared in the Ubuntu box?
 
Please advice.

---

### Post by Iowan on 2009-05-21
The "valid users =" option *should* do what you want.  The default /etc/samba/smb.conf file has an example in the [homes] share.

---

