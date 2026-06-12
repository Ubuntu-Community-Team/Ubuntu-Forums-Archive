---
title: "can't get file sharing over wlan working"
date: 2010-05-23
forum: Networking &amp; Wireless
---

### Post by aaron_the_dude on 2010-05-23
Ok, I have a desktop and laptop both running ubuntu 10.04.  I have them going through a wireless router, the desktop is wired of coarse.  I installed just about all the samba packages in synaptic that have the little ubuntu symbol next to them on both desktop and laptop except the Kde and document packages.  I installed the two necessary packages to enable personal file sharing to work.  But I can't seem to access files back and forth from these computers.  Please help.

---

### Post by tad1073 on 2010-05-23
open a terminal and type in ```
testparm
```, that will show your smb.conf configuration in the terminal. Copy and paste it with your next post.

---

### Post by Morbius1 on 2010-05-23
>  I installed the two necessary packages to enable personal file sharing  to work.  But I can't seem to access files back and forth from these  computers.Just so everyone understands what your talking about, you're talking about "Personal File Sharing" right. The thing that is disabled by default until you install two apache packages? That's not Samba.

---

### Post by aaron_the_dude on 2010-05-23
Morimbus1-  Yes, "Personal File Sharing" under system>preferences.  I didn't know for sure what is was, I've been trying everything though.

tad1073-  Ok, I'm gonna post the ones to both the desktop and laptop running ubuntu 10.04.

Desktop:

```
aaron@Mine:~$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[aaron]"
Processing section "[test]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
    workgroup = AARON
    server string = %h server (Samba, Ubuntu)
    encrypt passwords = No
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

[aaron]
    comment = Aaron's Desktop
    path = /home/aaron
    read only = No
    guest ok = Yes

[test]
    path = /home/USERNAME/test
    valid users = USERNAME
    read only = No
    guest ok = Yes

```
Laptop:

```
aaron@The-Shiz:~$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

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

```

---

### Post by Morbius1 on 2010-05-23
> [aaron]
    comment = Aaron's Desktop
    path = /home/aaron
    read only = No
    guest ok = Yes

[test]
    path = /home/USERNAME/test
    valid users = USERNAME
    read only = No
    guest ok = YesYou're allowing guest write access for both of those shares ( BTW - Do you really really want guest access to your home directory ?). I'm guessing you didn't modify the linux file permissions to allow "others" to write access to the folder. Samba says come on in - Linux itself says no you can't.

---

### Post by tad1073 on 2010-05-23
your laptop is not apart of any workgroup, add
```
workgroup=AARON
```

---

