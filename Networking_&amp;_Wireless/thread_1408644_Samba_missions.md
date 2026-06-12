---
title: "Samba missions"
date: 2010-02-16
forum: Networking &amp; Wireless
---

### Post by timvdwest on 2010-02-16
Hi all,

Overview: I have set up a machine running Ubuntu 9.10 x64 as a file/backup server. There are 3 mac clients connected to the network which all need access to a central "work" folder, this is my story.

I'm having endless issues with this ubuntu box I installed, first an issue with the SSH (but that was the router) and now I'm having samba permission issues. I've created a folder on the the server for the users to share their work and they are able to read the folders fine, but cannot create or delete anything (i.e no write permissions).

I've created the share with these details in smb.conf (and tried MANY different configurations all with the same result):

```
[work_share]

comment = Work Folder
path = /media/store01/work_share
#browseable = yes
#read only = no
writeable = yes
create mask = 0777
directory mask = 0777
valid users = @staff
force group = staff
```

This is the latest configuration i've tried, still no luck. I have authentication enabled and the users and smbpasswd's are created and are identical. Here is a listing of the files on the client's share (mac) and some commands I tried:

```
James-iMac:share james$ ls -l
total 2
-rwxrwxr-x 1 james staff 0 Feb 16 01:38 test2.txt
-r--r--r-- 1 james staff 37 Feb 16 02:59 test3.txt
-r--r--r-- 1 james staff 0 Feb 16 02:55 test4.txt
-r--r--r-- 1 james staff 0 Feb 16 02:58 test5.txt
-r--r--r-- 1 james staff 0 Feb 16 12:54 test6.txt
James-iMac:share james$ touch test7.txt
touch: test7.txt: Permission denied
James-iMac:share james$ rm test2.txt
rm: test2.txt: Read-only file system
```

As you see user "james" should be able to delete the file test2.txt, but gives me "Read-only file system" even though I've specified that it's not read only in the smb.conf file.

Here is confirmation that james is in the staff group:

```
wadmin@work-server:/media/store01$ sudo lid -g staff
jamesmentz(uid=1001)
```

Here are the folder permissions on the storage drive of the server:

```
wadmin@work-server:/media/store01$ ls -l
total 108
drwxrwxr-x 2 root staff 16384 2010-02-03 14:54 lost+found
drwxrwxr-x 2113 root staff 81920 2010-02-15 11:55 music_share
drwxrwxr-x 2 root staff 4096 2010-02-16 12:54 work_share
drwxrwxr-x 5 root staff 4096 2010-02-11 09:23 usr_backup
```

As you see the group "staff" should have full access to work_share. I've tried setting permissions to 777 as well, but no change.

If anybody has some insights in to why I'm having this problem, I would eternally in your debt!

UPDATE: I have tried now also give access to all, with full r/w permissions, but I get the same problem - Really have gone through it with a fine-tooth comb and come up short.

---

### Post by suseendran.rengabashyam on 2010-02-17
Hi,

Have you tried upgrading your SAMBA?

I remember a similar thread([http://ubuntuforums.org/showthread.php?t=1404863](http://ubuntuforums.org/showthread.php?t=1404863)) in which the user had upgraded SAMBA and his problem was fixed.

Let me know if this helps.

---

