---
title: "Cannot configure samba"
date: 2011-05-18
forum: Networking &amp; Wireless
---

### Post by roma0607 on 2011-05-18
Hello, 

I have a working (router) LAN connection between two Windows computers. I want to add a Ubuntu 10.04 laptop to this LAN. I read that SAMBA is indispensable for that. I can't configure /etc/samba/smb.config correctly. It still doesn't work. Connect with server --> Windows share | 192.168.0.1 "Cannot show address smb://192.168.0.1/, cannot get the list of available resources". Ping is fine.

this is a testparm: 
```

Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[workspace]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
    workgroup = MSHOME
    server string = %h server (Samba, Ubuntu)
    security = SHARE
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
    usershare owner only = No
    panic action = /usr/share/samba/panic-action %d
    read only = No

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

[workspace]
    path = /home/roma/workspace
    guest ok = Yes


```P.S. actually, I need to access the printer, connected with Win7 computer.

Thank you for your attention.

---

### Post by dandnsmith on 2011-05-19
Not entirely sure what is what here.
Is the printer on the Win7 computer?
Have you defined it as shareable?
Have you created any shares on the Ubuntu machine, as they don't show in your testparm (apart from workspace)?
Which PC is 192.168.0.1 Here - Win7 or ubuntu?

---

### Post by roma0607 on 2011-05-19
The printer is on the Win7 computer. I think it is shareable because other Windows computers prints well.
I haven't created any other shares on Ubuntu. 
192.168.0.1 is the Win7 ip (nslookup on cmd.exe).

Thank you.

---

### Post by roma0607 on 2011-05-20
I solved the problem using the simple step-by-step guide 
[https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html)

Big thanks to the creators of this manual. The basic configuration is that what I needed. It  works!

testparm (working) result:
```

Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[workspace]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
    server string = %h server (Samba, Ubuntu)
    security = SHARE
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
    usershare owner only = No
    panic action = /usr/share/samba/panic-action %d
    read only = No

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

[workspace]
    comment = Ubuntu File Server Share
    path = /home/roma/workspace
    create mask = 0755
    guest ok = Yes


```

---

