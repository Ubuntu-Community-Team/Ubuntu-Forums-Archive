---
title: "Folders shared in Home directory accessible in Win7, others are not"
date: 2010-06-16
forum: Networking &amp; Wireless
---

### Post by DethFiesta on 2010-06-16
Hello Everyone,

I am having some success and some failures when trying to share folders within a heterogeneous home network.  

Using the Samba GUI I have shared a few folders from my Home folder and these are viewable and accessible in my windows (7, XP, and Vista) machines.  However, folders that I share outside of my home folder (specifically, these are folders on other HDDs mounted in /media) are visible by the Windows machines but when I attempt to access them I am told that they are unavailable. 

I can connect and transfer files to the Music folder in /home/will/Music and Documents folder in /home/will/Documents, so there is not a connectivity issue between the Ubuntu machine and my other computers.

Here is the output from testparm

will@NAS:~$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[homes]"
Processing section "[printers]"
Processing section "[print$]"
Processing section "[TV]"
Processing section "[Music]"
Processing section "[Documents]"
Processing section "[Movies]"
Processing section "[Music Movies]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
    workgroup = HOME
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    guest account = viewer
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
    guest ok = Yes

[homes]
    comment = Home Directories
    read only = No
    create mask = 0775
    directory mask = 0775

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

[TV]
    comment = TV Shows
    path = /media/NAS2/TV
    read only = No

[Music]
    comment = Music
    path = /home/will/Music
    read only = No

[Documents]
    comment = Documents
    path = /home/will/Documents
    read only = No

[Movies]
    comment = Movies
    path = /media/NAS1/Movies
    read only = No

[Music Movies]
    comment = Music DVDs
    path = /media/NAS1/Music Movies
    read only = No
----
Reading on a different forum posting, someone had asked for the output of:
ls -dl /Path-To-Share

will@NAS:~$ ls /media
NAS1  NAS2

will@NAS:~$ ls /media/NAS1
lost+found  Movies  Music Movies

will@NAS:~$ ls /media/NAS1/Movies
this outputs a long list of folders
----

Any ideas why my folders in /home are accessible in Windows via SMB while those located in /media are not?

I am happy to run any command or provide any info.  Many thanks in advance!

---

