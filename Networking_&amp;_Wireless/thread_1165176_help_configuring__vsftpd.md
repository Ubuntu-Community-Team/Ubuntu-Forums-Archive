---
title: "help configuring  vsftpd"
date: 2009-05-20
forum: Networking &amp; Wireless
---

### Post by crash893 on 2009-05-20
I've seen a few writeups but they don't seem to be exactly what i want to do


I have a remote user that needs to dump photos on to our branch server so the branch employees can work on them.


I created a user called ftpuser 


what i would like to happen

1) user logs on with ftpuser /password
2) user only sees the dump directory that hes allowed to see
3) everything he drops in to that folder has full 777 rights
( currently if he or anyone else drops in a file the rights are 600)

4) (not vsftpd related) share that folder with samba so the staff can access it from windows)



With my current config i can connect but with any user on that ubuntu box and see any folder.  also every file i drop shows up as -rw------- but if i select the file from filezilla im allowed to change the permissions all the way up to 777  but i have to do it manually ( something the user shouldn't have to do)



please let me know if you have any ideas

---

### Post by superprash2003 on 2009-05-20
you should consider using gproftpd , it has a GUI

---

### Post by crash893 on 2009-05-20
I would love to but i do all my work remotely ssh useing putty

---

### Post by gpredrag on 2009-05-20
How about combining
file_open_mode
and
anon_umask or local_umask
that should give desired permissions on uploaded files

---

### Post by crash893 on 2009-05-21
so 

file_open_mode=0777
local_umask=077 ???? the documentation is a little lacking

I dont understand why it has all 3 for file open but only 2 levels for the local unmask

shouldnt it be local_mask=0777 too?>


How do you have it in your setup?

Thanks

---

### Post by gpredrag on 2009-05-21
umask defines which permission bits are NOT set, that is masked
file_open_mode defaults to 0666, that is rw for owner, rw for group and rw for others. It can be set to 0777 if you want files to be executable.
But then umask comes to effect to finaly determine which permission bits will be masked, that is NOT set on file. Default local_umask is 077 which does not mask-blocks any permission bits for user (0), blocks all permissions set for group (7) and blocks all permissions set for others (7).
So you probably get rw-------, 0600
My guess is that file_open_mode 0777 and local_umask 000 would give the result.
If ftp users are virtual users I guess you should use anon_umask

My setup is opposite, I needed anonymously uploaded files to be chowned, and not readable by anyone except few local users.

---

