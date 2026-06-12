---
title: "Problem with samba user config"
date: 2012-02-01
forum: Networking &amp; Wireless
---

### Post by Martur on 2012-02-01
I have a samba share for user1 that works with "security = user" and user map file. User1 owns the share and is in the group users. Recently I added user2 who should be able to read the share of user1. So I set the group permission for users to read, added user2 to this group and created with  
```
smbpasswd -ae user2
```a samba user2. I also mapped the samba username to the linux username in /etc/samba/smbusers.

However, I cannot login with user2.

This is the output from the log file when trying to connect with user2.

```
[2012/02/01 11:27:35.069105,  1] smbd/service.c:678(make_connection_snum)
  create_connection_server_info failed: NT_STATUS_ACCESS_DENIED

```What to do?

---

### Post by Martur on 2012-02-02
Found the solution:
During my extensive try and error journey I left by mistake the entry ```
valid users = user1
```
in smb.conf. After adding user2 the problem was solved.

---

