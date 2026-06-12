---
title: "Write Only Permissions not working"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by new2linux09 on 2009-01-28
Hello all,

I am having trouble with public file sharing permissions. I have a xubuntu box set up with file sharing and can successfully see it from XP Pro. I can also successfully change folder permissions to read only and read/write with chmod 777. Read/write permission allows files to be added from XP Pro.I have tried several different permission settings but each time the write only permission does not grant access from the XP Pro box. 

Anyone know what could be causing this? The write only permissions I have tried are 722 and 733.  Below is my smb.conf file for the share:

[public]
comment = Public Folder
path = /home/public
writable = yes
create mask = 722
directory mask = 722
force user = nobody

nobody is activated and password is null.

---

