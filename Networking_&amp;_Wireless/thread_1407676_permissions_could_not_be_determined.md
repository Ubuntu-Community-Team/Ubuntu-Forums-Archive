---
title: "permissions could not be determined"
date: 2010-02-15
forum: Networking &amp; Wireless
---

### Post by Horsepower on 2010-02-15
I have a server running 9.10 desktop, and previously in version 8, my windows computer could see the 2 additional drives in the server. I installed Samba and shared (what I thought) was everything and I see the files on the main drive, but cannot view the 2 additional drives. I go to the server to try to set permisions, but it says "permissions could not be determined" The windows computer is running 7, but a Vista computer on the same network (which used to see those drives) cannot access them either. Thanks.

---

### Post by johnson.d on 2010-02-17
Can you specify how you configured the samba share, by using Nautilus or by manually editing /etc/samba/smb.conf? And also post your smb.conf file if you are using it to configure.

Can you also specify the samba version you are using?

You can also try upgrading samba using the following command:

$ apt-get install samba

---

### Post by Horsepower on 2010-02-17
I used shares-admin from a terminal
Samba 2:3.4.0-3ubuntu5.4

[global]
workgroup = HOME
security = share

usershare path = /var/lib/samba/usershares
usershare max shares = 100
usershare allow guests = yes
usershare owner only = yes
wins support = no

I obviously only know enough to be dangerous, so please bear with me. Thank you.

---

### Post by superprash2003 on 2010-02-17
do post the full content of the smb.conf file

---

### Post by Horsepower on 2010-02-17
There are 3 files called "smb.conf" that is the full contects of the one that is NOT called "sample" Am I looking in the wrong place?
 
*note on the Windows 7 and the Vista computers, the Ubuntu share says it belongs to "homegroup" but the other belong to "workgroup" I cannot access anything from Windows 7, but can access the filesystem but not the additionals drives from the Vista computer.
Thank you

---

### Post by Morbius1 on 2010-02-17
There is something definitely wrong if that's the extent of your smb.conf file.

Try this:
Open **Terminal**
Type **testparm -s /etc/samba/smb.conf**

This should output a concise smb.conf.

> I installed Samba and shared (what I thought) was everything and I see the files on the main drive, but cannot view the 2 additional drives With the smb.conf you last posted you shouldn't have been able to see anything.

---

### Post by Horsepower on 2010-02-17
tonyw@tonyw-desktop:~$ testparm -s /etc/samba/smb.conf
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[tonyw]"
Processing section "[Drive_1]"
Processing section "[Drive_2]"
Processing section "[File System]"
Processing section "[Desktop]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = HOMEGROUP
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

[tonyw]
    path = /home/tonyw
    guest ok = Yes

[Drive_1]
    path = /media/Drive_1
    guest ok = Yes

[Drive_2]
    path = /media/Drive_2
    guest ok = Yes

[File System]
    path = /
    guest ok = Yes

[Desktop]
    path = /home/tonyw/Desktop
    guest ok = Yes
tonyw@tonyw-desktop:~$

---

### Post by Horsepower on 2010-02-17
Well I was able to change the group to workgroup, but have the same dilemma, but now the conf files has no line saying workgroup = "whatever"

---

### Post by Morbius1 on 2010-02-17
I take it that the following are the two drives that the client cannot see:
> [Drive_1]
    path = /media/Drive_1
    guest ok = Yes

[Drive_2]
    path = /media/Drive_2
    guest ok = Yes


Please post the output of the following commands:

Open **Terminal **
Type **ls -dl /media/Drive_1**
Type **ls -dl /media/Drive_2**

---

### Post by Horsepower on 2010-02-17
drwx------ 2 tonyw tonyw 16384 1969-12-31 16:00 /media/Drive_1

drwx------ 2 tonyw tonyw 16384 1969-12-31 16:00 /media/Drive_2

---

### Post by Morbius1 on 2010-02-17
Here's the problem. You want to give your remote users access to the shares and you've instructed samba to allow guest access - which it does. But the underlying linux permissions is only allowing you to read and write.

There's two ways to fix this:
(1) Mount the drives in fstab with the correct permissions if it's a fat32 or ntfs partition. Or a chmod if it's a ext3/4 partition.
(2) Or use samba itself to fix this problem:

Open **Terminal**
Type **gksu gedit /etc/samba/smb.conf**

Then change this:
> [Drive_1]
    path = /media/Drive_1
    guest ok = Yes

[Drive_2]
    path = /media/Drive_2
    guest ok = Yes
To this:
> [Drive_1]
     path = /media/Drive_1
     guest ok = Yes
[COLOR=Blue]force user = tonyw[/COLOR]
 
 [Drive_2]
     path = /media/Drive_2
     guest ok = Yes
[COLOR=Blue]force user = tonyw[/COLOR] This will create a mask that will make linux think that the remote user is you ( as far as that share is concerned ) since you are the only one who has access to it.

Save the smb.conf file, exit gedit, and back in the terminal issue a : **sudo service samba restart**

---

### Post by Horsepower on 2010-02-17
THANKS! That took care of the Vista box. Now I need to figure out the problem which I now know is with Windows 7.

---

