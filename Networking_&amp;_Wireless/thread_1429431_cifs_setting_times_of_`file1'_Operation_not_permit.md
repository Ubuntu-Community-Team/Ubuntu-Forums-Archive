---
title: "cifs: setting times of `file1': Operation not permitted"
date: 2010-03-14
forum: Networking &amp; Wireless
---

### Post by ljubom on 2010-03-14
Hi,

I have a WD MyBook World NAS share mounted with the following options (I tried also other options):

```
 cifs nouser,atime,auto,rw,nodev,noexec,nosuid,nodfs,nounix,guest,uid=0,gid=0,file_mode=0777,dir_mode=0777
```

The cp -a, touch, etc. commands can change the file time if the root is executing the command (means NAS supports time setting), but as an user I can't change the file time - with an exception of changing the time to the current time. For an illustration see below:

```
.../tmp> ls -la
total 0
drwxrwxrwx 1 root root 0 2010-03-14 09:18 ./
drwxrwxrwx 8 root root 0 2010-03-13 22:33 ../
-rwxrwxrwx 1 root root 0 2010-03-14 09:13 file1*

.../tmp> sudo touch -t 199901010101 file1
[sudo] password for user: 

.../tmp> ls -la
total 0
drwxrwxrwx 1 root root 0 2010-03-14 09:18 ./
drwxrwxrwx 8 root root 0 2010-03-13 22:33 ../
-rwxrwxrwx 1 root root 0 1999-01-01 01:01 file1*

.../tmp> touch file1

.../tmp> ls -la
total 0
drwxrwxrwx 1 root root 0 2010-03-14 09:18 ./
drwxrwxrwx 8 root root 0 2010-03-13 22:33 ../
-rwxrwxrwx 1 root root 0 2010-03-14 09:19 file1*

.../tmp> touch -t 199901010101 file1
touch: setting times of `file1': Operation not permitted
```

Any ideas?

Thanks,
ljubom

---

### Post by ljubom on 2010-03-22
No a single idea what is wrong? :-( 

I posted now the same question on [www.linuxforums.org](www.linuxforums.org)

---

### Post by ljubom on 2010-03-23
There are some hints from linuxforums that it could be related to selinux - do we have in ubuntu some "strong" security features? BTW, ```
~> getenforce 
Disabled
~> 
```

---

