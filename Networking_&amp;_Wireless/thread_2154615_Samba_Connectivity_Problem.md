---
title: "Samba Connectivity Problem"
date: 2013-06-15
forum: Networking &amp; Wireless
---

### Post by Deniz343 on 2013-06-15
Hi guys,

I have connectivity problem with samba service as when I'm copying a large file or a lot of files at the same time to any samba share on windows disconnects from samba while copying those files. This is very annoying. I wish you could help me solve this problem.

Ubuntu 12.04.2
Samba version 3.6.3

testparm -s
```
Load smb config files from /etc/samba/smb.confrlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[YouTube]"
Processing section "[Downloaded Torrents]"
Processing section "[TV Shows]"
Processing section "[Movies]"
Processing section "[Pictures]"
Processing section "[Control Unit]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
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
    idmap config * : backend = tdb


[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No


[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers


[YouTube]
    comment = Youtube
    path = /home/deniz/Samba/YouTube
    force user = deniz
    read only = No
    create mask = 0755
    guest ok = Yes


[Downloaded Torrents]
    comment = Torrents
    path = /home/deniz/Downloads/Torrents
    force user = deniz
    read only = No
    create mask = 0755
    guest ok = Yes


[TV Shows]
    comment = TV Shows
    path = /media/Entertaiment/TV Shows
    force user = deniz
    read only = No
    create mask = 0755
    guest ok = Yes


[Movies]
    comment = Movies
    path = /media/Entertaiment/Movies
    force user = deniz
    read only = No
    create mask = 0755
    guest ok = Yes


[Pictures]
    comment = Pictures
    path = /home/deniz/Samba/Pictures
    force user = deniz
    read only = No
    create mask = 0755
    guest ok = Yes


[Control Unit]
    comment = Install Control Unit
    path = /home/deniz/Samba/ControlUnit
    force user = deniz
    read only = No
    create mask = 0755
    guest ok = Yes



```

Best Regards

---

