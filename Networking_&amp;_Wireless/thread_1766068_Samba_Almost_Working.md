---
title: "Samba Almost Working"
date: 2011-05-23
forum: Networking &amp; Wireless
---

### Post by JSHarrison on 2011-05-23
I have Samba setup on Maverick and I'm having some trouble connecting to my shares from a Win 7 box the way I would like.

Issue 1. My Ubuntu box doesn't show up in my workgroup, but I am able to access it through \\server\share

Issue 2. I am only able to connect with \\server\share if my Windows user/pass is exactly the same as my Ubuntu user/pass.

smb.conf has this in it:
```
[global]
    log file = /var/log/samba/log.%m
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    obey pam restrictions = yes
    map to guest = bad user
    encrypt passwords = true
    passwd program = /usr/bin/passwd %u
    passdb backend = tdbsam
    dns proxy = no
    server string = %h server (Samba, Ubuntu)
    unix password sync = yes
    workgroup = WORKGROUP
    os level = 20
    syslog = 0
    panic action = /usr/share/samba/panic-action %d
    usershare allow guests = yes
    max log size = 1000
    pam password change = yes

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

[shares]
    writeable = yes
    valid users = jonathan,@users
    public = yes
    browsable = yes
    path = /home/jonathan/shares
```

Both computers are accessing the network wirelessly over a WRT54G.

Any thoughts would be greatly appreciated.

---

