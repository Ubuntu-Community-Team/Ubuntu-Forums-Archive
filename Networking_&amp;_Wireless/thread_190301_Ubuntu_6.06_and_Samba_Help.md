---
title: "Ubuntu 6.06 and Samba Help"
date: 2006-06-06
forum: Networking &amp; Wireless
---

### Post by jer2eydevil88 on 2006-06-06
I am new to setting up Samba shares on Linux but I have a limited experience with Linux.  I want to set up two users (administrator = root) and (roomate = limited account) both with passwords that have access on different levels on the two shares I have setup.

I have the drives I want shared already configured in Samba as follows 
```
[share1]
path = /share1
available = yes
browseable = yes
public = yes
writable = yes

[share2]
path = /share2
available = yes
browseable = yes
public = yes
writable = yes
```

Currently no one can connect to the server because I have no users setup correctly.  I would like to make the roomate username only have read and list access to the shares while the administrator account have full access.  If possible I would like to be able to view who is connected to what shares and be able to kick them (like Windows 2003's file server admin console) but thats not important if its not easy to setup.

---

