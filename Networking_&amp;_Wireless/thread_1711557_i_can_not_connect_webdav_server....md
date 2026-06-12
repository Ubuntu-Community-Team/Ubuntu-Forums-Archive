---
title: "i can not connect webdav server..."
date: 2011-03-21
forum: Networking &amp; Wireless
---

### Post by donlet on 2011-03-21
Hi...
 
i used webdav server from WIN 7 (IIS 7.5 + WEBDAV).
my server used anomymous auth...
 
i connected server using windows explorer (WIN 7, XP)
net use Z: [http://xxxxx](http://xxxxx) user:xxxx
 
Good!!!
 
But...
 
i can not connected ubuntu... (9.04, 10.10)
 
$ sudo mount.davfs 'http://xxx.xxx.xxx.xxx/xxx' '/media/xxx'
  Username: xxxxx
  Password:  
mount.davfs: warning: the server does not support locks
mount.davfs: Mounting failed.
Could not authenticate to server: ignored NTLM challenge, GSSAPI authentication error: An invalid name was supplied: Cannot determine realm for numeric host address

Do you know solution???

---

