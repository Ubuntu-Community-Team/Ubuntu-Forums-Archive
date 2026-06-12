---
title: "Samba AND OR Permissions issue.."
date: 2011-07-30
forum: Networking &amp; Wireless
---

### Post by Calandric on 2011-07-30
First, I hope I posted this in the right forum, if not please forgive me and direct me to the correct one.

Now, for the sake of comparison I have 2 drives that are similar in usage, only difference is mount point, and size. I created them both at the same time, configured smb.conf at the same time, etc and have had no problems out of one, and constantly out of the other. I'm thinking it is a configuration error or permissions issue. Either way, I'm about to pull my hair out.

Drive one (D1 from now on) I can get into from a windows computer using 'Network Places' or what have you, no password/username needed. Can read. Can write. The second drive, however (D2 from now on) I can see via Network Places, but when trying to enter it asks for username/password. After some searching the internet I found that using workgroup\nobody (see smb.conf, default setting at the end of post) will allow me to Read and Write. 

When writing to D1 or D2 it creates files as user/group nobody:nogroup (again see smb.conf, default setting) which is not a BIG problem, merely an annoyance. I'd like D2 to act like D1 in not wanting a username/password and to behave as far as permissions go since I had to set the base mounting point of both D1 and D2 to 777 in order for them to work properly. 

Please, someone with more knowledge than I, offer up some assistance. Thank you before hand!

```
[global]
        workgroup = workgroup
        server string = %h server (Samba)
        log file = /var/log/samba/log.%m
        max log size = 1000
        syslog = 0
        panic action = /usr/share/samba/panic-action %d
        dns proxy = no
        security = share
;       encrypt passwords = yes
;       guest ok = no
;       guest account = nobody

[Vault]
        comment = Vault
        path = /home/beast/Vault
        public = yes
        writable = Yes
        create mask = 0777
        directory mask = 0777
        force user = nobody
        force group = nogroup

[Slave]
        comment = Slave
        path = /home/beast/Slave
        public = yes
        writable = Yes
        create mask = 0777
        directory mask = 0777
        force user = nobody
        force group = nogroup

```

---

### Post by Morbius1 on 2011-07-30
The only problem with your description is that no one knows the relationship between D1, D2, Vault, and Slave.

Need to know things like permissions of each share:
```
 ls -al /home/beast/Vault
``````
 ls -al /home/beast/Slave
```Anywho, If "beast" is an actual user name and "beast" has access to Vault and Slave locally and if there is any connection between D1 and D2 to Vault and Slave, then the solution is simple:
```
[Vault]
        comment = Vault
        path = /home/beast/Vault
        public = yes
        writable = Yes
        force user = beast

[Slave]
        comment = Slave
        path = /home/beast/Slave
        public = yes
        writable = Yes
        force user = beast
```

---

### Post by Calandric on 2011-07-30
Hrm, of course, my apologies. D1 (Slave) appears to work fine. D2 (Vault) only somewhat works fine.

Vault Permissions:

```
total 152
drwxrwxrwx 17 beast  beast    4096 2011-07-30 17:51 .
drwxr-xr-x 38 beast  beast    4096 2011-07-30 17:45 ..
drwxrwxrwx  3 beast  beast    4096 2011-07-03 18:38 Folder
drwxrwxrwx  6 beast  beast    4096 2011-07-03 18:43 Folder
drwxrwxrwx 17 beast  beast    4096 2011-07-03 18:50 Applications
drwxrwxrwx  2 beast  beast    4096 2011-07-03 18:50 Book
drwxrwxrwx  7 beast  beast    4096 2011-07-03 18:50 C++
drwxrwxrwx  2 beast  beast    4096 2011-07-03 14:54 dbs
drwxrwxrwx 13 beast  beast    4096 2011-07-16 19:43 DeVry
drwxrwxrwx 39 beast  beast    4096 2011-07-03 19:46 Downloads
drwxrwxrwx  2 beast  users   16384 2011-07-03 13:28 lost+found
drwxrwxrwx  4 beast  beast    4096 2011-07-03 14:09 My Music
drwxrwxrwx  6 beast  beast    4096 2011-07-17 16:30 My Pictures
drwxrwxrwx  4 beast  beast    4096 2011-07-21 22:14 MythTV
-rwxrw-rw-  1 nobody nogroup   622 2006-04-22 11:28 filename.ini
drwxrwxrwx  2 nobody nogroup 32768 2011-07-30 16:45 override
drwxrwxrwx  2 nobody nogroup 45056 2011-07-30 16:46 portraits
drwxrwxrwx 25 beast  beast    4096 2011-07-03 19:54 www

```Slave Permissions:

```
total 624
drwxrwxrwx  8 beast beast   4096 2011-07-30 17:55 .
drwxr-xr-x 38 beast beast   4096 2011-07-30 17:45 ..
drwxrwxrwx 11 beast beast   4096 2011-01-24 21:43 Applications
drwxrwxrwx  2 beast beast   4096 2011-01-24 20:58 Book
drwxrwxrwx 13 beast beast   4096 2011-07-29 07:03 Downloads
drwxrwxrwx  2 beast beast  16384 2011-01-24 20:04 lost+found
drwxrwxr-x 32 beast beast   4096 2011-07-30 18:01 Folder
drwxrwxrwx 25 beast beast   4096 2011-01-24 21:09 www

```Also, relative FSTAB entry:

```
##### Mount Local Drives / USB Drives

/dev/sda1 /home/beast/Slave auto rw,user 0 2
/dev/sdb1 /home/beast/Vault auto rw,user 0 3
#/dev/sde1 /home/beast/Ravage auto rw,user,noauto 0 0
/dev/sdd1 /home/beast/Ravage auto rw,user,noauto 0 0

```As for the 'force' user beast and remove the force group, I'll give that a try and see what happens. Thanks for taking notice!

---

