---
title: "samba username problem"
date: 2011-01-14
forum: Networking &amp; Wireless
---

### Post by mistafeesh on 2011-01-14
EDIT- seems I've posted in the wrong place. Heading over to server platforms!

Hi, I've got a fileserver set up running samba. I currently have to log in by filling in the server name, then a backslash, then the username in the username field. Unfortunately one of the devices I want to connect ( wii media centre on homebrew) doesn't have access to a backslash! Can someone point me in the right direction?

here's a dump from testparm -sp so you know my settings:

Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[homes]"
Processing section "[profiles]"
Processing section "[printers]"
Processing section "[print$]"
Processing section "[www]"
Processing section "[work]"
Processing section "[stuff]"
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

[homes]
        comment = Home Directories
        read only = No
        create mask = 0775
        directory mask = 0775

[profiles]
        comment = Users profiles
        path = /home/samba/profiles
        create mask = 0755
        guest ok = Yes

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[www]
        comment = web server root
        path = /var/www
        read only = No
        guest ok = Yes

[work]
        path = /home/dan/Documents
        read only = No
        guest ok = Yes

[stuff]
        path = /media/STUFF
        read only = No
        guest ok = Yes

---

