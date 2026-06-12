---
title: "Samba privileges problems"
date: 2009-08-18
forum: Networking &amp; Wireless
---

### Post by lucifeer on 2009-08-18
I have a strange problem, I can write and delete some files on a samba share.
I can create files and directories, but if I create a directory and then I create a file inside that directory I can't remove it. But I can remove files and directorys directly at the shared folder.

```
lucifeer@lucifeer-laptop:/home/serverstorage$ ls -l
totalt 0
drwx------ 2 lucifeer lucifeer 0 2009-08-17 19:07 lost+found
lucifeer@lucifeer-laptop:/home/serverstorage$ mkdir test
lucifeer@lucifeer-laptop:/home/serverstorage$ touch fil1
lucifeer@lucifeer-laptop:/home/serverstorage$ touch test/fil2
lucifeer@lucifeer-laptop:/home/serverstorage$ ls -l fil1 test/fil2
-rw-r--r-- 1 lucifeer lucifeer 0 2009-08-18 09:41 fil1
-rw-r--r-- 1 lucifeer lucifeer 0 2009-08-18 09:41 test/fil2
lucifeer@lucifeer-laptop:/home/serverstorage$ rm fil1
lucifeer@lucifeer-laptop:/home/serverstorage$ rm test/fil2 
rm: kan inte ta bort "test/fil2": Åtkomst nekas
lucifeer@lucifeer-laptop:/home/serverstorage$ 
```


I have a folder over samba mounted with fstab:
```
//nas/storage	/home/serverstorage	smbfs	credentials=/root/.smbcredentials,iocharset=utf8,uid=1000,gid=1000,noauto	0	0
```
But I also tried connecting whru smbclient and the same problem appears aswell.

```
[global]

   workgroup = home
   netbios name = nas
   encrypt passwords = yes
   invalid users = root
   guest account = nobody
   security = user
   unix charset = iso-8859-15
   display charset = iso-8859-15
   dos charset = 850

#### Debugging/Accounting ####
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d

#======================= Share Definitions =======================

[storage]
	path = /home/storage
	browseable = no
	read only = no
	create mode = 0750

```

---

