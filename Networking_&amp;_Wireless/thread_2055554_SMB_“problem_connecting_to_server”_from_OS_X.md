---
title: "SMB “problem connecting to server” from OS X"
date: 2012-09-09
forum: Networking &amp; Wireless
---

### Post by gellpak on 2012-09-09
New 12.04 install, I set up Samba using webmin and all went well.

Attempting to access the server from OS X Mountain Lion. I use "connect to..." and then enter "smb://mediacenter"

I enter my credentials (I've created a unix and samba account to match the username/password on my mac) and am allowed to select the share.

At this point, I receive the error message "There was a problem connecting to the server 'mediacenter'".

Connecting via IP address yields the same issues.

Here are the relevant parts of my smb.conf:

```
#======================= Global Settings =======================

[global]
log file = /var/log/samba/log.%m
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword$
obey pam restrictions = yes
username map = /etc/samba/smbusers
map to guest = bad user
passwd program = /usr/bin/passwd %u
dns proxy = no
server string = %h server (Samba, Ubuntu)
unix password sync = yes
workgroup = workgroup
os level = 20
security = share
syslog = 0
panic action = /usr/share/samba/panic-action %d
usershare allow guests = Yes
max log size = 1000
pam password change = yes

[cerberus]
comment = Cerberus network share
path = /media/cerberus
read only = No  
```

The logfile  /var/log/samba/log.192.168.1.104 is the only one I've found that contains any relevant info, and it repeats this line whenever I make a connection attempt from OS X:

```
[2012/09/09 13:32:44.007936, 0] param/loadparm.c:8843(check_usershare_stat) check_usershare_stat: file /var/lib/samba/usershares/ owned by uid 0 is not a regular file
```

---

