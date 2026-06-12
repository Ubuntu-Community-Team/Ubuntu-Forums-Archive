---
title: "User and Groups miss-match on NFS"
date: 2012-02-25
forum: Networking &amp; Wireless
---

### Post by schworak on 2012-02-25
Server where the NFS is mounted from: Ubunut 11.04 Server 64bit
Client where NFS is being mounted to: Ubuntu 11.10 64bit

I just upgraded the server from 10.04 to 11.04 and this problem started. It was not an issue before the upgrade so I suspect something in the config on the server got changed but I am not sure where to start looking.

I checked both systems and when I run the ID command I have the same user ID on both machines just like I did before the upgrade so both accounts are still in sync right?


When I run LS on the two machines, things are very different.
From the SERVER via SSH:
```

server:/shared_data/web/apache-sites$ id -u glenn
1000

server:/shared_data/web/apache-sites$ ls -l
total 88
-rw-rw-r-- 1 glenn www-data  149 2012-02-08 19:13 000-Default.conf

server:/shared_data/web/apache-sites$ ls -ln
total 88
-rw-rw-r-- 1 1000   33  149 2012-02-08 19:13 000-Default.conf

```From the LAPTOP:
```

laptop:/shared_data/web/apache-sites$ id -u glenn
1000

laptop:/shared_data/web/apache-sites$ ls -l
total 88
-rw-rw-r-- 1 4294967294 4294967294  149 2012-02-08 19:13 000-Default.conf

laptop:/shared_data/web/apache-sites$ ls -ln
total 88
-rw-rw-r-- 1 4294967294 4294967294  149 2012-02-08 19:13 000-Default.conf

```Notice that on the LAPTOP using -l or -ln both give the numeric user and group but it isn't the same as what is on the server and it is wrong!

The strange thing is, I created all of the files from the laptop and as soon as they are created they have this strange user ID and group ID. I can still edit, delete, rename. I just cant change the access rights. chmod, chgrp, chown all fail.

Also, I created these from the laptop which shows the wrong user and group ID info but when I look at the files on the server the user and group IDs are correct.

This is very confusing and very frustrating. Especially it was all working 100% just before the upgrade on the server from 10.04 to 11.04 (yes, I went to 10.10 during the process)

---

