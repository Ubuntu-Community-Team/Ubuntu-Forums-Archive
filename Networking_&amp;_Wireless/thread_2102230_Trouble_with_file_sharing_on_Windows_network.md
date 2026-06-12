---
title: "Trouble with file sharing on Windows network"
date: 2013-01-06
forum: Networking &amp; Wireless
---

### Post by Lloydb39 on 2013-01-06
Using 12.04 on a homebuilt AMD machine. Installed Samba so I could access my Ubuntu files over on my Windows 7 machine. (I already can read the Windows files on the Linux machine.) The computer shows in Windows Explorer but when I try to access the two folders I have marked for sharing in Ubuntu, it won't work. I get the "can't access" message, which doesn't tell me why. Is there a way to diagnose and fix this?  I've searched but can't find a fix -- at least not one I can understand.

---

### Post by Morbius1 on 2013-01-06
It may not be a Samba issue it may be a Linux permissions issue. But first we need to see how you are set up. Please post the output of the following commands:
```
testparm -s
```
```
net usershare info --long
```

---

### Post by Lloydb39 on 2013-01-07
lloyd@linux:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
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

and also 

lloyd@linux:~$ net usershare info --long
[Pictures]
path=/home/lloyd/Pictures
comment=
usershare_acl=Everyone:R,LINUX\lloyd:F,
guest_ok=n

[Documents]
path=/home/lloyd/Documents
comment=
usershare_acl=Everyone:R,LINUX\lloyd:F,
guest_ok=n

---

### Post by Morbius1 on 2013-01-07
In both cases you created shares that require user credentials to access:
> [Pictures]
path=/home/lloyd/Pictures
comment=
usershare_acl=Everyone:R,LINUX\lloyd:F,
[COLOR=Blue]**guest_ok=n**[/COLOR]So you have 2 choices depending on what your original intent was:

[1] Make the share guest accessible.

Go back into Nautilus and make sure "Guest Access" is checked.

[2] Create a new user on your Ubuntu machine that matches the name of the user that you want to allow access to that share. Then add that user to the samba database:
```
sudo smbpasswd -a user-name
```

---

