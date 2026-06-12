---
title: "home folder on server returns error &quot;Failed to mount Windows share&quot;"
date: 2010-04-03
forum: Networking &amp; Wireless
---

### Post by walter_j on 2010-04-03
I set up a home server (ubuntu 9.10 server) where i want to back up data to a home directory. I can ssh into the server and see the home drectory, and i can rsync files to the directory, but i can't browse the directory with nautilus from my desktop pc (karmic). When I select the homes folder in nautilus, i get the error "Failed to mount Windows share"

I ran adduser and smbpasswd -a and added users to the server. I want windows users to be able to access their home directories too.

testparm -s (on server)
global]
        server string = %h server (Samba, Ubuntu)
        map to guest = Bad User
        obey pam restrictions = Yes
        passdb backend = smbpasswd
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword$
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d

[homes]
        comment = Home Directories
        valid users = %S
        read only = No
        create mask = 0700
        directory mask = 0700

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No
        browsable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[Share]
        path = /home/public
        read only = No
        guest ok = Yes


Note the [Share] works great. not the [homes] though. I spent waay too much time on this and am totally frustrated. Any help would be appreciated.

SOLVED
Found that the problem is with nautilus, which doesn't work with networks very well. Nor does Gnome Commander. Krusader worked as expected, and quickly brought up all shares using "net connection". Windows vista had no problems with the shares.

---

