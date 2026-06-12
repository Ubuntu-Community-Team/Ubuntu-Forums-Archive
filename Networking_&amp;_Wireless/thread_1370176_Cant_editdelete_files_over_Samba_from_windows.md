---
title: "Cant edit/delete files over Samba from windows"
date: 2010-01-01
forum: Networking &amp; Wireless
---

### Post by rugbert on 2010-01-01
I just installed Ubuntu server 9.04 and am try to get it all set up but Ive run into a snag with Samba. I cant delete, add, or change files from my windows machine like I could before. Here is my minimalist Samba config that I used on my old ubuntu server:

> 

[global]
        server string = %h server (Samba, Ubuntu)
        security = SHARE
        map to guest = Bad User
        obey pam restrictions = Yes
        passdb backend = tdbsam
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
        invalid users = root

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No

#Shares go here --------------------------------------------

[mnt]
        path = /mnt
        read only = No
        guest ok = Yes
        available = Yes
[music]
        path = /mnt/music
        read only = No
        guest ok = Yes
        available = Yes
[movies]
        path = /mnt/videos
        read only = No
        guest ok = Yes
        available = Yes


Im sure its just one small thing Im forgetting..Its been a while since I played around with my server!

---

### Post by peepingtom on 2010-01-02
You have to set the linux file permissions to be written by "everyone" if you want Samba Guests to be able to write/delete. You can do this in nautilus by selecting "properties" from the context (right-click) menu. Otherwise, use chmod in terminal.

---

