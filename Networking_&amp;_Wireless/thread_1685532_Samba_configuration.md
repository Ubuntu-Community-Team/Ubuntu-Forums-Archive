---
title: "Samba configuration"
date: 2011-02-10
forum: Networking &amp; Wireless
---

### Post by jestinjoy on 2011-02-10
My smb.conf is given below

```
[global]
workgroup = WORKGROUP
netbios name = PIRATEBAY
wins support = yes
server string = %h server (Samba %v)
log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
security = share
guest account = nobody
map to guest = bad user


[Movies-1]
path = /media/Store/movies
comment = Movies
read only = Yes
guest ok = Yes
available = yes
browsable = yes
public = yes
writable = no
```

Though others could easily access my shares in a passwordless way, I am being aksed for password when I try to access their shares. They are running windows machines. I could easily access their shres without password from my windows setup.

Please help

---

### Post by headvampyre@hotmail.co.uk on 2011-02-11
Set:
security = user
To:
security = share

then press ALT+F2 -> check "Run in Terminal" and type 
smbpasswd -a YOURUSERNAME
type the password for the account, run
service samba restart or
service smbd restart && service nmbd restart
Hope this works

---

