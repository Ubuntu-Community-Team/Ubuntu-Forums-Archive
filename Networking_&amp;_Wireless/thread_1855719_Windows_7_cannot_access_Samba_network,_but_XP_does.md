---
title: "Windows 7 cannot access Samba network, but XP does"
date: 2011-10-06
forum: Networking &amp; Wireless
---

### Post by odror on 2011-10-06
OS: Ubuntu 11.10, 11.04 and 10.10

I have a linux machine running samba (samba name MY_NACHINE and ip 192.x.x.x)

The windows 7 machine can see MY_NACHINE, but I am getting an access error when I click on the MY_NACHINE icon. on the other hand if I type \\192.x.x.x\ on windows rxplorer everything works well with no errors. I can use the IP, but not the machine name that is detected by windows 7. Windows xp does not have this problem.

When I type ping MY_MACHINE on the linux side I get the correct IP address (192.x.x.x) 

What king of setup I am missing to make it work for windows 7 as it does for windows xp.

My basic setup is

[global]
        workgroup = MY_GROUP
        server string = %h server (Samba, Ubuntu)
        interfaces = eth0, lo
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
        unix extensions = No
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        wide links = Yes


[dir]
        path = /home/MYUSER_ID/dir
        valid users = ME
        read only = No

---

