---
title: "Windows Server 2003 Share mounting in fstab with cifs"
date: 2009-09-14
forum: Networking &amp; Wireless
---

### Post by shayaknyc on 2009-09-14
Hi All,

I have ubuntu 9.04 installed on an old Dell laptop here at work. This is by far one of the best versions of Ubuntu I have ever worked with and has been exceptionally graceful at being able to be as good as if not better than the windows xp/vista machines here in our office.

We primarily use the windows 2003 server for file-storage purposes (each user has a private folder and full RW access to a "shared" folder).

Anyway, I'm trying to mount these two shares with the user's windows server credentials in fstab.

Here's what I have:

```
#Network Shares
//192.168.1.254/usersdata/rachel /media/P cifs auto,user,isocharset=utf8,credentials=/home/rachel/.smbcredentials,rw,file_mode=0777,dir_mode=0777,nounix,uid=1001,gid=1001 0 0

//192.168.1.254/share /media/S cifs auto,user,isocharset=utf8,credentials=/home/rachel/.smbcredentials,rw,file_mode=0777,dir_mode=0777,nounix,uid=1001,gid=1001 0 0
```

So here's what happens. They both mount beautifully to /media/P and /media/S, however the only user that has full RW access is root. The user for some reason only has RO access.

Any help would be GREATLY appreciated!

Thanks SO SO MUCH!

--S

---

