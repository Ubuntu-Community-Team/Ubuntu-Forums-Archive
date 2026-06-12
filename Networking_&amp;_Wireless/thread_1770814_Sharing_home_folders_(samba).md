---
title: "Sharing home folders (samba)"
date: 2011-05-29
forum: Networking &amp; Wireless
---

### Post by drbisio on 2011-05-29
I need help sharing the home directory of my mediacenter pc.

I run xubuntu 10.04 on this machine, so I had to write my own smb.conf file:

[global]
workgroup = ReteDomestica
netbios name = MEDIASERVER
security = USER
smb passwd file = /etc/samba/smbpasswd
encrypt passwords = YES
log file = /var/log/samba/m%.log
max log size = 100
log level = 1

[homes]
comment = cartella utenti
read only = no
browseable = yes
create mask = 0700
directory mask = 0700
valid users = %S

On my desktop PC (ubuntu 10.10) I can see the home folder of the mediacenter, but I cannot open it (unable to mount windows share)

Where's the mistake?

Any help is really appreciated !
thanks a lot!

---

### Post by Morbius1 on 2011-05-29
The [homes] section is a special type of share that creates a share "on the fly" when it's called upon to do so. It usually isn't browseable since it's not something you browse to and access like a normal share.

When a Linux client wants to access the [homes] section it must ask for it explicitly. For example:
```
nautilus smb://192.168.0.100/morbius
```Of course you need to have that username with it's home directory already set up on the server.

---

