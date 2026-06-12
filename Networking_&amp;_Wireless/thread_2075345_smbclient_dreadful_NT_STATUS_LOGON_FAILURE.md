---
title: "smbclient dreadful NT_STATUS_LOGON_FAILURE"
date: 2012-10-23
forum: Networking &amp; Wireless
---

### Post by mvbozkurt on 2012-10-23
I can't login to any samba share (printer/folder) ever since I upgraded to 12.10. I tried all I found on the net even downgraded smb libs and cups but no love. Any one experiencing similar issues ar did please take a look at my configuration and tell me whats wrong I'm going crazy. And the sad part is I can print within virtual OS (windows xp) while damn linux refuses all I tried.

```

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

```

---

