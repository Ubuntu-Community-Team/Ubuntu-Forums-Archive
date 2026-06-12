---
title: "Problem with SAMBA and secondary HDD"
date: 2010-09-27
forum: Networking &amp; Wireless
---

### Post by Maila87 on 2010-09-27
Hi, I successfully installed Samba, but have problem with access to any shared folder on my secondary drive. 

If I try access secondary drive with admin user, everything is fine. If with another account try to access via samba to shared folder on partition with Ubuntu, everything is fine again. 

Every folder has set privileges to read&write to everyone, so shouldn't be problem here. 

Any help welcome :-)

---

### Post by Morbius1 on 2010-09-27
Anyone looking at your question is going to need way more information than you provided. Let's start with the first one:

What method of samba sharing are you using - there are 2. Post the output of the following commands and we can determine that:
```
net usershare info
sudo net usershare info
testparm -s
```

---

### Post by Maila87 on 2010-09-29
Installed by apt-get samba and system-config samba.
Before that tried to set by GADMIN, but with same result  so renewed samba config. Thanks for help!

Result of net usershare infoLoad smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[strizna]"
Processing section "[ucebna]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = SUM
    server string = %h server (Samba, Ubuntu)
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

[strizna]
    path = /media/server/strizna
    valid users = bazinga, samba, scholzova, student
    read only = No

[ucebna]
    path = /media/server/ucebna
    read only = No
    guest ok = Yes
bazinga@server:~$ sudo net usershare info
bazinga@server:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[strizna]"
Processing section "[ucebna]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = SUM
    server string = %h server (Samba, Ubuntu)
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

[strizna]
    path = /media/server/strizna
    valid users = bazinga, samba, scholzova, student
    read only = No

[ucebna]
    path = /media/server/ucebna
    read only = No
    guest ok = Yes
bazinga@server:~$ net usershare info
[strizna]
path=/media/server/strizna
comment=
usershare_acl=Everyone:F,
guest_ok=n

[ucebna]
path=/media/server/ucebna
comment=
usershare_acl=Everyone:F,
guest_ok=n
--------------------------------------
Result of 
sudo net usershare info

nothing


Result of 
sudo net usershare info
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[strizna]"
Processing section "[ucebna]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = SUM
    server string = %h server (Samba, Ubuntu)
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

[strizna]
    path = /media/server/strizna
    valid users = bazinga, samba, scholzova, student
    read only = No

[ucebna]
    path = /media/server/ucebna
    read only = No
    guest ok = Yes
bazinga@server:~$

---

### Post by Morbius1 on 2010-09-29
I don't understand your output. You have the output of 3 different testparm's - Do you have 3 different machines? It's hard to follow this.

Try to limit this to just one machine and provide the output of the following commands:
```
net usershare info
```
```
sudo net usershare info
```
```
testparm -s
```

---

### Post by Maila87 on 2010-09-29
Sorry, have only one machine. This is what I got( sudo net usershare info gave me no result, just asked for amin password):
```
net usershare info

[strizna]
path=/media/server/strizna
comment=
usershare_acl=Everyone:F,
guest_ok=n

[ucebna]
path=/media/server/ucebna
comment=
usershare_acl=Everyone:F,
guest_ok=n
``````
sudo net usershare info
``````
testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[strizna]"
Processing section "[ucebna]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = SUM
    server string = %h server (Samba, Ubuntu)
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

[strizna]
    path = /media/server/strizna
    valid users = bazinga, samba, scholzova, student
    read only = No

[ucebna]
    path = /media/server/ucebna
    read only = No
    guest ok = Yes



```

Hope, that this is right, I spend few evenings searching resulsts, but as I"m new in world of Linux, still without results by myself.

---

### Post by Morbius1 on 2010-09-29
First, there are 2 completely different methods to use samba to create shares. You're using both at the same time on the same targets and with different authorizations.
For example:
This is a Nautilus-share that will not allow guest access:
> [ucebna]
path=/media/server/ucebna
comment=
usershare_acl=Everyone:F,
guest_ok=nThis is a Classic-share that does allow guest access on the same folder:
> [ucebna]
    path = /media/server/ucebna
    read only = No
    guest ok = YesGo back into nautilus and "unshare" the the two nautilus-shares or use the terminal:
```
net usershare delete strizna
net usershare delete ucebna
```That might fix it. If it doesn't then it might be a permissions problem on the targets themselves. Post the output of the following command:
```
ls -al /media/server
```

---

### Post by Maila87 on 2010-10-01
I unmounted nautilus shares, but still same.
```
ls -al /media/server
total 44
drwxrwx---  8 bazinga bazinga     4096 2010-09-16 11:22 .
drwxr-xr-x  3 root    root        4096 2010-09-26 17:38 ..
drwxr-xr-- 14 bazinga bazinga     4096 2010-09-26 16:54 Install
drwxrwx---  2 bazinga sambashare  4096 2010-09-16 11:21 Kancelar
drwx------  2 root    root       16384 2010-08-21 14:38 lost+found
drwxrwxrwx  5 bazinga sambashare  4096 2010-10-01 12:08 strizna
drwx------  4 bazinga bazinga     4096 2010-09-16 10:31 .Trash-1000
drwxrwxrwx  4 bazinga sambashare  4096 2010-09-24 13:40 ucebna


```

---

### Post by Morbius1 on 2010-10-01
From the looks of it strizna and ucebna have the right permissions but /media/server does not:
> ls -al /media/server
drwxrwx---  8 bazinga bazinga     4096 2010-09-16 11:22 . Any system or remote user that tries to get to strinza will have to open up /media/server first and they cannot because the only person that can enter is bazinga.

One way to fix this is to alter the permission to allow other to open the parent of your shares:
```
sudo chmod 0777 /media/server
```OR
```
sudo chmod 0775 /media/server
```OR
```
sudo chmod 0771 /media/server
```

---

### Post by Maila87 on 2010-10-07
it worked at glance, Thank you very much!!

---

