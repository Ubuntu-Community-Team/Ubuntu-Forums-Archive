---
title: "Writting to a network share"
date: 2006-07-09
forum: Networking &amp; Wireless
---

### Post by ashrack on 2006-07-09
The only way Im able to write to my network share is by using the following in fstab:
```
//192.168.0.1/d /media/d	cifs	user=tom,pass=****,uname=1000,users	0    0
```
Unfortunetly that allows complete write access to only one user.
BUt I would need full write access to all of the users on the machine!

So I tried the following line:
```
//192.168.0.1/d /media/d	cifs	user=tom,pass=****,nocase,file_mode=0777,dir_mode=0777	0	0
```
But that only allows copying of files. But if I copy a directory which has subdirectories to this shared drive than I get permission error.

ps. the network share has Win2k3 SERVER

EDIT:
Found the sollution. I had to add the thing in red:
> //192.168.0.1/d /media/d	cifs credentials=/root/.smbserver,[COLOR="Red"]noperm[/COLOR],nocase,file_mode=0777,dir_mode=0777		0	0

---

