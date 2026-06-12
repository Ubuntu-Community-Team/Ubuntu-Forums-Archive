---
title: "Sharing Ubuntu files on Windows workgroup"
date: 2011-02-05
forum: Networking &amp; Wireless
---

### Post by ConLoco76 on 2011-02-05
[SIZE=3]Hi, 

I've just recently got my samba confg working with a workgroup. I can view/access/modify windows machines on workgroup just fine. 

What I can't do is access shares created on ubuntu desktop. My ubuntu machine appears on Windows Workgroup, but denies to Windows users. 

When I try to create  a share using Folder Sharing, I get this returned to me:

[I]'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. Invalid parameter.
[/I]


Here's by samba config file. ANy help?  THanks for the great support on these forums![/SIZE]

[global]
    workgroup = JANSSEN HOME
    server string = UServer
    encrypt passwords = No
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

---

### Post by Morbius1 on 2011-02-05
You know what's funny is that I can take my working smb.conf file and completely reproduce your error by changing one line to match yours:
```
encrypt passwords = No
```I would change that to:
```
encrypt passwords = Yes
```Save the file and restart samba:
```
sudo service smbd restart
```

---

### Post by ConLoco76 on 2011-02-05
I don't use passwords, but I will try.

---

### Post by ConLoco76 on 2011-02-05
Surprise, surprise, it did work!

Don't understand why, but THANKS!

---

### Post by juliobahar on 2011-03-03
> **Morbius1 said:**
> You know what's funny is that I can take my working smb.conf file and completely reproduce your error by changing one line to match yours:
```
encrypt passwords = No
```I would change that to:
```
encrypt passwords = Yes
```Save the file and restart samba:
```
sudo service smbd restart
```

This worked for me so marvelously. I have my encrypt passwords set to false. Just by changing it to "YES"
```
encrypt passwords = Yes
```
Thank you

---

