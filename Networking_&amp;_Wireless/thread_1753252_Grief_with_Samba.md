---
title: "Grief with Samba"
date: 2011-05-08
forum: Networking &amp; Wireless
---

### Post by don644 on 2011-05-08
I recently replaced my Ubuntu Desktop with Ubuntu Server 10.04. I've installed Samba so I can share files with my Mac across my network. 
On the desktop system, Samba was working great but on the server I'm having connection problems from the  Mac or Windows machines. I keep getting "connection refused" on the Mac and I'm at the end of the road with ideas. I've checked permissions, changed my smb password, etc, but still no luck.

Any ideas anyone?:(

---

### Post by Morbius1 on 2011-05-08
The first step is to post the output of the following command so people here can see how your samba server is set up:
```
testparm -s
```

---

### Post by don644 on 2011-05-08
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[drives]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    comment = Home Directories
    valid users = %S
    create mask = 0775
    directory mask = 0700

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[drives]
    comment = Drives on Thor
    path = /mnt/
    read only = No
root@Thor:~#

---

### Post by Morbius1 on 2011-05-08
Just to make sure I understand this:
> [drives]
    comment = Drives on Thor
    path = /mnt/
    read only = NoBy default /mnt is owned by root with permissions of 755 so all of the remote users may be able to access the contents of /mnt but what are the permissions of it's contents:
```
ls -al /mnt
```All of the subdirectories are going to have to have 777 permissions unless you've done some creative permissions.

> comment = Home Directories
    valid users = %S
    create mask = 0775
    directory mask = 0700I don't know if that's a typo or a mistake but that looks like the contents of a [homes] share. Problem is it's missing it's tag. It should read:
> [homes]
comment = Home Directories
     valid users = %S
     create mask = 0775
     directory mask = 0700That lets the system know that you are attempting to share local users home directories.

---

### Post by don644 on 2011-05-08
Thanks so much Morbius1, you saved me. It's incredible what a second set of eyes can do for ya.
Everything is working just fine now.

-Don

---

