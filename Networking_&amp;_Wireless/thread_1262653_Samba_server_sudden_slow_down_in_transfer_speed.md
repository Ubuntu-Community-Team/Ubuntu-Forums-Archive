---
title: "Samba server sudden slow down in transfer speed"
date: 2009-09-10
forum: Networking &amp; Wireless
---

### Post by seshomaru samma on 2009-09-10
I'm running a Samba file server on Ubuntu intrepid , 
samba version 2:3.2.3
 It was working fine for almost a year but recently all clients (Ubuntu, Xp and Mac) report extremely slow transfer speed. Even browsing directories take a long time. I don't know why caused this sudden change, I havent updated anything, didn't change the network configuration or hardware. The router is working properly and internet speed is good. Top doesn't show any extra activity on the server side, CPU usually at 5% or less. 
I have looked at the samba files and I get some errors which I couldn't google out , like this:
```
"[2009/09/10 16:17:46,  0] smbd/trans2.c:call_trans2qfsinfo(2562)
  call_trans2qfsinfo: not an allowed info level (0x102) on IPC$."
```

this is my smb.conf:
```
[public]
comment = Public Folders
path = /media/fatfiles
public = yes
writable = yes
create mask = 0777
directory mask = 0777
force user = nobody
force group = nogroup

[teachers]
comment = Public Folders
path=/win/Teachers
public = yes
writable = yes
create mask = 0777
directory mask = 0777
force user = nobody
force group = nogroup

[pictures]
comment = Public Folders
path=/win/Pictures
public = yes
writable = yes
create mask = 0777
directory mask = 0777
force user = nobody
force group = nogroup

[Resources]
comment = Public Folders
path=/win/Resource
public = yes
writable = yes
create mask = 0777
directory mask = 0777
force user = nobody
force group = nogroup


smb ports = 139

```

any ideas?

---

### Post by seshomaru samma on 2009-09-12
It turned out the for some reason the entry for my default gateway changed into 0.0.0.0 . Don't know why.
Once I changed it back to the normal address everything was fine.
The error had nothing to do with it.

---

