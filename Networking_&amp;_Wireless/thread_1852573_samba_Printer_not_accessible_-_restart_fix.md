---
title: "samba Printer not accessible - restart fix"
date: 2011-09-30
forum: Networking &amp; Wireless
---

### Post by inforvez on 2011-09-30
hello,

When I first start or reboot my shared printer is not accessable by a windows user - note that i have a shared folder that is accessible.  

All I have to do to get things going is:

> sudo service smbd restart                      my smb.conf look like this:

 > [global]
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
     name resolve order = lmhosts host wins bcast
     printcap name = cups
     dns proxy = No
     usershare allow guests = Yes
     panic action = /usr/share/samba/panic-action %d
 
 [printers]
     comment = All Printers
     path = /var/spool/samba
     create mask = 0700
     guest ok = Yes
     hosts allow = 192.168.
     printable = Yes
     browseable = No
     browsable = No
 
 [print$]
     comment = Printer Drivers
     path = /var/lib/samba/printers
 
 [share]
     comment = Ubuntu File Server Share
     path = /srv/samba/share
     read only = No
     create mask = 0755
     guest ok = Yes
 [printers]
     comment = All Printers
     path = /var/spool/samba
     create mask = 0700
     guest ok = Yes
     hosts allow = 192.168.
     printable = Yes
     browseable = No
     browsable = Noi have removed winbind but didn 't resolved my problem.

Any ideas?

thanks
[I]
(i have already post this problem in thread 1749823, but because it is marked as solved by the owner, i have decided to put it as a thread. hope i have done nothing wrong)[/I]

---

### Post by inforvez on 2011-10-10
Sorry for bumping again.  

To summarize the problem: After a boot or reboot I cannot share my printer with windows computers.  

If I run:

 >  sudo service smbd restart 

Everything works fine until my next boot/reboot.

---

### Post by kamaji792 on 2011-10-10
I have never really nailed down printer sharing with Samba working in a mixed environment of Ubuntu and Win boxes.  In the end I just setup CUPS on the server and do everything directly through that.

The main trick is to allow CUPS on the server to be manageable from one of the clients.

Sadly I have not found a good one size fits all HowTo but a good starting point is:

[http://ubuntuforums.org/showthread.php?t=310450]("http://ubuntuforums.org/showthread.php?t=310450")

Good luck - k

---

